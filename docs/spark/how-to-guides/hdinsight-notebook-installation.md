---
title: Instalace rozhraní .NET pro Apache Spark na poznámkových blocích Jupyter v clusterech s Azure HDInsight Spark
description: Přečtěte si, jak nainstalovat .NET pro Apache Spark v poznámkových blocích Jupyter v Azure HDInsight.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617740"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="e4907-103">Instalace rozhraní .NET pro Apache Spark na poznámkových blocích Jupyter v clusterech s Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="e4907-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="e4907-104">V tomto článku se dozvíte, jak nainstalovat .NET pro Apache Spark na poznámkových blocích Jupyter v clusterech s Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="e4907-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="e4907-105">.NET pro Apache Spark v clusterech Azure HDInsight můžete nasadit pomocí kombinace příkazového řádku a Azure Portal (Další informace najdete v tématu [Jak nasadit rozhraní .NET pro Apache Spark aplikaci do služby Azure HDInsight](../tutorials/hdinsight-deployment.md)), ale poznámkové bloky poskytují interaktivní a iterativní možnosti.</span><span class="sxs-lookup"><span data-stu-id="e4907-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="e4907-106">Clustery Azure HDInsight se už dodávají s poznámkovým blokem Jupyter, takže stačí, když nakonfigurujete poznámkové bloky Jupyter tak, aby spouštěly rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e4907-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="e4907-107">Chcete-li použít rozhraní .NET pro Apache Spark ve vašich poznámkových blocích Jupyter, je nutné, aby byl kód jazyka C# spouštěn po řádku a aby v případě potřeby zachoval stav provádění.</span><span class="sxs-lookup"><span data-stu-id="e4907-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="e4907-108">[Vyzkoušejte rozhraní .NET](https://github.com/dotnet/try) , které je integrované jako oficiální REPL .NET.</span><span class="sxs-lookup"><span data-stu-id="e4907-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="e4907-109">Pokud chcete povolit rozhraní .NET pro Apache Spark prostřednictvím Jupyter poznámkových bloků, je nutné provést několik ručních kroků prostřednictvím [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) a odeslat [akce skriptu](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) v clusteru HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="e4907-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="e4907-110">Tato funkce je *experimentální* a tým HDInsight Spark ho nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="e4907-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="e4907-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4907-111">Prerequisites</span></span>

<span data-ttu-id="e4907-112">Pokud ho ještě nemáte, vytvořte cluster [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) .</span><span class="sxs-lookup"><span data-stu-id="e4907-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="e4907-113">Přejděte na [Azure Portal](https://portal.azure.com) a vyberte **+ vytvořit prostředek**.</span><span class="sxs-lookup"><span data-stu-id="e4907-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="e4907-114">Vytvořte nový prostředek clusteru Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="e4907-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="e4907-115">Během vytváření clusteru vyberte **Spark 2,4** a **HDI 4,0** .</span><span class="sxs-lookup"><span data-stu-id="e4907-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="e4907-116">Instalace rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e4907-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="e4907-117">V Azure Portal vyberte **cluster HDInsight Spark** , který jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="e4907-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="e4907-118">Zastavení serveru Livy</span><span class="sxs-lookup"><span data-stu-id="e4907-118">Stop the Livy server</span></span>

1. <span data-ttu-id="e4907-119">Na portálu vyberte **Přehled**a pak vyberte **Ambari Home (domů**).</span><span class="sxs-lookup"><span data-stu-id="e4907-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="e4907-120">Pokud se zobrazí výzva, zadejte přihlašovací údaje pro cluster.</span><span class="sxs-lookup"><span data-stu-id="e4907-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Zastavit Livy Server](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="e4907-122">V levé navigační nabídce vyberte **Spark2** a jako **Server Spark2 vyberte LIVY**.</span><span class="sxs-lookup"><span data-stu-id="e4907-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Zastavit Livy Server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="e4907-124">Vybrat **hn0... Hostitel**:</span><span class="sxs-lookup"><span data-stu-id="e4907-124">Select **hn0... host**.</span></span>

   ![Zastavit Livy Server](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="e4907-126">Vyberte tři tečky vedle **Livy pro server Spark2** a vyberte **zastavit**.</span><span class="sxs-lookup"><span data-stu-id="e4907-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="e4907-127">Po zobrazení výzvy pokračujte výběrem **OK** .</span><span class="sxs-lookup"><span data-stu-id="e4907-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="e4907-128">Zastavte Livy pro server Spark2.</span><span class="sxs-lookup"><span data-stu-id="e4907-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="e4907-129">![Zastavit Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="e4907-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="e4907-130">Opakujte předchozí postup pro **HN1... Hostitel**:</span><span class="sxs-lookup"><span data-stu-id="e4907-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="e4907-131">Odeslat akci skriptu HDInsight</span><span class="sxs-lookup"><span data-stu-id="e4907-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="e4907-132">`install-interactive-notebook.sh`Je skript, který nainstaluje rozhraní .NET pro Apache Spark a provede změny v Apache Livy a sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="e4907-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="e4907-133">Než odešlete akci skriptu do HDInsight, je potřeba vytvořit a nahrát `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="e4907-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="e4907-134">V místním počítači vytvořte nový soubor s názvem **install-Interactive-notebook.sh** a vložte obsah [install-Interactive-notebook.sh obsahu](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="e4907-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="e4907-135">Nahrajte skript do [identifikátoru URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) , který je přístupný z clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="e4907-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="e4907-136">Například, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="e4907-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="e4907-137">Spusťte `install-interactive-notebook.sh` v clusteru pomocí [akcí skriptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="e4907-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="e4907-138">Vraťte se do clusteru HDI ve Azure Portal a vyberte **akce skriptu** z možností na levé straně.</span><span class="sxs-lookup"><span data-stu-id="e4907-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="e4907-139">Odešlete jednu akci skriptu pro nasazení rozhraní .NET pro Apache Spark REPL do clusteru HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="e4907-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="e4907-140">Použijte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="e4907-140">Use the following settings:</span></span>

   |<span data-ttu-id="e4907-141">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e4907-141">Property</span></span>  |<span data-ttu-id="e4907-142">Popis</span><span class="sxs-lookup"><span data-stu-id="e4907-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="e4907-143">Typ skriptu</span><span class="sxs-lookup"><span data-stu-id="e4907-143">Script type</span></span> | <span data-ttu-id="e4907-144">Vlastní</span><span class="sxs-lookup"><span data-stu-id="e4907-144">Custom</span></span> |
   | <span data-ttu-id="e4907-145">Name</span><span class="sxs-lookup"><span data-stu-id="e4907-145">Name</span></span> | <span data-ttu-id="e4907-146">*Instalace rozhraní .NET pro Apache Spark interaktivní Poznámkový blok*</span><span class="sxs-lookup"><span data-stu-id="e4907-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="e4907-147">Identifikátor URI skriptu bash</span><span class="sxs-lookup"><span data-stu-id="e4907-147">Bash script URI</span></span> | <span data-ttu-id="e4907-148">Identifikátor URI, na který jste nahráli `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="e4907-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="e4907-149">Typ (typy) uzlů</span><span class="sxs-lookup"><span data-stu-id="e4907-149">Node type(s)</span></span>| <span data-ttu-id="e4907-150">Vedoucí a pracovní proces</span><span class="sxs-lookup"><span data-stu-id="e4907-150">Head and Worker</span></span> |
   | <span data-ttu-id="e4907-151">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4907-151">Parameters</span></span> | <span data-ttu-id="e4907-152">Rozhraní .NET pro Apache Spark verzi.</span><span class="sxs-lookup"><span data-stu-id="e4907-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="e4907-153">Můžete kontrolovat [verze rozhraní .NET pro Apache Spark](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="e4907-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="e4907-154">Například pokud chcete nainstalovat Sparkdotnet verze 0.6.0, bude `0.6.0` .</span><span class="sxs-lookup"><span data-stu-id="e4907-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="e4907-155">Přejděte k dalšímu kroku, když se vedle stavu akce skriptu zobrazí zelené zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="e4907-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="e4907-156">Spuštění serveru Livy</span><span class="sxs-lookup"><span data-stu-id="e4907-156">Start the Livy server</span></span>

<span data-ttu-id="e4907-157">Postupujte podle pokynů v oddílu [zastavení Livy serveru](#stop-the-livy-server) a **Spusťte** (místo **zastavení**) Livy pro server Spark2 pro hostitele **hn0** a **HN1**.</span><span class="sxs-lookup"><span data-stu-id="e4907-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="e4907-158">Nastavení výchozích konfigurací Sparku</span><span class="sxs-lookup"><span data-stu-id="e4907-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="e4907-159">Na portálu vyberte **Přehled**a pak vyberte **Ambari Home (domů**).</span><span class="sxs-lookup"><span data-stu-id="e4907-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="e4907-160">Po zobrazení výzvy zadejte přihlašovací údaje clusteru.</span><span class="sxs-lookup"><span data-stu-id="e4907-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="e4907-161">Vyberte **Spark2** a **Konfigurace**.</span><span class="sxs-lookup"><span data-stu-id="e4907-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="e4907-162">Pak vyberte **vlastní spark2 – výchozí**.</span><span class="sxs-lookup"><span data-stu-id="e4907-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Nastavení konfigurací](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="e4907-164">Pokud chcete přidat výchozí nastavení Sparku, vyberte **Přidat vlastnost...**</span><span class="sxs-lookup"><span data-stu-id="e4907-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Přidat vlastnost](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="e4907-166">Existují tři jednotlivé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e4907-166">There are three individual properties.</span></span> <span data-ttu-id="e4907-167">Současně je přidejte pomocí typu vlastnosti **text** v režimu přidání jedné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e4907-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="e4907-168">Ověřte, že nemáte žádné nadbytečné mezery před nebo za libovolnými klíči/hodnotami.</span><span class="sxs-lookup"><span data-stu-id="e4907-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="e4907-169">**Vlastnost 1**</span><span class="sxs-lookup"><span data-stu-id="e4907-169">**Property 1**</span></span>
       * <span data-ttu-id="e4907-170">Zkrat&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="e4907-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="e4907-171">Hodnota: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="e4907-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="e4907-172">**Vlastnost 2** Použijte verzi rozhraní .NET pro Apache Spark, kterou jste zahrnuli do předchozí akce skriptu.</span><span class="sxs-lookup"><span data-stu-id="e4907-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="e4907-173">Zkrat&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="e4907-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="e4907-174">Hodnota: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="e4907-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="e4907-175">**Vlastnost 3**</span><span class="sxs-lookup"><span data-stu-id="e4907-175">**Property 3**</span></span>
       * <span data-ttu-id="e4907-176">Zkrat&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="e4907-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="e4907-177">Hodnota: `try`</span><span class="sxs-lookup"><span data-stu-id="e4907-177">Value: `try`</span></span>

   <span data-ttu-id="e4907-178">Například následující obrázek zachytí nastavení pro přidání vlastnosti 1:</span><span class="sxs-lookup"><span data-stu-id="e4907-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Nastavení konfigurací](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="e4907-180">Po přidání tří vlastností vyberte **Uložit**.</span><span class="sxs-lookup"><span data-stu-id="e4907-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="e4907-181">Pokud se zobrazí varovná obrazovka s doporučeními pro konfiguraci, vyberte **pokračovat**.</span><span class="sxs-lookup"><span data-stu-id="e4907-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="e4907-182">Příslušné součásti restartujte.</span><span class="sxs-lookup"><span data-stu-id="e4907-182">Restart affected components.</span></span>

   <span data-ttu-id="e4907-183">Po přidání nových vlastností je nutné restartovat součásti, které byly ovlivněny změnami.</span><span class="sxs-lookup"><span data-stu-id="e4907-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="e4907-184">V horní části vyberte **restartovat**a pak **všechny ovlivněné** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="e4907-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Nastavení konfigurací](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="e4907-186">Po zobrazení výzvy vyberte **Potvrdit RESTARTOVÁNÍ všech** , aby se dalo dokončit, a pak klikněte na **OK** .</span><span class="sxs-lookup"><span data-stu-id="e4907-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="e4907-187">Odesílání úloh prostřednictvím poznámkového bloku Jupyter</span><span class="sxs-lookup"><span data-stu-id="e4907-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="e4907-188">Po dokončení předchozích kroků můžete nyní odeslat .NET pro Apache Spark úlohy prostřednictvím poznámkových bloků Jupyter.</span><span class="sxs-lookup"><span data-stu-id="e4907-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="e4907-189">Vytvoří nový Poznámkový blok .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e4907-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="e4907-190">Z clusteru HDI z Azure Portal spusťte Poznámkový blok Jupyter.</span><span class="sxs-lookup"><span data-stu-id="e4907-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Spustit Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="e4907-192">Pak vyberte **Nový**  >  **.NET Spark (C#)** a vytvořte Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="e4907-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Poznámkový blok Jupyter](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="e4907-194">Odeslání úloh pomocí .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e4907-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="e4907-195">Pomocí následujícího fragmentu kódu vytvořte datový rámec:</span><span class="sxs-lookup"><span data-stu-id="e4907-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Odeslat Sparkovou úlohu](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="e4907-197">Pomocí následujícího fragmentu kódu Zaregistrujte uživatelsky definovanou funkci (UDF) a použijte UDF s datovými rámečky:</span><span class="sxs-lookup"><span data-stu-id="e4907-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Odeslat Sparkovou úlohu](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="e4907-199">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e4907-199">Next steps</span></span>

* [<span data-ttu-id="e4907-200">Nasazení aplikace .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="e4907-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="e4907-201">Dokumentace ke službě HDInsight</span><span class="sxs-lookup"><span data-stu-id="e4907-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
