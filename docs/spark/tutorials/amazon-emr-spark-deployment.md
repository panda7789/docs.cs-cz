---
title: Nasazení rozhraní .NET pro aplikaci Apache Spark do amazonského EMR Spark
description: Zjistěte, jak nasadit .NET pro aplikaci Apache Spark do Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73454932"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Nasazení rozhraní .NET pro aplikaci Apache Spark do amazonského EMR Spark

Tento kurz učí, jak nasadit .NET pro aplikaci Apache Spark do Amazon EMR Spark.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Příprava microsoft.spark.worker
> * Publikování aplikace Spark .NET
> * Nasazení aplikace do Amazon EMR Spark
> * Spuštění aplikace

## <a name="prerequisites"></a>Požadavky

Než začnete, postupujte takto:

* Stáhněte si [rozhraní se křižovatek AWS](https://aws.amazon.com/cli/).
* Stáhněte [si install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do místního počítače. Toto je pomocný skript, který později použijete ke kopírování souborů .NET pro závislé soubory Apache Spark do pracovních uzlů clusteru Spark.

## <a name="prepare-worker-dependencies"></a>Příprava závislostí pracovníků

**Microsoft.Spark.Worker** je back-endová součást, která žije na jednotlivých pracovních uzlech vašeho clusteru Spark. Pokud chcete spustit C# UDF (uživatelem definovaná funkce), Spark musí pochopit, jak spustit .NET CLR ke spuštění UDF. **Microsoft.Spark.Worker** poskytuje kolekci tříd pro Spark, které umožňují tuto funkci.

1. Vyberte verzi [netcoreapp microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux, která se má nasadit ve vašem clusteru.

   Chcete-li například `.NET for Apache Spark v0.1.0` `netcoreapp2.1`použít program , stáhněte si soubor [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Nahrávání `Microsoft.Spark.Worker.<release>.tar.gz` a [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do distribuovaného systému souborů (např. s3), ke kterému má cluster přístup.

## <a name="prepare-your-net-for-apache-spark-app"></a>Příprava aplikace .NET pro Apache Spark

1. Podle kurzu [Začínáme](get-started.md) vytvořte aplikaci.

2. Publikujte aplikaci Spark .NET jako samostatnou.

   Spusťte následující příkaz na Linuxu.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Vytvořit `<your app>.zip` pro publikované soubory.

   Spusťte následující příkaz `zip`na Linuxu pomocí .

   ```bash
   zip -r <your app>.zip .
   ```

4. Nahrajte do distribuovaného systému souborů (např. s3) následující položky, ke kterému má cluster přístup:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tato nádoba je součástí balíčku [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet a je umístěna společně ve výstupním adresáři sestavení vaší aplikace.
   * `<your app>.zip`
   * Soubory (jako jsou soubory závislostí nebo společná data přístupná každému pracovníkovi) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo knihovny, na kterých závisí vaše aplikace), které mají být umístěny do pracovního adresáře každého vykonavatele.

## <a name="deploy-to-amazon-emr-spark"></a>Nasazení na Amazon EMR Spark

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) je spravovaná clusterová platforma, která zjednodušuje provoz rámců pro velké objemy dat na AWS.

> [!NOTE]
> Amazon EMR Spark je založen na Linuxu. Pokud tedy máte zájem o nasazení aplikace do Amazon EMR Spark, ujistěte se, že vaše aplikace je kompatibilní se standardem .NET standard a že k kompilaci aplikace používáte [kompilátor .NET Core.](https://dotnet.microsoft.com/download)

### <a name="deploy-microsoftsparkworker"></a>Nasazení microsoft.spark.worker

Tento krok je vyžadován pouze při vytváření clusteru.

Spustit `install-worker.sh` během vytváření clusteru pomocí [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Spusťte následující příkaz na Linuxu pomocí příkazového příkazu AWS.

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>Spuštění aplikace

Existují dva způsoby, jak spustit aplikaci v Amazon EMR Spark: spark-submit a Amazon EMR Steps.

### <a name="use-spark-submit"></a>Použití spark-submit

Příkaz [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete použít k odeslání .NET pro úlohy Apache Spark do Amazon EMR Spark.

1. `ssh`do jednoho z uzlů v clusteru.

2. Spusťte `spark-submit`.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Použití Amazon EMR kroky

[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) lze použít k odeslání úloh do rámce Spark nainstalovaného v clusteru EMR.

Spusťte následující příkaz na Linuxu pomocí příkazového příkazu AWS.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste nasadili .NET pro aplikaci Apache Spark do Amazon EMR Spark. Pro .NET pro projekty příklad Apache Spark pokračujte na GitHub.

> [!div class="nextstepaction"]
> [.NET pro ukázky Apache Spark](https://github.com/dotnet/spark/tree/master/examples)
