---
title: Instalace rozhraní .NET pro Apache Spark na poznámkové bloky Jupyter v clusterech Azure HDInsight Spark
description: Přečtěte si, jak nainstalovat rozhraní .NET pro Apache Spark do poznámkových bloků Jupyter od Azure HDInsight.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 32047efcde093a3752bdd59baa88896d1547b93e
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546747"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="475aa-103">Instalace rozhraní .NET pro Apache Spark na poznámkové bloky Jupyter v clusterech Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="475aa-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="475aa-104">Tento článek vás naučí, jak nainstalovat rozhraní .NET pro Apache Spark na poznámkové bloky Jupyter v clusterech Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="475aa-105">Rozhraní .NET pro Apache Spark můžete nasadit do clusterů Azure HDInsight prostřednictvím kombinace příkazového řádku a portálu Azure (další informace najdete v tématu [jak nasadit aplikaci .NET pro Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)), ale poznámkové bloky poskytují více interaktivní a iterativní prostředí.</span><span class="sxs-lookup"><span data-stu-id="475aa-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="475aa-106">Clustery Azure HDInsight už mají notebooky Jupyter, takže jediné, co musíte udělat, je nakonfigurovat poznámkové bloky Jupyter tak, aby spouštěly rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="475aa-107">Chcete-li použít .NET pro Apache Spark ve vašich poznámkových bloků Jupyter, C# REPL je potřeba ke spuštění kódu C# řádek po řádku a zachovat stav spuštění v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="475aa-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="475aa-108">[Try .NET](https://github.com/dotnet/try) byl integrován jako oficiální .NET REPL.</span><span class="sxs-lookup"><span data-stu-id="475aa-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="475aa-109">Chcete-li povolit rozhraní .NET pro Apache Spark prostřednictvím prostředí Jupyter Notebooks, musíte postupovat podle několika ručních kroků přes [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) a odeslat [akce skriptu](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) v clusteru HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="475aa-110">Tato funkce je *experimentální* a není podporována týmem HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="475aa-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="475aa-111">Prerequisites</span></span>

<span data-ttu-id="475aa-112">Pokud ještě nemáte, vytvořte cluster [Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster)</span><span class="sxs-lookup"><span data-stu-id="475aa-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster) cluster.</span></span>

1. <span data-ttu-id="475aa-113">Navštivte [portál Azure](https://portal.azure.com) a vyberte **+ Vytvořit prostředek**.</span><span class="sxs-lookup"><span data-stu-id="475aa-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="475aa-114">Vytvořte nový prostředek clusteru Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="475aa-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="475aa-115">Vyberte **Spark 2.4** a **HDI 4.0** během vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="475aa-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="475aa-116">Instalace rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="475aa-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="475aa-117">Na webu Azure Portal vyberte **cluster HDInsight Spark,** který jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="475aa-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="475aa-118">Zastavení serveru Livy</span><span class="sxs-lookup"><span data-stu-id="475aa-118">Stop the Livy server</span></span>

1. <span data-ttu-id="475aa-119">Na portálu vyberte **Přehled**a pak vyberte **Ambari home**.</span><span class="sxs-lookup"><span data-stu-id="475aa-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="475aa-120">Po zobrazení výzvy zadejte přihlašovací údaje clusteru.</span><span class="sxs-lookup"><span data-stu-id="475aa-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Zastavit livy server](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="475aa-122">V levé navigační nabídce vyberte **Spark2** a vyberte **LIVY FOR SPARK2 SERVER**.</span><span class="sxs-lookup"><span data-stu-id="475aa-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Zastavit livy server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="475aa-124">Vyberte **hn0... hostitele**.</span><span class="sxs-lookup"><span data-stu-id="475aa-124">Select **hn0... host**.</span></span>

   ![Zastavit livy server](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="475aa-126">Vyberte tři tečky vedle **Livy pro Spark2 Server** a vyberte **Zastavit**.</span><span class="sxs-lookup"><span data-stu-id="475aa-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="475aa-127">Po zobrazení výzvy pokračujte výběrem **možnosti OK.**</span><span class="sxs-lookup"><span data-stu-id="475aa-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="475aa-128">Zastavte Livy pro Spark2 Server.</span><span class="sxs-lookup"><span data-stu-id="475aa-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="475aa-129">![Zastavit livy server](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="475aa-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="475aa-130">Opakujte předchozí kroky pro **hn1... hostitele**.</span><span class="sxs-lookup"><span data-stu-id="475aa-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="475aa-131">Odeslání akce skriptu HDInsight</span><span class="sxs-lookup"><span data-stu-id="475aa-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="475aa-132">Je `install-interactive-notebook.sh` skript, který instaluje .NET pro Apache Spark a provádí změny Apache Livy a sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="475aa-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="475aa-133">Před odesláním akce skriptu do služby HDInsight je třeba vytvořit a nahrát `install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="475aa-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="475aa-134">Vytvořte nový soubor s názvem **install-interactive-notebook.sh** v místním počítači a vložte obsah [install-interactive-notebook.sh obsahu](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="475aa-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="475aa-135">Nahrajte skript do [identifikátoru URI,](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) který je přístupný z clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="475aa-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="475aa-136">Například, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="475aa-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="475aa-137">Spouštění `install-interactive-notebook.sh` v clusteru pomocí [akcí skriptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="475aa-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="475aa-138">Vraťte se do clusteru HDI na webu Azure Portal a z možností vlevo vyberte **Akce skriptu.**</span><span class="sxs-lookup"><span data-stu-id="475aa-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="475aa-139">Odešlete jednu akci skriptu pro nasazení rozhraní .NET pro Apache Spark REPL v clusteru HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="475aa-140">Použijte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="475aa-140">Use the following settings:</span></span>

   |<span data-ttu-id="475aa-141">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="475aa-141">Property</span></span>  |<span data-ttu-id="475aa-142">Popis</span><span class="sxs-lookup"><span data-stu-id="475aa-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="475aa-143">Typ skriptu</span><span class="sxs-lookup"><span data-stu-id="475aa-143">Script type</span></span> | <span data-ttu-id="475aa-144">Vlastní</span><span class="sxs-lookup"><span data-stu-id="475aa-144">Custom</span></span> |
   | <span data-ttu-id="475aa-145">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="475aa-145">Name</span></span> | <span data-ttu-id="475aa-146">*Instalace rozhraní .NET pro interaktivní poznámkové bloky Apache Spark*</span><span class="sxs-lookup"><span data-stu-id="475aa-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="475aa-147">Bash skript URI</span><span class="sxs-lookup"><span data-stu-id="475aa-147">Bash script URI</span></span> | <span data-ttu-id="475aa-148">Identifikátor URI, do `install-interactive-notebook.sh`kterého jste nahráli .</span><span class="sxs-lookup"><span data-stu-id="475aa-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="475aa-149">Typ uzlu</span><span class="sxs-lookup"><span data-stu-id="475aa-149">Node type(s)</span></span>| <span data-ttu-id="475aa-150">Vedoucí a pracovník</span><span class="sxs-lookup"><span data-stu-id="475aa-150">Head and Worker</span></span> |
   | <span data-ttu-id="475aa-151">Parametry</span><span class="sxs-lookup"><span data-stu-id="475aa-151">Parameters</span></span> | <span data-ttu-id="475aa-152">.NET pro verzi Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="475aa-153">Můžete zkontrolovat [.NET pro Apache Spark verze](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="475aa-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="475aa-154">Například, pokud chcete nainstalovat Sparkdotnet verze 0.6.0 `0.6.0`pak by to bylo .</span><span class="sxs-lookup"><span data-stu-id="475aa-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="475aa-155">Přechod na další krok, když se vedle stavu akce skriptu zobrazí zelené značky.</span><span class="sxs-lookup"><span data-stu-id="475aa-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="475aa-156">Spuštění serveru Livy</span><span class="sxs-lookup"><span data-stu-id="475aa-156">Start the Livy server</span></span>

<span data-ttu-id="475aa-157">Postupujte podle pokynů v části [Stop Livy server](#stop-the-livy-server) na **Start** (spíše než **Stop)** Livy for Spark2 Server pro hostitele **hn0** a **hn1**.</span><span class="sxs-lookup"><span data-stu-id="475aa-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="475aa-158">Nastavení výchozích konfigurací Spark</span><span class="sxs-lookup"><span data-stu-id="475aa-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="475aa-159">Na portálu vyberte **Přehled**a pak vyberte **Ambari home**.</span><span class="sxs-lookup"><span data-stu-id="475aa-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="475aa-160">Po zobrazení výzvy zadejte přihlašovací údaje clusteru.</span><span class="sxs-lookup"><span data-stu-id="475aa-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="475aa-161">Vyberte **Spark2** a **CONFIGS**.</span><span class="sxs-lookup"><span data-stu-id="475aa-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="475aa-162">Potom vyberte **Vlastní spark2-výchozí hodnoty**.</span><span class="sxs-lookup"><span data-stu-id="475aa-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Nastavit konfigurace](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="475aa-164">Vyberte **Přidat vlastnost...** a přidejte výchozí nastavení Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Přidat vlastnost](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="475aa-166">Existují tři individuální vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="475aa-166">There are three individual properties.</span></span> <span data-ttu-id="475aa-167">Přidejte je jeden po druhém pomocí typu vlastnosti **TEXT** v režimu přidání vlastnosti Single.</span><span class="sxs-lookup"><span data-stu-id="475aa-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="475aa-168">Zkontrolujte, zda nemáte žádné mezery před nebo za některou z klíčů / hodnot.</span><span class="sxs-lookup"><span data-stu-id="475aa-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="475aa-169">**Vlastnost 1**</span><span class="sxs-lookup"><span data-stu-id="475aa-169">**Property 1**</span></span>
       * <span data-ttu-id="475aa-170">Klíč:&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="475aa-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="475aa-171">Hodnota: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="475aa-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="475aa-172">**Vlastnost 2** Použijte verzi rozhraní .NET pro Apache Spark, kterou jste zahrnuli do předchozí akce skriptu.</span><span class="sxs-lookup"><span data-stu-id="475aa-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="475aa-173">Klíč:&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="475aa-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="475aa-174">Hodnota: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="475aa-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="475aa-175">**Vlastnost 3**</span><span class="sxs-lookup"><span data-stu-id="475aa-175">**Property 3**</span></span>
       * <span data-ttu-id="475aa-176">Klíč:&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="475aa-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="475aa-177">Hodnota: `try`</span><span class="sxs-lookup"><span data-stu-id="475aa-177">Value: `try`</span></span>

   <span data-ttu-id="475aa-178">Například následující obrázek zachycuje nastavení pro přidání vlastnosti 1:</span><span class="sxs-lookup"><span data-stu-id="475aa-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Nastavit konfigurace](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="475aa-180">Po přidání tří vlastností vyberte **ULOŽIT**.</span><span class="sxs-lookup"><span data-stu-id="475aa-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="475aa-181">Pokud se zobrazí varovná obrazovka doporučení konfiguračních konfigurací, vyberte **možnost POKRAČOVAT V OPAČNÉM PŘÍPADĚ**.</span><span class="sxs-lookup"><span data-stu-id="475aa-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="475aa-182">Restartujte ohrožené součásti.</span><span class="sxs-lookup"><span data-stu-id="475aa-182">Restart affected components.</span></span>

   <span data-ttu-id="475aa-183">Po přidání nových vlastností je třeba restartovat součásti, které byly ovlivněny změnami.</span><span class="sxs-lookup"><span data-stu-id="475aa-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="475aa-184">V horní části vyberte **restartovat**a potom **restartujte všechny ovlivněné** z rozevíracího souboru.</span><span class="sxs-lookup"><span data-stu-id="475aa-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Nastavit konfigurace](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="475aa-186">Po zobrazení výzvy vyberte **možnost POTVRDIT RESTART ALL,** chcete-li pokračovat, a pak klepněte na tlačítko **OK,** abyste to dokončili.</span><span class="sxs-lookup"><span data-stu-id="475aa-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="475aa-187">Odeslání úloh prostřednictvím poznámkového bloku Jupyter</span><span class="sxs-lookup"><span data-stu-id="475aa-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="475aa-188">Po dokončení předchozích kroků můžete nyní odeslat úlohy .NET pro Apache Spark prostřednictvím poznámkových bloků Jupyter.</span><span class="sxs-lookup"><span data-stu-id="475aa-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="475aa-189">Vytvořte novou .NET pro poznámkový blok Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="475aa-190">Spusťte poznámkový blok Jupyter z clusteru HDI na webu Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="475aa-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Spuštění notebooku Jupyter](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="475aa-192">Potom vyberte **Nový** > **.NET Spark (C#)** pro vytvoření poznámkového bloku.</span><span class="sxs-lookup"><span data-stu-id="475aa-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Poznámkový blok Jupyter](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="475aa-194">Odeslat úlohy pomocí rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="475aa-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="475aa-195">K vytvoření datového rámce použijte následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="475aa-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Odeslat úlohu Spark](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="475aa-197">Pomocí následujícího fragmentu kódu zaregistrujte uživatelem definovanou funkci (UDF) a použijte UDF s datovými rámci:</span><span class="sxs-lookup"><span data-stu-id="475aa-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Odeslat úlohu Spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="475aa-199">Další kroky</span><span class="sxs-lookup"><span data-stu-id="475aa-199">Next steps</span></span>

* [<span data-ttu-id="475aa-200">Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="475aa-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="475aa-201">Dokumentace ke službě HDInsight</span><span class="sxs-lookup"><span data-stu-id="475aa-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
