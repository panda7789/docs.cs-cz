---
title: Začínáme s .NET pro Apache Spark
description: Zjistěte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows, macOS a Ubuntu.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d7297b11a2b5b21420fcb2f0f9ae823cb29b88d1
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358996"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="d1ead-103">Kurz: Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="d1ead-104">V tomto kurzu se naučíte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows, macOS a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d1ead-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, macOS, and Ubuntu.</span></span>

<span data-ttu-id="d1ead-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="d1ead-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d1ead-106">Příprava prostředí pro .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="d1ead-107">Zápis prvního rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="d1ead-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="d1ead-108">Sestavování a spouštění jednoduchého rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="d1ead-108">Build and run your simple .NET for Apache Spark application</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="d1ead-109">Příprava prostředí</span><span class="sxs-lookup"><span data-stu-id="d1ead-109">Prepare your environment</span></span>

<span data-ttu-id="d1ead-110">Než začnete psát aplikaci, musíte nastavit některé závislosti požadavků.</span><span class="sxs-lookup"><span data-stu-id="d1ead-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="d1ead-111">Pokud `dotnet` `java` `mvn` `spark-shell` v prostředí příkazového řádku můžete spustit,,, je vaše prostředí už připravené a můžete přejít k další části.</span><span class="sxs-lookup"><span data-stu-id="d1ead-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="d1ead-112">Pokud nemůžete spustit žádný z příkazů nebo všechny, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="d1ead-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="d1ead-113">1. instalace .NET</span><span class="sxs-lookup"><span data-stu-id="d1ead-113">1. Install .NET</span></span>

<span data-ttu-id="d1ead-114">Chcete-li začít sestavovat aplikace .NET, je nutné stáhnout a nainstalovat sadu .NET SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="d1ead-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="d1ead-115">Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span><span class="sxs-lookup"><span data-stu-id="d1ead-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="d1ead-116">Instalace sady SDK přidá do `dotnet` své cesty sada nástrojů.</span><span class="sxs-lookup"><span data-stu-id="d1ead-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="d1ead-117">Po instalaci .NET Core SDK otevřete nový příkazový řádek nebo terminál a spusťte příkaz `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="d1ead-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="d1ead-118">Pokud se příkaz spustí a vytiskne informace o použití dotnet, může přejít k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="d1ead-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="d1ead-119">Pokud se zobrazí `'dotnet' is not recognized as an internal or external command` Chyba, před spuštěním příkazu se ujistěte, že jste otevřeli **Nový** příkazový řádek nebo terminál.</span><span class="sxs-lookup"><span data-stu-id="d1ead-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="d1ead-120">2. instalace Java</span><span class="sxs-lookup"><span data-stu-id="d1ead-120">2. Install Java</span></span>

<span data-ttu-id="d1ead-121">Nainstalujte [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pro Windows a MacOS nebo [OpenJDK 8](https://openjdk.java.net/install/) pro Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d1ead-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and macOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="d1ead-122">Vyberte odpovídající verzi pro váš operační systém.</span><span class="sxs-lookup"><span data-stu-id="d1ead-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="d1ead-123">Vyberte například **jdk-8u201-windows-x64.exe** pro počítač se systémem Windows x64 (jak je vidět níže) nebo **JDK-8u231-MacOSX-x64. dmg** pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="d1ead-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for macOS.</span></span> <span data-ttu-id="d1ead-124">Pak pomocí příkazu `java` Ověřte instalaci.</span><span class="sxs-lookup"><span data-stu-id="d1ead-124">Then, use the command `java` to verify the installation.</span></span>

![Stažení Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="d1ead-126">3. instalace kompresního softwaru</span><span class="sxs-lookup"><span data-stu-id="d1ead-126">3. Install compression software</span></span>

<span data-ttu-id="d1ead-127">Apache Spark se stáhl jako komprimovaný soubor. tgz.</span><span class="sxs-lookup"><span data-stu-id="d1ead-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="d1ead-128">K extrakci souboru použijte program pro extrakci, například [7-zip](https://www.7-zip.org/) nebo [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="d1ead-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="d1ead-129">4. instalace Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-129">4. Install Apache Spark</span></span>

<span data-ttu-id="d1ead-130">[Stáhněte a nainstalujte Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="d1ead-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="d1ead-131">Bude nutné vybrat z verze 2,3. \* nebo 2.4.0, 2.4.1, 2.4.3 nebo 2.4.4 (rozhraní .NET pro Apache Spark není kompatibilní s jinými verzemi Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="d1ead-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="d1ead-132">Příkazy použité v následujících krocích předpokládají, že jste [stáhli a nainstalovali Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="d1ead-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="d1ead-133">Pokud chcete použít jinou verzi, nahraďte hodnotu **2.4.1** příslušným číslem verze.</span><span class="sxs-lookup"><span data-stu-id="d1ead-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="d1ead-134">Pak extrahujte soubor **. tar** a Apache Spark soubory.</span><span class="sxs-lookup"><span data-stu-id="d1ead-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="d1ead-135">Extrahování vnořeného souboru **. tar** :</span><span class="sxs-lookup"><span data-stu-id="d1ead-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="d1ead-136">Vyhledejte soubor **Spark-2.4.1-bin-Hadoop 2.7. tgz** , který jste si stáhli.</span><span class="sxs-lookup"><span data-stu-id="d1ead-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="d1ead-137">Klikněte pravým tlačítkem na soubor a vyberte **7-zip-> extrakci**.</span><span class="sxs-lookup"><span data-stu-id="d1ead-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="d1ead-138">**Spark-2.4.1-bin-Hadoop 2.7. tar** se vytvoří společně s souborem **. tgz** , který jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="d1ead-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="d1ead-139">Extrahování Apache Spark souborů:</span><span class="sxs-lookup"><span data-stu-id="d1ead-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="d1ead-140">Klikněte pravým tlačítkem na **Spark-2.4.1-bin-Hadoop 2.7. tar** a vyberte **7-zip-> extrahování souborů...**</span><span class="sxs-lookup"><span data-stu-id="d1ead-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="d1ead-141">Do pole **extrahovat do** zadejte **C:\Bin** .</span><span class="sxs-lookup"><span data-stu-id="d1ead-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="d1ead-142">Zrušte zaškrtnutí políčka pod polem **extrahovat do** .</span><span class="sxs-lookup"><span data-stu-id="d1ead-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="d1ead-143">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="d1ead-143">Select **OK**.</span></span>
* <span data-ttu-id="d1ead-144">Soubory Apache Spark jsou extrahovány do C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="d1ead-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Instalace Sparku](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="d1ead-146">Spuštěním následujících příkazů nastavte proměnné prostředí používané k vyhledání Apache Spark ve **Windows**:</span><span class="sxs-lookup"><span data-stu-id="d1ead-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="d1ead-147">Spuštěním následujících příkazů nastavte proměnné prostředí používané k vyhledání Apache Spark v **MacOS** a **Ubuntu**:</span><span class="sxs-lookup"><span data-stu-id="d1ead-147">Run the following commands to set the environment variables used to locate Apache Spark on **macOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="d1ead-148">Jakmile nainstalujete vše a nastavíte proměnné prostředí, otevřete **Nový** příkazový řádek nebo terminál a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1ead-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="d1ead-149">Pokud se příkaz spustí a zobrazí informace o verzi, můžete přejít k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="d1ead-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="d1ead-150">Pokud se zobrazí `'spark-submit' is not recognized as an internal or external command` Chyba, ujistěte se, že jste otevřeli **Nový** příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="d1ead-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="d1ead-151">5. Nainstalujte rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="d1ead-152">Stáhněte si verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) z rozhraní .net pro Apache Spark GitHub.</span><span class="sxs-lookup"><span data-stu-id="d1ead-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="d1ead-153">Pokud jste například na počítači s Windows a plánujete použít .NET Core, [Stáhněte si verzi Windows x64 netcoreapp 3.1](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span><span class="sxs-lookup"><span data-stu-id="d1ead-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="d1ead-154">Extrakce Microsoft. spark. Worker:</span><span class="sxs-lookup"><span data-stu-id="d1ead-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="d1ead-155">Vyhledejte soubor **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** , který jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="d1ead-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="d1ead-156">Klikněte pravým tlačítkem a vyberte **7-zip-> extrahování souborů...**.</span><span class="sxs-lookup"><span data-stu-id="d1ead-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="d1ead-157">Do pole **extrahovat do** zadejte **C:\Bin** .</span><span class="sxs-lookup"><span data-stu-id="d1ead-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="d1ead-158">Zrušte zaškrtnutí políčka pod polem **extrahovat do** .</span><span class="sxs-lookup"><span data-stu-id="d1ead-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="d1ead-159">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="d1ead-159">Select **OK**.</span></span>

![Instalace .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="d1ead-161">6. instalace WinUtils (jenom Windows)</span><span class="sxs-lookup"><span data-stu-id="d1ead-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="d1ead-162">Rozhraní .NET pro Apache Spark vyžaduje, aby se WinUtils nainstalovaly společně s Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="d1ead-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="d1ead-163">[Stáhněte si winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="d1ead-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="d1ead-164">Pak zkopírujte WinUtils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="d1ead-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="d1ead-165">Pokud používáte jinou verzi systému Hadoop, která je Poznáma na konci názvu instalační složky Sparku, [Vyberte verzi WinUtils](https://github.com/steveloughran/winutils) , která je kompatibilní s vaší verzí Hadoop.</span><span class="sxs-lookup"><span data-stu-id="d1ead-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="d1ead-166">7. Nastavte DOTNET_WORKER_DIR a ověřte závislosti.</span><span class="sxs-lookup"><span data-stu-id="d1ead-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="d1ead-167">Spusťte jeden z následujících příkazů, abyste nastavili `DOTNET_WORKER_DIR` proměnnou prostředí, kterou aplikace .NET používá k vyhledání rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="d1ead-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="d1ead-168">V **systému Windows**vytvořte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali Microsoft. spark. Worker (například `C:\bin\Microsoft.Spark.Worker\` ).</span><span class="sxs-lookup"><span data-stu-id="d1ead-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="d1ead-169">V **MacOS**vytvořte novou proměnnou prostředí pomocí `export DOTNET_WORKER_DIR <your_path>` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali Microsoft. spark. Worker (například *~/bin/Microsoft.spark.Worker/*).</span><span class="sxs-lookup"><span data-stu-id="d1ead-169">On **macOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="d1ead-170">V **Ubuntu**vytvořte [novou proměnnou prostředí](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` a nastavte ji do adresáře, do kterého jste stáhli a extrahovali Microsoft. spark. Worker (například *~/bin/Microsoft.spark.Worker*).</span><span class="sxs-lookup"><span data-stu-id="d1ead-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="d1ead-171">Nakonec dvakrát kontrolujte, že `dotnet` `java` `mvn` `spark-shell` před přechodem na další část můžete z příkazového řádku spustit,,.</span><span class="sxs-lookup"><span data-stu-id="d1ead-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="d1ead-172">Zápis rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="d1ead-173">1. vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="d1ead-173">1. Create a console app</span></span>

<span data-ttu-id="d1ead-174">V příkazovém řádku nebo terminálu spusťte následující příkazy k vytvoření nové konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="d1ead-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="d1ead-175">`dotnet`Příkaz vytvoří `new` aplikaci typu `console` pro vás.</span><span class="sxs-lookup"><span data-stu-id="d1ead-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="d1ead-176">`-o`Parametr vytvoří adresář s názvem *mySparkApp* , kde je vaše aplikace uložená, a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="d1ead-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="d1ead-177">`cd mySparkApp`Příkaz změní adresář na adresář aplikace, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="d1ead-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="d1ead-178">2. instalace balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="d1ead-178">2. Install NuGet package</span></span>

<span data-ttu-id="d1ead-179">Pokud chcete použít .NET pro Apache Spark v aplikaci, nainstalujte balíček Microsoft. spark.</span><span class="sxs-lookup"><span data-stu-id="d1ead-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="d1ead-180">V příkazovém řádku nebo terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1ead-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="d1ead-181">3. kódování aplikace</span><span class="sxs-lookup"><span data-stu-id="d1ead-181">3. Code your app</span></span>

<span data-ttu-id="d1ead-182">Otevřete *program.cs* v Visual Studio Code nebo libovolný textový editor a nahraďte celý kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d1ead-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="d1ead-183">4. vytvoření a přidání datového souboru</span><span class="sxs-lookup"><span data-stu-id="d1ead-183">4. Create and add a data file</span></span>

<span data-ttu-id="d1ead-184">Otevřete příkazový řádek nebo terminál a přejděte do složky aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1ead-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="d1ead-185">Vaše aplikace zpracovává soubor obsahující řádky textu.</span><span class="sxs-lookup"><span data-stu-id="d1ead-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="d1ead-186">Vytvořte soubor *input.txt* v adresáři *mySparkApp* , který obsahuje následující text:</span><span class="sxs-lookup"><span data-stu-id="d1ead-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="d1ead-187">Spuštění aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="d1ead-188">Spuštěním následujícího příkazu sestavte aplikaci:</span><span class="sxs-lookup"><span data-stu-id="d1ead-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="d1ead-189">Spuštěním následujícího příkazu odešlete aplikaci, která se má spustit na Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="d1ead-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="d1ead-190">Tento příkaz předpokládá, že jste stáhli Apache Spark a přidali ho do proměnné prostředí PATH, aby bylo možné ho použít `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="d1ead-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="d1ead-191">V opačném případě byste měli použít úplnou cestu (například *C:\bin\apache-spark\bin\spark-Submit* nebo *~/Spark/bin/Spark-Submit*).</span><span class="sxs-lookup"><span data-stu-id="d1ead-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="d1ead-192">Po spuštění vaší aplikace se do konzoly zapíše data počtu slov *input.txt* souboru.</span><span class="sxs-lookup"><span data-stu-id="d1ead-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="d1ead-193">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="d1ead-193">Congratulations!</span></span> <span data-ttu-id="d1ead-194">Úspěšně jste vytvořili a spustili rozhraní .NET pro Apache Spark aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d1ead-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d1ead-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d1ead-195">Next steps</span></span>

<span data-ttu-id="d1ead-196">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="d1ead-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="d1ead-197">Příprava prostředí Windows pro rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="d1ead-198">Zápis prvního rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="d1ead-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="d1ead-199">Sestavování a spouštění jednoduchého rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="d1ead-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="d1ead-200">Pokud se chcete podívat na video s vysvětlením výše uvedených kroků, Zarezervujte si [řadu videí .NET pro Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="d1ead-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="d1ead-201">Další informace najdete na stránce prostředky.</span><span class="sxs-lookup"><span data-stu-id="d1ead-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d1ead-202">.NET pro prostředky Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ead-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
