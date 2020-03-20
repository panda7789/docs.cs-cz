---
title: Odeslání úlohy .NET pro Apache Spark do Azure HDInsight
description: Přečtěte si, jak odeslat úlohu .NET pro Apache Spark do Azure HDInsight pomocí spark-submit a Apache Livy.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 83359f7f613b500a4ce121ce1612cda0ad1191ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185789"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Odeslání úlohy .NET pro Apache Spark do Azure HDInsight

Existují dva způsoby nasazení úlohy .NET pro `spark-submit` Apache Spark do HDInsightu: a Apache Livy.

## <a name="deploy-using-spark-submit"></a>Nasazení pomocí spark-submit

Pomocí příkazu [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete odeslat .NET pro úlohy Apache Spark do Azure HDInsight.

1. Přejděte do clusteru HDInsight Spark na webu Azure Portal a pak vyberte **Přihlášení SSH + Cluster**.

2. Zkopírujte přihlašovací údaje ssh a vložte přihlášení do terminálu. Přihlaste se ke clusteru pomocí hesla, které nastavíte při vytváření clusteru. Měli byste vidět zprávy, které vás vítají na Ubuntu a Spark.

3. Pomocí příkazu **spark-submit** můžete aplikaci spouštět v clusteru HDInsight. Nezapomeňte nahradit **mycontainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy kontejneru objektů blob a účtu úložiště. Nezapomeňte také nahradit `microsoft-spark-2.3.x-0.6.0.jar` příslušným souborem jar, který používáte pro nasazení. `2.3.x`představuje verzi Apache Spark `0.6.0` a představuje verzi [.NET pro pracovníka Apache Spark](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Nasazení pomocí Apache Livy

[Pomocí apache livy](https://livy.incubator.apache.org/), rozhraní APACHE Spark REST API, můžete odeslat rozhraní .NET pro úlohy Apache Spark do clusteru Azure HDInsight Spark. Další informace naleznete v [tématu Vzdálené úlohy s Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Následující příkaz na Linuxu `curl`můžete spustit pomocí :

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

* [Začínáme s rozhraním .NET pro Apache Spark](../tutorials/get-started.md)
* [Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Dokumentace ke službě HDInsight](https://docs.microsoft.com/azure/hdinsight/)
