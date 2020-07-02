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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="a802a-103">Odeslání úlohy .NET for Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="a802a-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="a802a-104">Existují dva způsoby, jak nasadit aplikaci .NET pro Apache Spark úlohy do HDInsight: `spark-submit` a Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="a802a-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="a802a-105">Nasazení pomocí Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="a802a-105">Deploy using spark-submit</span></span>

<span data-ttu-id="a802a-106">K odeslání .NET pro úlohy Apache Spark do Azure HDInsight můžete použít příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) .</span><span class="sxs-lookup"><span data-stu-id="a802a-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="a802a-107">Přejděte do clusteru HDInsight Spark v Azure Portal a pak vyberte **ssh + přihlášení ke clusteru**.</span><span class="sxs-lookup"><span data-stu-id="a802a-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="a802a-108">Zkopírujte přihlašovací informace SSH a vložte přihlašovací jméno do terminálu.</span><span class="sxs-lookup"><span data-stu-id="a802a-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="a802a-109">Přihlaste se ke svému clusteru pomocí hesla, které jste nastavili při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="a802a-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="a802a-110">Měli byste vidět zprávy, které vás přivítá vás a Ubuntu a Spark.</span><span class="sxs-lookup"><span data-stu-id="a802a-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="a802a-111">Pomocí příkazu **Spark-Submit** spusťte aplikaci v clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="a802a-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="a802a-112">Nezapomeňte nahradit **myContainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy vašeho kontejneru objektů BLOB a účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="a802a-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="a802a-113">Nezapomeňte také nahradit `microsoft-spark-2.3.x-0.6.0.jar` vhodným souborem jar, který používáte pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="a802a-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="a802a-114">`2.3.x`představuje verzi Apache Spark a `0.6.0` představuje verzi [rozhraní .net pro Apache Spark Worker](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="a802a-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="a802a-115">Nasazení pomocí Apache Livy</span><span class="sxs-lookup"><span data-stu-id="a802a-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="a802a-116">K odeslání rozhraní .NET pro Apache Spark úlohy do clusteru Azure HDInsight Spark můžete použít [Apache Livy](https://livy.incubator.apache.org/)Apache Spark REST API.</span><span class="sxs-lookup"><span data-stu-id="a802a-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="a802a-117">Další informace najdete v tématu [vzdálené úlohy s Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="a802a-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="a802a-118">Následující příkaz můžete na platformě Linux spustit pomocí `curl` :</span><span class="sxs-lookup"><span data-stu-id="a802a-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="a802a-119">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a802a-119">Next steps</span></span>

* [<span data-ttu-id="a802a-120">Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a802a-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="a802a-121">Nasazení aplikace .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="a802a-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="a802a-122">Dokumentace ke službě HDInsight</span><span class="sxs-lookup"><span data-stu-id="a802a-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
