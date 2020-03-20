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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="04454-103">Odeslání úlohy .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="04454-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="04454-104">Existují dva způsoby nasazení úlohy .NET pro `spark-submit` Apache Spark do HDInsightu: a Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="04454-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="04454-105">Nasazení pomocí spark-submit</span><span class="sxs-lookup"><span data-stu-id="04454-105">Deploy using spark-submit</span></span>

<span data-ttu-id="04454-106">Pomocí příkazu [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete odeslat .NET pro úlohy Apache Spark do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="04454-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="04454-107">Přejděte do clusteru HDInsight Spark na webu Azure Portal a pak vyberte **Přihlášení SSH + Cluster**.</span><span class="sxs-lookup"><span data-stu-id="04454-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="04454-108">Zkopírujte přihlašovací údaje ssh a vložte přihlášení do terminálu.</span><span class="sxs-lookup"><span data-stu-id="04454-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="04454-109">Přihlaste se ke clusteru pomocí hesla, které nastavíte při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="04454-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="04454-110">Měli byste vidět zprávy, které vás vítají na Ubuntu a Spark.</span><span class="sxs-lookup"><span data-stu-id="04454-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="04454-111">Pomocí příkazu **spark-submit** můžete aplikaci spouštět v clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="04454-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="04454-112">Nezapomeňte nahradit **mycontainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy kontejneru objektů blob a účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="04454-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="04454-113">Nezapomeňte také nahradit `microsoft-spark-2.3.x-0.6.0.jar` příslušným souborem jar, který používáte pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="04454-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="04454-114">`2.3.x`představuje verzi Apache Spark `0.6.0` a představuje verzi [.NET pro pracovníka Apache Spark](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="04454-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="04454-115">Nasazení pomocí Apache Livy</span><span class="sxs-lookup"><span data-stu-id="04454-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="04454-116">[Pomocí apache livy](https://livy.incubator.apache.org/), rozhraní APACHE Spark REST API, můžete odeslat rozhraní .NET pro úlohy Apache Spark do clusteru Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="04454-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="04454-117">Další informace naleznete v [tématu Vzdálené úlohy s Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="04454-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="04454-118">Následující příkaz na Linuxu `curl`můžete spustit pomocí :</span><span class="sxs-lookup"><span data-stu-id="04454-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="04454-119">Další kroky</span><span class="sxs-lookup"><span data-stu-id="04454-119">Next steps</span></span>

* [<span data-ttu-id="04454-120">Začínáme s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="04454-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="04454-121">Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="04454-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="04454-122">Dokumentace ke službě HDInsight</span><span class="sxs-lookup"><span data-stu-id="04454-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
