---
title: Analýza mínění pomocí rozhraní příkazového řádku ML.NET
description: Automaticky generovat model ML a související kód Jazyka C# z ukázkové datové sady
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc
ms.topic: tutorial,mlnet-tooling
ms.openlocfilehash: d817e173239d2848fb16e94cca8ead563bc900a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187624"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="0f7ee-103">Analýza mínění pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="0f7ee-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="0f7ee-104">Zjistěte, jak pomocí ML.NET cli automaticky generovat ML.NET modelu a základní kód C#.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="0f7ee-105">Poskytujete datovou sadu a úlohu strojového učení, kterou chcete implementovat, a cli používá modul Automatické ml k vytvoření generování modelu a zdrojového kódu nasazení, stejně jako binární model.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="0f7ee-106">V tomto kurzu provedete následující kroky:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0f7ee-107">Příprava dat na vybraný úkol strojového učení</span><span class="sxs-lookup"><span data-stu-id="0f7ee-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="0f7ee-108">Spusťte příkaz "mlnet auto-train" z rozhraní příkazového příkazu</span><span class="sxs-lookup"><span data-stu-id="0f7ee-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> - <span data-ttu-id="0f7ee-109">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="0f7ee-109">Review the quality metric results</span></span>
> - <span data-ttu-id="0f7ee-110">Principy generované ho C# kód pro použití modelu ve vaší aplikaci</span><span class="sxs-lookup"><span data-stu-id="0f7ee-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="0f7ee-111">Prozkoumejte vygenerovaný kód jazyka C#, který byl použit k trénování modelu</span><span class="sxs-lookup"><span data-stu-id="0f7ee-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="0f7ee-112">Toto téma odkazuje na nástroj ML.NET cli, který je aktuálně ve verzi Preview, a materiál může být může být může změnit.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="0f7ee-113">Další informace naleznete na [stránce ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="0f7ee-114">ML.NET CLI je součástí ML.NET a jeho hlavním cílem je "demokratizovat" ML.NET pro vývojáře .NET při učení ML.NET, takže nemusíte kódovat od nuly, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="0f7ee-115">PříkazclML.NET můžete spustit na libovolném příkazovém řádku (Windows, Mac nebo Linux) a generovat kvalitní ML.NET modely a zdrojový kód založený na trénovacích datových sadách, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="0f7ee-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f7ee-116">Pre-requisites</span></span>

- <span data-ttu-id="0f7ee-117">[Sada .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo novější</span><span class="sxs-lookup"><span data-stu-id="0f7ee-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="0f7ee-118">(Nepovinné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="0f7ee-119">Rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="0f7ee-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="0f7ee-120">Můžete buď spustit vygenerované projekty kódu Jazyka `dotnet run` C# z Visual Studia nebo pomocí (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="0f7ee-121">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="0f7ee-121">Prepare your data</span></span>

<span data-ttu-id="0f7ee-122">Budeme používat existující datovou sadu použitou pro scénář analýzy mínění, což je úloha strojového učení s binární klasifikací.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="0f7ee-123">Můžete použít vlastní datovou sadu podobným způsobem a model a kód budou generovány za vás.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="0f7ee-124">Stáhněte si [soubor zip datové sady UCI Sentiment Labeled Sentences (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte jej v libovolné složce, kterou zvolíte.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f7ee-125">Datové sady tohoto kurzu používá datovou sadu ze skupiny na jednotlivé popisky pomocí deep features, Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="0f7ee-126">KDD 2015 a hostované v Úložišti strojového učení UCI - Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="0f7ee-127">Úložiště strojového učeníhttp://archive.ics.uci.edu/mlUCI [ ].</span><span class="sxs-lookup"><span data-stu-id="0f7ee-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="0f7ee-128">Irvine, KALIFORNIE: Kalifornská univerzita, Škola informací a informatiky.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="0f7ee-129">Zkopírujte `yelp_labelled.txt` soubor do libovolné složky, `/cli-test`kterou jste dříve vytvořili (například ).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="0f7ee-130">Otevřete upřednostňovaný příkazový řádek a přesuňte se do složky, do které jste soubor datové sady zkopírovali.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="0f7ee-131">Například:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="0f7ee-132">Pomocí libovolného textového `yelp_labelled.txt` editoru, jako je například Visual Studio Code, můžete otevřít a prozkoumat soubor datové sady.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="0f7ee-133">Můžete vidět, že struktura je:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="0f7ee-134">Soubor nemá záhlaví.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-134">The file has no header.</span></span> <span data-ttu-id="0f7ee-135">Budete používat index sloupce.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-135">You will use the column's index.</span></span>

    - <span data-ttu-id="0f7ee-136">Existují pouze dva sloupce:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-136">There are just two columns:</span></span>

        | <span data-ttu-id="0f7ee-137">Text (index sloupce 0)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-137">Text (Column index 0)</span></span> | <span data-ttu-id="0f7ee-138">Popisek (index sloupce 1)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="0f7ee-139">Wow... Miloval toto místo.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-139">Wow... Loved this place.</span></span> | <span data-ttu-id="0f7ee-140">1</span><span class="sxs-lookup"><span data-stu-id="0f7ee-140">1</span></span> |
        | <span data-ttu-id="0f7ee-141">Kůrka není dobrá.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-141">Crust is not good.</span></span> | <span data-ttu-id="0f7ee-142">0</span><span class="sxs-lookup"><span data-stu-id="0f7ee-142">0</span></span> |
        | <span data-ttu-id="0f7ee-143">Není chutné a textura byla prostě ošklivá.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="0f7ee-144">0</span><span class="sxs-lookup"><span data-stu-id="0f7ee-144">0</span></span> |
        | <span data-ttu-id="0f7ee-145">... MNOHO DALŠÍCH ŘÁDKŮ TEXTU...</span><span class="sxs-lookup"><span data-stu-id="0f7ee-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="0f7ee-146">... (1 nebo 0)...</span><span class="sxs-lookup"><span data-stu-id="0f7ee-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="0f7ee-147">Ujistěte se, že jste soubor datové sady zavřeli z editoru.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="0f7ee-148">Nyní jste připraveni začít používat vykreslování lisování- lis pro tento scénář analýzy mínění.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f7ee-149">Po dokončení tohoto kurzu můžete také vyzkoušet s vlastní datové sady tak dlouho, dokud jsou připraveny k použití pro některý z úkolů ML v současné době podporuje ML.NET CLI Preview, které jsou *'binární klasifikace', 'Multi-class Klasifikace' a 'Regrese'*).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="0f7ee-150">Spuštění příkazu "mlnet auto-train"</span><span class="sxs-lookup"><span data-stu-id="0f7ee-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="0f7ee-151">Spusťte následující ML.NET příkazem příkazu příkazu k příkazu příkazu:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="0f7ee-152">Tento příkaz spustí \*\* `mlnet auto-train` příkaz\*\*:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="0f7ee-153">pro **úlohu typu ML\*\*\*\*`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="0f7ee-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="0f7ee-154">používá **soubor `yelp_labelled.txt` datové sady** jako trénovací a testovací datovou sadu (interní zaostřovací systém buď použije křížové ověření, nebo jej rozdělí do dvou datových sad, jednu pro školení a jednu pro testování)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="0f7ee-155">kde **sloupec cíle/cíle,** který chcete předpovědět (běžně nazývaný **"popisek"),** je **sloupec s indexem 1** (to je druhý sloupec, protože index je založen na nule)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="0f7ee-156">**Nepoužívá záhlaví souboru** s názvy sloupců, protože tento konkrétní soubor datové sady nemá záhlaví</span><span class="sxs-lookup"><span data-stu-id="0f7ee-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="0f7ee-157">**cílená doba průzkumu** experimentu je **10 sekund**</span><span class="sxs-lookup"><span data-stu-id="0f7ee-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="0f7ee-158">Zobrazí se výstup z cli, podobně jako:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[<span data-ttu-id="0f7ee-159">Windows</span><span class="sxs-lookup"><span data-stu-id="0f7ee-159">Windows</span></span>](#tab/windows)

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[<span data-ttu-id="0f7ee-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="0f7ee-161">macOS Bash</span></span>](#tab/macosbash)

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="0f7ee-163">V tomto konkrétním případě, za pouhých 10 sekund a s malou datovou sadou k dispozici, nástroj CLI byl schopen spustit poměrně málo iterací, což znamená školení vícekrát na základě různých kombinací algoritmů / konfigurace s různými interními transformacemi dat a hyperparametry algoritmu.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="0f7ee-164">Konečně, "nejlepší kvalita" model nalezený za 10 sekund je model pomocí konkrétního trenéra / algoritmu s jakoukoli konkrétní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="0f7ee-165">V závislosti na době průzkumu příkaz může způsobit jiný výsledek.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="0f7ee-166">Výběr je založen na více zobrazených `Accuracy`metrikách, například .</span><span class="sxs-lookup"><span data-stu-id="0f7ee-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="0f7ee-167">**Pochopení metrik kvality modelu**</span><span class="sxs-lookup"><span data-stu-id="0f7ee-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="0f7ee-168">První a nejjednodušší metrika pro vyhodnocení binárního klasifikačního modelu je přesnost, která je snadno pochopitelná.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="0f7ee-169">"Přesnost je podíl správných předpovědí se sadou testovacích dat.".</span><span class="sxs-lookup"><span data-stu-id="0f7ee-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="0f7ee-170">Čím blíže k 100% (1,00), tím lépe.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="0f7ee-171">Existují však případy, kdy stačí měření s metrikou přesnost nestačí, zejména pokud popisek (0 a 1 v tomto případě) je nevyvážený v testovací datové sadě.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="0f7ee-172">Další metriky a **podrobnější informace o metrikách,** jako je přesnost, AUC, AUCPR a skóre F1 použité k vyhodnocení různých modelů, najdete v [tématu Principy ML.NET metriky](../resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f7ee-173">Můžete zkusit tuto velmi stejnou datovou `--max-exploration-time` sadu a zadat několik minut (například tři minuty, takže zadáte 180 sekund), který najde lepší "nejlepší model" pro vás s jinou konfiguraci trénovacího kanálu pro tuto datovou sadu (což je docela malé, 1000 řádků).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="0f7ee-174">Chcete-li najít model "nejlepší/dobrá kvalita", který je "model připravený k výrobě" zaměřený na větší datové sady, měli byste provádět experimenty s příkazovým příkazem, který obvykle určuje mnohem více času průzkumu v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="0f7ee-175">Ve skutečnosti v mnoha případech můžete vyžadovat více hodin doby průzkumu, zejména pokud je datová sada velká na řádcích a sloupcích.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="0f7ee-176">Předchozí spuštění příkazu vygenerovalo následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="0f7ee-177">Serializovaný model .zip ("nejlepší model") připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-177">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="0f7ee-178">C# kód ke spuštění/skóre, které generované model (Chcete-li předpovědi v aplikacích koncových uživatelů s tímto modelem).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="0f7ee-179">C# trénovací kód používaný ke generování tohoto modelu (Učení účely).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="0f7ee-180">Soubor protokolu se všemi prozkoumány iterací s konkrétní podrobné informace o každém algoritmu se snažil s jeho kombinací hyper-parametry a transformace dat.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="0f7ee-181">První dva majetek (. ZIP model souboru a C# kód pro spuštění tohoto modelu) lze přímo použít ve vašich aplikacích pro koncové uživatele (ASP.NET základní webové aplikace, služby, desktop aplikace, atd.) k předpovědi s tímto generovaným modelem ML.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="0f7ee-182">Třetí prostředek, trénovací kód, vám ukáže, jaký ML.NET kód rozhraní API byl použit rozhraním API k trénování generovaného modelu, takže můžete zjistit, jaké konkrétní trenér/algoritmus a hyperparametry byly vybrány rozhraní matřištěm.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="0f7ee-183">Tyto výčtové prostředky jsou vysvětleny v následujících krocích kurzu.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="0f7ee-184">Prozkoumejte vygenerovaný kód Jazyka C#, který se má použít pro spuštění modelu, aby se předpovědi</span><span class="sxs-lookup"><span data-stu-id="0f7ee-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="0f7ee-185">V sadě Visual Studio (2017 nebo 2019) otevřete řešení generované ve složce `SampleBinaryClassification` `/cli-test`pojmenované v původní cílové složce (v kurzu byl pojmenován).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="0f7ee-186">Měli byste vidět řešení podobné:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f7ee-187">V kurzu doporučujeme použít Visual Studio, ale můžete také prozkoumat generovaný kód Jazyka C# (dva projekty) s libovolným textovým editorem a spustit vygenerovanou konzolovou aplikaci s počítačem `dotnet CLI` s macOS, Linuxem nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Řešení VS generované cli](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="0f7ee-189">Vygenerovaná **knihovna tříd** obsahující serializovaný model ML (soubor ZIP) a datové třídy (datové modely) je něco, co můžete přímo použít v aplikaci koncového uživatele, a to i přímým odkazováním na tuto knihovnu tříd (nebo přesunutím kódu, jak dáváte přednost).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="0f7ee-190">Vygenerovaná **konzolová aplikace** obsahuje kód spuštění, který je nutné zkontrolovat, a pak obvykle znovu použijete "bodovací kód" (kód, který spouští model ML, aby se předpovědi) přesunutím tohoto jednoduchého kódu (jen několik řádků) do aplikace koncového uživatele, kde chcete provést předpovědi.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="0f7ee-191">Otevřete **soubory tříd ModelInput.cs** a **ModelOutput.cs** v rámci projektu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="0f7ee-192">Uvidíte, že tyto třídy jsou "třídy dat" nebo POCO třídy používané k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="0f7ee-193">Je to 'často používaný kód', ale užitečné mít generované, pokud vaše datová sada má desítky nebo dokonce stovky sloupců.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="0f7ee-194">Třída `ModelInput` se používá při čtení dat z datové sady.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-194">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="0f7ee-195">Třída `ModelOutput` se používá k získání výsledku předpověď (data předpověď).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="0f7ee-196">Otevřete soubor Program.cs a prozkoumejte kód.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="0f7ee-197">V několika řádcích, budete moci spustit model a provést ukázkovou předpověď.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

    - <span data-ttu-id="0f7ee-198">První řádek kódu jednoduše `MLContext` vytvoří objekt potřebný při každém spuštění ML.NET kódu.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span>

    - <span data-ttu-id="0f7ee-199">Druhý řádek kódu je komentovaný, protože nemusíte trénovat model, protože byl již vyškolen pro vás nástrojem CLI a uložen do modelu serializované . ZIP.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="0f7ee-200">Ale pokud chcete vidět *"jak byl model trénovaný"* cli, můžete odkomentovat tento řádek a spustit/ladit trénovací kód používaný pro tento konkrétní model ML.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

    - <span data-ttu-id="0f7ee-201">Ve třetím řádku kódu načtete model z serializovaného modelu . ZIP s `mlContext.Model.Load()` rozhraním API poskytnutím cesty k tomuto modelu . ZIP.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

    - <span data-ttu-id="0f7ee-202">Ve čtvrtém řádku kódu načtete `PredictionEngine` vytvořit `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` objekt s rozhraním API.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="0f7ee-203">Potřebujete `PredictionEngine` objekt vždy, když chcete provést předpověď cílení na jeden vzorek dat (V tomto případě jeden kus textu předpovědět jeho mínění).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

    - <span data-ttu-id="0f7ee-204">Pátý řádek kódu je místo, kde můžete vytvořit, že *jeden ukázková data,* která mají být použita pro předpověď voláním funkce `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="0f7ee-205">Vzhledem k tomu, že nástroj zaokreslování nezná, jaký druh ukázkových dat použít, v rámci této funkce načítá první řádek datové sady.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="0f7ee-206">V tomto případě však můžete také vytvořit vlastní "pevně zakódovaná" `CreateSingleDataSample()` data namísto aktuální implementace funkce aktualizací tohoto jednoduššího kódu implementujícího tuto funkci:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. <span data-ttu-id="0f7ee-207">Spusťte projekt, a to buď pomocí původní ukázková data načtená z prvního řádku datové sady nebo poskytnutím vlastních pevně zakódovaných ukázkových dat.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="0f7ee-208">Měli byste získat předpověď srovnatelnou s:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-208">You should get a prediction comparable to:</span></span>

    # <a name="windows"></a>[<span data-ttu-id="0f7ee-209">Windows</span><span class="sxs-lookup"><span data-stu-id="0f7ee-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="0f7ee-210">Spusťte konzolovou aplikaci z Visual Studia stisknutím tlačítka F5 (Přehrát):</span><span class="sxs-lookup"><span data-stu-id="0f7ee-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="0f7ee-212">)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-212">)</span></span>

    # <a name="macos-bash"></a>[<span data-ttu-id="0f7ee-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="0f7ee-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="0f7ee-214">Spusťte konzolovou aplikaci z příkazového řádku zadáním následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-214">Run the console app from the command-prompt by typing the following commands:</span></span>

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="0f7ee-216">)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-216">)</span></span>

    ---

1. <span data-ttu-id="0f7ee-217">Zkuste změnit pevně zakódovaná ukázková data na jiné věty s jiným míněním a podívejte se, jak model předpovídá pozitivní nebo negativní mínění.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="0f7ee-218">Naplnit aplikace koncových uživatelů předpověďmi modelu ML</span><span class="sxs-lookup"><span data-stu-id="0f7ee-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="0f7ee-219">Můžete použít podobný "ML model bodovací kód" ke spuštění modelu v aplikaci koncového uživatele a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="0f7ee-220">Například můžete přímo přesunout tento kód do libovolné desktopové aplikace systému Windows, jako je **WPF** a **WinForms** a spustit model stejným způsobem, než tomu bylo v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="0f7ee-221">Způsob implementace těchto řádků kódu pro spuštění modelu ML by však měl být optimalizován (tj. ukládat soubor modelu do mezipaměti a načíst jej jednou) a mít objekty singleton namísto jejich vytváření při každém požadavku, zejména pokud vaše aplikace musí být škálovatelná, například webové aplikace nebo distribuované služby, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="0f7ee-222">Spuštění ML.NET modelů v škálovatelných ASP.NET webových aplikací a služeb Core (aplikace s více vlákny)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="0f7ee-223">Vytvoření objektu modelu`ITransformer` (načteného ze souboru .zip `PredictionEngine` modelu) a objektu by mělo být optimalizováno zejména při spuštění v škálovatelných webových aplikacích a distribuovaných službách.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="0f7ee-224">Pro první případ je objekt`ITransformer`modelu ( ) optimalizace přímočará.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="0f7ee-225">Vzhledem `ITransformer` k tomu, že objekt je bezpečný pro přístup z více vláken, můžete objekt uložit do mezipaměti jako objekt singleton nebo statický objekt, takže model načtete jednou.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="0f7ee-226">Pro druhý objekt, `PredictionEngine` objekt, není to tak `PredictionEngine` snadné, protože objekt není bezpečný pro přístup z více vláken, proto nelze vytvořit konkretní tento objekt jako singleton nebo statický objekt v aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="0f7ee-227">Tento problém s bezpečností a škálovatelností pro vlákna je hluboce popsán v tomto [příspěvku blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="0f7ee-228">Nicméně, věci dostal mnohem jednodušší pro vás, než to, co je vysvětleno v tomto blogu.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="0f7ee-229">Pracovali jsme na jednodušším přístupu pro vás a vytvořili jsme pěkný **'.NET Core Integration Package',** který můžete snadno použít ve vašem ASP.NET základní aplikace a služby tím, že ji zaregistrujete v aplikaci DI služby (služby vkládání závislostí) a pak jej přímo používat z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="0f7ee-230">Podívejte se na následující kurz a příklad pro to, že:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="0f7ee-231">Kurz: Spuštění ML.NET modelů na škálovatelných ASP.NET webových aplikacích Core a webapii</span><span class="sxs-lookup"><span data-stu-id="0f7ee-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="0f7ee-232">Ukázka: Škálovatelný model ML.NET na rozhraní ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="0f7ee-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="0f7ee-233">Prozkoumejte generovaný kód Jazyka C#, který byl použit k trénování modelu "nejlepší kvality"</span><span class="sxs-lookup"><span data-stu-id="0f7ee-233">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="0f7ee-234">Pro pokročilejší účely učení můžete také prozkoumat generovaný kód Jazyka C#, který byl použit nástrojem cli k trénování generovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="0f7ee-235">Tento "kód modelu školení" je aktuálně generován ve `ModelBuilder` vlastní třídě generované s názvem, takže můžete prozkoumat, že kód školení.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="0f7ee-236">Ještě důležitější je, pro tento konkrétní scénář (sentiment analýza modelu) můžete také porovnat, že generované trénovací kód s kódem vysvětleným v následujícím kurzu:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="0f7ee-237">Porovnat: [Kurz: Použití ML.NET v binárním klasifikačním scénáři analýzy mínění](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="0f7ee-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="0f7ee-238">Je zajímavé porovnat zvolený algoritmus a konfiguraci kanálu v kurzu s kódem generovaným nástrojem CLI.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="0f7ee-239">V závislosti na tom, kolik času strávíte iterace a hledání lepších modelů, může být zvolený algoritmus odlišný spolu s jeho konkrétní hyper-parametry a konfigurace kanálu.</span><span class="sxs-lookup"><span data-stu-id="0f7ee-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="0f7ee-240">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="0f7ee-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0f7ee-241">Příprava dat na vybraný úkol ML (problém k vyřešení)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-241">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="0f7ee-242">Spuštění příkazu "mlnet auto-train" v nástroji rozhraní příkazového příkazu</span><span class="sxs-lookup"><span data-stu-id="0f7ee-242">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> - <span data-ttu-id="0f7ee-243">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="0f7ee-243">Review the quality metric results</span></span>
> - <span data-ttu-id="0f7ee-244">Principy generované ho C# kód pro spuštění modelu (Kód pro použití v aplikaci koncového uživatele)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-244">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="0f7ee-245">Prozkoumejte generovaný kód Jazyka C#, který byl použit k trénování modelu "nejlepší kvality" (účely učení)</span><span class="sxs-lookup"><span data-stu-id="0f7ee-245">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="0f7ee-246">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f7ee-246">See also</span></span>

- [<span data-ttu-id="0f7ee-247">Automatizace tréninku modelu pomocí ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="0f7ee-247">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="0f7ee-248">Kurz: Spuštění ML.NET modelů na škálovatelných ASP.NET webových aplikacích Core a webapii</span><span class="sxs-lookup"><span data-stu-id="0f7ee-248">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="0f7ee-249">Ukázka: Škálovatelný model ML.NET na rozhraní ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="0f7ee-249">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="0f7ee-250">ML.NET referenční příručka příkazu automatického vlakového ústrojí ML.NET</span><span class="sxs-lookup"><span data-stu-id="0f7ee-250">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="0f7ee-251">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="0f7ee-251">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
