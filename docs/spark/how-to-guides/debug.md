---
title: Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows
description: Naučte se ladit rozhraní .NET pro Apache Spark aplikace ve Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 098c7519fe99ef04773c5e4b81685ca0f06f1272
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281531"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="1c632-103">Ladění aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="1c632-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="1c632-104">Tento postup poskytuje příkazy, které je třeba spustit, chcete-li ladit rozhraní .NET pro Apache Spark Scala a kód aplikace v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1c632-104">This how-to provides the commands you need to run to debug your .NET for Apache Spark application and Scala code on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="1c632-105">Ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="1c632-105">Debug your application</span></span>

<span data-ttu-id="1c632-106">Otevřete nové okno příkazového řádku, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1c632-106">Open a new command prompt window, run the following:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="1c632-107">Po spuštění příkazu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1c632-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="1c632-108">V tomto režimu ladění `DotnetRunner` nespustí aplikaci .NET, ale počká na připojení.</span><span class="sxs-lookup"><span data-stu-id="1c632-108">In this debug mode, `DotnetRunner` does not launch the .NET application, but it waits for it to connect.</span></span> <span data-ttu-id="1c632-109">Nechte okno příkazového řádku otevřené.</span><span class="sxs-lookup"><span data-stu-id="1c632-109">Leave this command prompt window open.</span></span>

<span data-ttu-id="1c632-110">Nyní můžete spustit aplikaci .NET pomocí libovolného ladicího programu pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c632-110">Now you can run your .NET application with any debugger to debug your application.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="1c632-111">Ladění kódu Scala</span><span class="sxs-lookup"><span data-stu-id="1c632-111">Debug Scala code</span></span>

<span data-ttu-id="1c632-112">Pokud potřebujete ladit Scala na straně kódu, například `DotnetRunner` nebo `DotnetBackendHandler`, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1c632-112">If you need to debug the Scala side code, such as `DotnetRunner` or `DotnetBackendHandler`, run the following command:</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="1c632-113">Po spuštění příkazu připojte ladicí program k běžícímu procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="1c632-113">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1c632-114">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1c632-114">Next steps</span></span>

* [<span data-ttu-id="1c632-115">Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="1c632-115">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="1c632-116">Nasazení aplikace .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="1c632-116">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="1c632-117">Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů</span><span class="sxs-lookup"><span data-stu-id="1c632-117">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="1c632-118">Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="1c632-118">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
