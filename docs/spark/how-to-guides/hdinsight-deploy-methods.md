---
title: Odeslání úlohy .NET for Apache Spark do Azure HDInsight
description: Naučte se, jak odeslat úlohu .NET for Apache Spark do Azure HDInsight pomocí Spark-Submit a Apache Livy.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 50611b1f62934a446e5b80a8c53698efe23cd1fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617688"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Odeslání úlohy .NET for Apache Spark do Azure HDInsight

Existují dva způsoby, jak nasadit aplikaci .NET pro Apache Spark úlohy do HDInsight: `spark-submit` a Apache Livy.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a>Nasazení pomocí Spark-Submit

K odeslání .NET pro úlohy Apache Spark do Azure HDInsight můžete použít příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) .

1. Přejděte do clusteru HDInsight Spark v Azure Portal a pak vyberte **ssh + přihlášení ke clusteru**.

2. Zkopírujte přihlašovací informace SSH a vložte přihlašovací jméno do terminálu. Přihlaste se ke svému clusteru pomocí hesla, které jste nastavili při vytváření clusteru. Měli byste vidět zprávy, které vás přivítá vás a Ubuntu a Spark.

3. Pomocí příkazu **Spark-Submit** spusťte aplikaci v clusteru HDInsight. Nezapomeňte nahradit **myContainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy vašeho kontejneru objektů BLOB a účtu úložiště. Nezapomeňte také nahradit `microsoft-spark-2.3.x-0.6.0.jar` vhodným souborem jar, který používáte pro nasazení. `2.3.x`představuje verzi Apache Spark a `0.6.0` představuje verzi [rozhraní .net pro Apache Spark Worker](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Nasazení pomocí Apache Livy

K odeslání rozhraní .NET pro Apache Spark úlohy do clusteru Azure HDInsight Spark můžete použít [Apache Livy](https://livy.incubator.apache.org/)Apache Spark REST API. Další informace najdete v tématu [vzdálené úlohy s Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Následující příkaz můžete na platformě Linux spustit pomocí `curl` :

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

## <a name="next-steps"></a>Další kroky

* [Začínáme s .NET pro Apache Spark](../tutorials/get-started.md)
* [Nasazení aplikace .NET pro Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Dokumentace ke službě HDInsight](https://docs.microsoft.com/azure/hdinsight/)
