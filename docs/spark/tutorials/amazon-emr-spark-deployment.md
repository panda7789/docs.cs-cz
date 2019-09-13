---
title: Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8cde4f173fb1de5ebf271f4f080d21d587d3229e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928540"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark

V tomto kurzu se naučíte nasadit rozhraní .NET pro Apache Spark aplikaci do Amazon EMR Spark.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Příprava Microsoft. spark. Worker
> * Publikování aplikace Spark .NET
> * Nasazení aplikace do Amazon EMR Spark
> * Spuštění aplikace

## <a name="prerequisites"></a>Požadavky

Než začnete, udělejte toto:

* Stáhněte si rozhraní příkazového [řádku AWS](https://aws.amazon.com/cli/).
* Stáhněte si [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do svého místního počítače. Toto je pomocný skript, který později použijete ke kopírování rozhraní .NET pro Apache Spark závislé soubory do pracovních uzlů clusteru Spark.

## <a name="prepare-worker-dependencies"></a>Příprava závislostí pracovního procesu

**Microsoft. spark. Worker** je komponenta back-end, která je umístěná na jednotlivých pracovních uzlech clusteru Spark. Pokud chcete spustit systém C# souborů UDF (uživatelsky definovaná funkce), musí Spark pochopit, jak spustit modul CLR .NET pro spouštění systému souborů UDF. **Microsoft. spark. Worker** poskytuje kolekci tříd pro Spark, které tuto funkci povolují.

1. Vyberte verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, která se má nasadit na váš cluster.

   Pokud například chcete `.NET for Apache Spark v0.1.0` použít `netcoreapp2.1`, Stáhněte si soubor [Microsoft. spark. work. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Nahrajte `Microsoft.Spark.Worker.<release>.tar.gz` a [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do distribuovaného systému souborů (např. S3), ke kterému má váš cluster přístup.

## <a name="prepare-your-net-for-apache-spark-app"></a>Příprava rozhraní .NET pro aplikaci Apache Spark

1. Při sestavování aplikace postupujte podle kurzu [Začínáme](get-started.md) .

2. Publikujte aplikaci Spark .NET jako samostatnou.

   Spusťte následující příkaz na platformě Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Vytvořte `<your app>.zip` pro publikované soubory.

   Spusťte následující příkaz na platformě Linux pomocí `zip`příkazu.

   ```bash
   zip -r <your app>.zip .
   ```

4. Nahrajte následující položky do distribuovaného systému souborů (například S3), ke kterému má váš cluster přístup:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tento JAR je součástí balíčku NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) a je umístěný ve výstupním adresáři sestavení vaší aplikace.
   * `<your app>.zip`
   * Soubory (jako jsou soubory závislosti nebo společná data dostupná pro každého pracovního procesu) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo knihovny, na kterých je vaše aplikace závislá), aby se umístily do pracovního adresáře každého prováděcího modulu.

## <a name="deploy-to-amazon-emr-spark"></a>Nasazení na Amazon EMR Spark

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) je spravovaná platforma clusteru, která usnadňuje spouštění rozsáhlých datových ARCHITEKTUR na AWS.

> [!NOTE] 
> Amazon EMR Spark je založený na systému Linux. Proto pokud vás zajímá nasazení aplikace do Amazon EMR Spark, ujistěte se, že je vaše aplikace .NET Standard kompatibilní a že ke kompilaci vaší aplikace použijete [kompilátor .NET Core](https://dotnet.microsoft.com/download) .

### <a name="deploy-microsoftsparkworker"></a>Nasazení Microsoft. spark. Worker

Tento krok se vyžaduje jenom při vytváření clusteru.

Spustí `install-worker.sh` se během vytváření clusteru pomocí [spouštěcích akcí](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Spusťte následující příkaz na platformě Linux pomocí rozhraní příkazového řádku AWS.

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

Existují dva způsoby, jak aplikaci spustit v Amazon EMR Spark: Spark-Submit a Amazon EMR kroky.

### <a name="use-spark-submit"></a>Použití Spark-Submit

Pomocí příkazu [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete odesílat .NET pro úlohy Apache Spark do Amazon EMR Spark.

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

### <a name="use-amazon-emr-steps"></a>Použití kroků Amazon EMR

[Kroky Amazon EMR](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) je možné použít k odesílání úloh do rozhraní Spark instalovaného v clusteru EMR.

Spusťte následující příkaz na platformě Linux pomocí rozhraní příkazového řádku AWS.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Další postup

V tomto kurzu jste nasadili rozhraní .NET pro Apache Spark aplikaci do Amazon EMR Spark. V případě rozhraní .NET for Apache Spark ukázkové projekty pokračujte na GitHub.

> [!div class="nextstepaction"]
> [Ukázky pro .NET for Apache Spark](https://github.com/dotnet/spark/tree/master/examples)
