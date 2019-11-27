---
title: Odeslání úlohy .NET for Apache Spark do Azure HDInsight
description: Naučte se, jak odeslat úlohu .NET for Apache Spark do Azure HDInsight pomocí Spark-Submit a Apache Livy.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: cdd5e15ffde78ccb8b3156ee047b8ca98f7320b8
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74553009"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="864e3-103">Odeslání úlohy .NET for Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="864e3-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="864e3-104">Existují dva způsoby, jak nasadit aplikaci .NET pro Apache Spark úlohy do HDInsight: `spark-submit` a Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="864e3-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="864e3-105">Nasazení pomocí Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="864e3-105">Deploy using spark-submit</span></span>

<span data-ttu-id="864e3-106">K odeslání .NET pro úlohy Apache Spark do Azure HDInsight můžete použít příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) .</span><span class="sxs-lookup"><span data-stu-id="864e3-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="864e3-107">Přejděte do clusteru HDInsight Spark v Azure Portal a pak vyberte **ssh + přihlášení ke clusteru**.</span><span class="sxs-lookup"><span data-stu-id="864e3-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="864e3-108">Zkopírujte přihlašovací informace SSH a vložte přihlašovací jméno do terminálu.</span><span class="sxs-lookup"><span data-stu-id="864e3-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="864e3-109">Přihlaste se ke svému clusteru pomocí hesla, které jste nastavili při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="864e3-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="864e3-110">Měli byste vidět zprávy, které vás přivítá vás a Ubuntu a Spark.</span><span class="sxs-lookup"><span data-stu-id="864e3-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="864e3-111">Pomocí příkazu **Spark-Submit** spusťte aplikaci v clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="864e3-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="864e3-112">Nezapomeňte nahradit **myContainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy vašeho kontejneru objektů BLOB a účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="864e3-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="864e3-113">Nezapomeňte také nahradit `microsoft-spark-2.3.x-0.6.0.jar` příslušným souborem jar, který používáte pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="864e3-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="864e3-114">`2.3.x` představuje verzi Apache Spark a `0.6.0` představuje verzi [rozhraní .NET pro Apache Spark pracovního procesu](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="864e3-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="864e3-115">Nasazení pomocí Apache Livy</span><span class="sxs-lookup"><span data-stu-id="864e3-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="864e3-116">K odeslání rozhraní .NET pro Apache Spark úlohy do clusteru Azure HDInsight Spark můžete použít [Apache Livy](https://livy.incubator.apache.org/)Apache Spark REST API.</span><span class="sxs-lookup"><span data-stu-id="864e3-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="864e3-117">Další informace najdete v tématu [vzdálené úlohy s Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="864e3-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="864e3-118">Následující příkaz můžete na platformě Linux spustit pomocí `curl`:</span><span class="sxs-lookup"><span data-stu-id="864e3-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="864e3-119">Další kroky</span><span class="sxs-lookup"><span data-stu-id="864e3-119">Next steps</span></span>

* [<span data-ttu-id="864e3-120">Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="864e3-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="864e3-121">Nasazení aplikace .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="864e3-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="864e3-122">Dokumentace k HDInsight</span><span class="sxs-lookup"><span data-stu-id="864e3-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
