---
title: Nasazení aplikace .NET pro Apache Spark do Azure HDInsight
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 81d1af1fd4e3329c4a289eea388edf8af57d7c4e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243948"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Nasazení aplikace .NET pro Apache Spark do Azure HDInsight

V tomto kurzu se naučíte nasadit rozhraní .NET pro Apache Spark aplikaci do Azure HDInsight.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Příprava Microsoft. spark. Worker
> * Publikování aplikace Spark .NET
> * Nasazení aplikace do Azure HDInsight
> * Spuštění aplikace

## <a name="prerequisites"></a>Požadavky

Než začnete, udělejte toto:

* Stáhněte si [Průzkumník služby Azure Storage](https://azure.microsoft.com/features/storage-explorer/).
* Stáhněte si [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do svého místního počítače. Toto je pomocný skript, který později použijete ke kopírování rozhraní .NET pro Apache Spark závislé soubory do pracovních uzlů clusteru Spark.

## <a name="prepare-worker-dependencies"></a>Příprava závislostí pracovního procesu

**Microsoft. spark. Worker** je komponenta back-end, která je umístěná na jednotlivých pracovních uzlech clusteru Spark. Pokud chcete spustit systém C# souborů UDF (uživatelsky definovaná funkce), musí Spark pochopit, jak spustit modul CLR .NET pro spouštění systému souborů UDF. **Microsoft. spark. Worker** poskytuje kolekci tříd pro Spark, které tuto funkci povolují.

1. Vyberte verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, která se má nasadit na váš cluster.

   Pokud například chcete `.NET for Apache Spark v0.1.0` použít `netcoreapp2.1`, Stáhněte si soubor [Microsoft. spark. work. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Nahrajte `Microsoft.Spark.Worker.<release>.tar.gz` a [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do distribuovaného systému souborů (např. HDFS, WASB, adls), ke kterému má váš cluster přístup.

## <a name="prepare-your-net-for-apache-spark-app"></a>Příprava rozhraní .NET pro aplikaci Apache Spark

1. Při sestavování aplikace postupujte podle kurzu [Začínáme](get-started.md) .

2. Publikujte aplikaci Spark .NET jako samostatnou.

   V systému Linux můžete spustit následující příkaz.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Vytvořte `<your app>.zip` pro publikované soubory.

   Následující příkaz můžete spustit na platformě Linux pomocí nástroje `zip`.

   ```bash
   zip -r <your app>.zip .
   ```

4. Následujícím způsobem nahrajte distribuovaný systém souborů (např. HDFS, WASB, ADLS), ke kterému má váš cluster přístup:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tento JAR je součástí balíčku NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) a je umístěný ve výstupním adresáři sestavení vaší aplikace.
   * `<your app>.zip`
   * Soubory (jako jsou soubory závislostí nebo společná data dostupná pro každého pracovního procesu) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo `app` knihovny, na kterých závisí), budou umístěny do pracovního adresáře každého prováděcího modulu.

## <a name="deploy-to-azure-hdinsight-spark"></a>Nasadit do Azure HDInsight Spark

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) je implementace Apache Spark v cloudu od Microsoftu, která umožňuje uživatelům spouštět a konfigurovat clustery Spark v Azure. Clustery HDInsight Spark můžete použít ke zpracování dat uložených v [Azure Storage](https://azure.microsoft.com/services/storage/) nebo [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).

> [!NOTE]
> Azure HDInsight Spark je založen na systému Linux. Pokud vás zajímá nasazení aplikace pro Azure HDInsight Spark, ujistěte se, že je vaše aplikace .NET Standard kompatibilní a že ke kompilaci vaší aplikace používáte [kompilátor .NET Core](https://dotnet.microsoft.com/download) .

### <a name="deploy-microsoftsparkworker"></a>Nasazení Microsoft. spark. Worker

Tento krok se vyžaduje jenom jednou pro váš cluster.

Spusťte `install-worker.sh` v clusteru pomocí [akcí skriptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

|Nastavení|Value|
|-------|-----|
|Typ skriptu|Vlastní|
|Name|Nainstalovat Microsoft. spark. Worker|
|Identifikátor URI skriptu bash|Identifikátor URI, na který jste `install-worker.sh`nahráli. Třeba `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`.|
|Typ (typy) uzlů|Zaměstnanec|
|Parametry|Parametry do `install-worker.sh`. Pokud jste například nahráli `install-worker.sh` Azure Data Lake Gen 2, bude to. `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`|

![Obrázek akce skriptu](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>Spuštění aplikace

Svoji úlohu můžete odeslat do Azure HDInsight pomocí `spark-submit` aplikace nebo Apache Livy.

### <a name="use-spark-submit"></a>Použití Spark-Submit

K odeslání .NET pro úlohy Apache Spark do Azure HDInsight můžete použít příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) .
 
1. `ssh`do jednoho z hlavních uzlů v clusteru.

1. Spusťte `spark-submit`:

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Použití Apache Livy

K odeslání rozhraní .NET pro Apache Spark úlohy do clusteru Azure HDInsight Spark můžete použít [Apache Livy](https://livy.incubator.apache.org/)Apache Spark REST API. Další informace najdete v tématu [vzdálené úlohy s Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Následující příkaz můžete na platformě Linux spustit pomocí `curl`:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Další postup

V tomto kurzu jste nasadili aplikaci .NET pro Apache Spark do služby Azure HDInsight. Pokud se chcete dozvědět víc o službě HDInsight, přejděte k dokumentaci k Azure HDInsight.

> [!div class="nextstepaction"]
> [Dokumentace ke službě Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
