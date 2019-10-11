---
title: Začínáme s .NET pro Apache Spark
description: Zjistěte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c4dbce74d0d8c0a682250a8021d983ef2990971f
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250314"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="7666d-103">Kurz: Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7666d-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="7666d-104">V tomto kurzu se naučíte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="7666d-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="7666d-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="7666d-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7666d-106">Příprava prostředí Windows pro rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7666d-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="7666d-107">Stáhnout **Microsoft. spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="7666d-107">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="7666d-108">Sestavení a spuštění jednoduchého rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="7666d-108">Build and run a simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="7666d-109">Příprava prostředí</span><span class="sxs-lookup"><span data-stu-id="7666d-109">Prepare your environment</span></span>

<span data-ttu-id="7666d-110">Než začnete, ujistěte se, že na příkazovém řádku můžete spustit `dotnet`, `java`, `mvn`, `spark-shell`.</span><span class="sxs-lookup"><span data-stu-id="7666d-110">Before you begin, make sure you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line.</span></span> <span data-ttu-id="7666d-111">Pokud je vaše prostředí už připravené, můžete přejít k další části.</span><span class="sxs-lookup"><span data-stu-id="7666d-111">If your environment is already prepared, you can skip to the next section.</span></span> <span data-ttu-id="7666d-112">Pokud nemůžete spustit žádný nebo žádný z těchto příkazů, postupujte podle následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="7666d-112">If you cannot run any or all of the commands, follow the steps below.</span></span>

1. <span data-ttu-id="7666d-113">Stáhněte a nainstalujte [sadu .NET Core 2.1 x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="7666d-113">Download and install the [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="7666d-114">Instalace sady SDK přidá do cesty `dotnet` sada nástrojů.</span><span class="sxs-lookup"><span data-stu-id="7666d-114">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> <span data-ttu-id="7666d-115">K ověření instalace použijte příkaz prostředí PowerShell `dotnet --version`.</span><span class="sxs-lookup"><span data-stu-id="7666d-115">Use the PowerShell command `dotnet --version` to verify the installation.</span></span>

2. <span data-ttu-id="7666d-116">Nainstalujte [Visual studio 2017](https://www.visualstudio.com/downloads/) nebo [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) s nejnovějšími aktualizacemi.</span><span class="sxs-lookup"><span data-stu-id="7666d-116">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/) or [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) with the latest updates.</span></span> <span data-ttu-id="7666d-117">Můžete použít komunita, Professional nebo Enterprise.</span><span class="sxs-lookup"><span data-stu-id="7666d-117">You can use Community, Professional, or Enterprise.</span></span> <span data-ttu-id="7666d-118">Verze Community je zdarma.</span><span class="sxs-lookup"><span data-stu-id="7666d-118">The Community version is free.</span></span>

   <span data-ttu-id="7666d-119">Během instalace vyberte následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="7666d-119">Choose the following workloads during installation:</span></span>
      * <span data-ttu-id="7666d-120">Vývoj pro desktopy .NET</span><span class="sxs-lookup"><span data-stu-id="7666d-120">.NET desktop development</span></span>
          * <span data-ttu-id="7666d-121">Všechny požadované součásti</span><span class="sxs-lookup"><span data-stu-id="7666d-121">All required components</span></span>
          * <span data-ttu-id="7666d-122">Vývojové nástroje .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="7666d-122">.NET Framework 4.6.1 Development Tools</span></span>
      * <span data-ttu-id="7666d-123">Vývoj pro různé platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="7666d-123">.NET Core cross-platform development</span></span>
          * <span data-ttu-id="7666d-124">Všechny požadované součásti</span><span class="sxs-lookup"><span data-stu-id="7666d-124">All required components</span></span>

3. <span data-ttu-id="7666d-125">Nainstalujte [Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="7666d-125">Install [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

    * <span data-ttu-id="7666d-126">Vyberte odpovídající verzi pro váš operační systém.</span><span class="sxs-lookup"><span data-stu-id="7666d-126">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="7666d-127">Vyberte například **JDK-8u201-Windows-x64. exe** pro počítač se systémem Windows x64.</span><span class="sxs-lookup"><span data-stu-id="7666d-127">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span>
    * <span data-ttu-id="7666d-128">K ověření instalace použijte příkaz prostředí PowerShell `java -version`.</span><span class="sxs-lookup"><span data-stu-id="7666d-128">Use the PowerShell command `java -version` to verify the installation.</span></span>

4. <span data-ttu-id="7666d-129">Nainstalujte [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).</span><span class="sxs-lookup"><span data-stu-id="7666d-129">Install [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span></span>
    * <span data-ttu-id="7666d-130">Stáhněte si [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="7666d-130">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
    * <span data-ttu-id="7666d-131">Extrahuje do místního adresáře.</span><span class="sxs-lookup"><span data-stu-id="7666d-131">Extract to a local directory.</span></span> <span data-ttu-id="7666d-132">Například `c:\bin\apache-maven-3.6.0\`.</span><span class="sxs-lookup"><span data-stu-id="7666d-132">For example, `c:\bin\apache-maven-3.6.0\`.</span></span>
    * <span data-ttu-id="7666d-133">Přidejte Apache Maven do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="7666d-133">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="7666d-134">Pokud jste extrahovali do `c:\bin\apache-maven-3.6.0\`, přidali byste do cesty `c:\bin\apache-maven-3.6.0\bin`.</span><span class="sxs-lookup"><span data-stu-id="7666d-134">If you extracted to `c:\bin\apache-maven-3.6.0\`, you would add `c:\bin\apache-maven-3.6.0\bin` to your PATH.</span></span>
    * <span data-ttu-id="7666d-135">K ověření instalace použijte příkaz prostředí PowerShell `mvn -version`.</span><span class="sxs-lookup"><span data-stu-id="7666d-135">Use the PowerShell command `mvn -version` to verify the installation.</span></span>

5. <span data-ttu-id="7666d-136">Nainstalujte [Apache Spark 2.3 +](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="7666d-136">Install [Apache Spark 2.3+](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="7666d-137">Apache Spark 2.4 + se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="7666d-137">Apache Spark 2.4+ isn't supported.</span></span>
    * <span data-ttu-id="7666d-138">Stáhněte si [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) a extrahujte ji do místní složky pomocí nástroje, jako je [7-zip](https://www.7-zip.org/) nebo [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="7666d-138">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder using a tool like [7-zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/).</span></span> <span data-ttu-id="7666d-139">Můžete ho například extrahovat do `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="7666d-139">For example, you might extract it to `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>
    * <span data-ttu-id="7666d-140">Přidejte Apache Spark do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="7666d-140">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="7666d-141">Pokud jste extrahovali do `c:\bin\spark-2.3.2-bin-hadoop2.7\`, přidali byste do cesty `c:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span><span class="sxs-lookup"><span data-stu-id="7666d-141">If you extracted to `c:\bin\spark-2.3.2-bin-hadoop2.7\`, you would add `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` to your PATH.</span></span>
    * <span data-ttu-id="7666d-142">Přidejte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) nazvanou `SPARK_HOME`.</span><span class="sxs-lookup"><span data-stu-id="7666d-142">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) called `SPARK_HOME`.</span></span> <span data-ttu-id="7666d-143">Pokud jste extrahovali do `C:\bin\spark-2.3.2-bin-hadoop2.7\`, pro **hodnotu proměnné**použijte `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="7666d-143">If you extracted to `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use  `C:\bin\spark-2.3.2-bin-hadoop2.7\` for the **Variable value**.</span></span>
    * <span data-ttu-id="7666d-144">Ověřte, že z příkazového řádku můžete spustit `spark-shell`.</span><span class="sxs-lookup"><span data-stu-id="7666d-144">Verify you are able to run `spark-shell` from your command line.</span></span>

6. <span data-ttu-id="7666d-145">Nastavte [WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="7666d-145">Set up [WinUtils](https://github.com/steveloughran/winutils).</span></span>
    * <span data-ttu-id="7666d-146">Stáhněte si binární soubor **winutils. exe** z [úložiště winutils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="7666d-146">Download the **winutils.exe** binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="7666d-147">Vyberte verzi Hadoop, se kterou byla distribuce Sparku zkompilována.</span><span class="sxs-lookup"><span data-stu-id="7666d-147">Select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="7666d-148">Například můžete použít **Hadoop-2.7.1** pro **Spark 2.3.2**.</span><span class="sxs-lookup"><span data-stu-id="7666d-148">For example, you use **hadoop-2.7.1** for **Spark 2.3.2**.</span></span> <span data-ttu-id="7666d-149">Na konci názvu instalační složky Sparku se používá Poznámka k verzi systému Hadoop.</span><span class="sxs-lookup"><span data-stu-id="7666d-149">The Hadoop version is annotated at the end of your Spark install folder name.</span></span>
    * <span data-ttu-id="7666d-150">Uložte binární soubor **winutils. exe** do adresáře podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="7666d-150">Save the **winutils.exe** binary to a directory of your choice.</span></span> <span data-ttu-id="7666d-151">Například `c:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="7666d-151">For example, `c:\hadoop\bin`.</span></span>
    * <span data-ttu-id="7666d-152">Nastavte `HADOOP_HOME` pro reflektování adresáře pomocí **winutils. exe** bez `bin`.</span><span class="sxs-lookup"><span data-stu-id="7666d-152">Set `HADOOP_HOME` to reflect the directory with **winutils.exe** without `bin`.</span></span> <span data-ttu-id="7666d-153">Například `c:\hadoop`.</span><span class="sxs-lookup"><span data-stu-id="7666d-153">For example, `c:\hadoop`.</span></span>
    * <span data-ttu-id="7666d-154">Nastavte proměnnou prostředí PATH tak, aby zahrnovala `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="7666d-154">Set the PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span>

<span data-ttu-id="7666d-155">Než přejdete k další části, můžete před přechodem na další část spustit `dotnet`, `java`, `mvn`, `spark-shell` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7666d-155">Double check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="download-the-microsoftsparkworker-release"></a><span data-ttu-id="7666d-156">Stažení verze Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="7666d-156">Download the Microsoft.Spark.Worker release</span></span>

1. <span data-ttu-id="7666d-157">Stáhněte si verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) ze stránky rozhraní .net pro Apache Spark verze GitHubu do svého místního počítače.</span><span class="sxs-lookup"><span data-stu-id="7666d-157">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub Releases page to your local machine.</span></span> <span data-ttu-id="7666d-158">Můžete ho třeba stáhnout do cesty `c:\bin\Microsoft.Spark.Worker\`.</span><span class="sxs-lookup"><span data-stu-id="7666d-158">For example, you might download it to the path, `c:\bin\Microsoft.Spark.Worker\`.</span></span>

2. <span data-ttu-id="7666d-159">Vytvořte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) nazvanou `DOTNET_WORKER_DIR` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali **Microsoft. spark. Worker**.</span><span class="sxs-lookup"><span data-stu-id="7666d-159">Create a [new environment variable](https://www.java.com/en/download/help/path.xml) called `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the **Microsoft.Spark.Worker**.</span></span> <span data-ttu-id="7666d-160">Například `c:\bin\Microsoft.Spark.Worker`.</span><span class="sxs-lookup"><span data-stu-id="7666d-160">For example, `c:\bin\Microsoft.Spark.Worker`.</span></span>

## <a name="clone-the-net-for-apache-spark-github-repo"></a><span data-ttu-id="7666d-161">Klonovat rozhraní .NET pro Apache Spark úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="7666d-161">Clone the .NET for Apache Spark GitHub repo</span></span>

<span data-ttu-id="7666d-162">K naklonování rozhraní .NET pro Apache Spark úložiště do počítače použijte následující příkaz [GitBash](https://gitforwindows.org/) .</span><span class="sxs-lookup"><span data-stu-id="7666d-162">Use the following [GitBash](https://gitforwindows.org/) command to clone the .NET for Apache Spark repo to your machine.</span></span>

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="7666d-163">Zápis rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7666d-163">Write a .NET for Apache Spark app</span></span>

1. <span data-ttu-id="7666d-164">Otevřete **Visual Studio** a přejděte na **soubor > vytvořit nový projekt > Konzolová aplikace (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="7666d-164">Open **Visual Studio** and navigate to **File > Create New Project > Console App (.NET Core)**.</span></span> <span data-ttu-id="7666d-165">Pojmenujte aplikaci **HelloSpark**.</span><span class="sxs-lookup"><span data-stu-id="7666d-165">Name the application **HelloSpark**.</span></span>

2. <span data-ttu-id="7666d-166">Nainstalujte [balíček NuGet Microsoft. Spark](https://www.nuget.org/profiles/spark).</span><span class="sxs-lookup"><span data-stu-id="7666d-166">Install the [Microsoft.Spark NuGet package](https://www.nuget.org/profiles/spark).</span></span> <span data-ttu-id="7666d-167">Další informace o instalaci balíčků NuGet najdete v tématu [různé způsoby instalace balíčku NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span><span class="sxs-lookup"><span data-stu-id="7666d-167">For more information on installing NuGet packages, see [Different ways to install a NuGet Package](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span></span>

3. <span data-ttu-id="7666d-168">V **Průzkumník řešení**otevřete **program.cs** a napište následující C# kód:</span><span class="sxs-lookup"><span data-stu-id="7666d-168">In **Solution Explorer**, open **Program.cs** and write the following C# code:</span></span>

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. <span data-ttu-id="7666d-169">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="7666d-169">Build the solution.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="7666d-170">Spuštění aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7666d-170">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="7666d-171">Otevřete **PowerShell** a změňte adresář na složku, ve které je uložená vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="7666d-171">Open **PowerShell** and change the directory to the folder where your app is stored.</span></span>

   ```powershell
   cd <your-app-output-directory>
   ```

2. <span data-ttu-id="7666d-172">Vytvořte soubor s názvem **lidi. JSON** s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="7666d-172">Create a file called **people.json** with the following content:</span></span>

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. <span data-ttu-id="7666d-173">Ke spuštění aplikace použijte následující příkaz prostředí PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7666d-173">Use the following PowerShell command to run your app:</span></span>

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

<span data-ttu-id="7666d-174">Gratulujeme!</span><span class="sxs-lookup"><span data-stu-id="7666d-174">Congratulations!</span></span> <span data-ttu-id="7666d-175">Úspěšně jste vytvořili a spustili rozhraní .NET pro Apache Spark aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7666d-175">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7666d-176">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7666d-176">Next steps</span></span>

<span data-ttu-id="7666d-177">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="7666d-177">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7666d-178">Příprava prostředí Windows pro rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7666d-178">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="7666d-179">Stáhnout **Microsoft. spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="7666d-179">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="7666d-180">Sestavení a spuštění jednoduchého rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="7666d-180">Build and run a simple .NET for Apache Spark application</span></span>

<span data-ttu-id="7666d-181">Další informace najdete na stránce prostředky.</span><span class="sxs-lookup"><span data-stu-id="7666d-181">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7666d-182">.NET pro prostředky Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7666d-182">.NET for Apache Spark Resources</span></span>](../resources/index.md)
