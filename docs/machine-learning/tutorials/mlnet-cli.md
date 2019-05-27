---
title: Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku ML.NET
description: Automaticky generovat modelu ML a související C# kódu z ukázkové datové sadě
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 029685be9d44ad947d4291912d7da1d8ce73d52a
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053649"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a><span data-ttu-id="7577f-103">Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7577f-103">Auto generate a binary classifier using the CLI</span></span>

<span data-ttu-id="7577f-104">Další informace o použití rozhraní příkazového řádku ML.NET k automatickému generování modelu ML.NET a příslušná C# kódu.</span><span class="sxs-lookup"><span data-stu-id="7577f-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="7577f-105">Zadejte vaše datová sada a strojového učení úkol, který chcete implementovat a rozhraní příkazového řádku používá modul AutoML pro vytvoření generování modelu a nasazení zdrojového kódu, jakož i binárnímu modelu.</span><span class="sxs-lookup"><span data-stu-id="7577f-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="7577f-106">V tomto kurzu provedete následující kroky:</span><span class="sxs-lookup"><span data-stu-id="7577f-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7577f-107">Příprava dat pro úlohu učení vybraný počítač</span><span class="sxs-lookup"><span data-stu-id="7577f-107">Prepare your data for the selected machine learning task</span></span>
> * <span data-ttu-id="7577f-108">Z rozhraní příkazového řádku spusťte příkaz "mlnet automaticky – train"</span><span class="sxs-lookup"><span data-stu-id="7577f-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> * <span data-ttu-id="7577f-109">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="7577f-109">Review the quality metric results</span></span>
> * <span data-ttu-id="7577f-110">Vysvětlení generované C# kódu k použití modelu v aplikaci</span><span class="sxs-lookup"><span data-stu-id="7577f-110">Understand the generated C# code to use the model in your application</span></span>
> * <span data-ttu-id="7577f-111">Prozkoumejte generované C# kód, který byl použit pro trénování modelu</span><span class="sxs-lookup"><span data-stu-id="7577f-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="7577f-112">Toto téma odkazuje na nástroj ML.NET rozhraní příkazového řádku, který je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="7577f-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="7577f-113">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7577f-113">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="7577f-114">Rozhraní příkazového řádku ML.NET je součástí ML.NET a jeho hlavním cílem je "demokratizaci" ML.NET pro vývojáře na platformě .NET při učení ML.NET, takže není nutné do kódu od začátku začít.</span><span class="sxs-lookup"><span data-stu-id="7577f-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="7577f-115">Rozhraní příkazového řádku ML.NET můžete spustit na libovolné příkazového řádku (Windows, Mac nebo Linux) ke generování kvalitních ML.NET modely a zdrojový kód podle cvičných datových sad, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="7577f-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="7577f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7577f-116">Pre-requisites</span></span>

- <span data-ttu-id="7577f-117">[Sada .NET core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo novější</span><span class="sxs-lookup"><span data-stu-id="7577f-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="7577f-118">(Volitelné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="7577f-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="7577f-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="7577f-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="7577f-120">Můžete spustit buď generované C# projekty ze sady Visual Studio nebo pomocí kódu `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="7577f-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="7577f-121">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="7577f-121">Prepare your data</span></span>

<span data-ttu-id="7577f-122">Budeme používat existující datovou sadu používají pro scénáře "Analýza mínění", což je úloha binární klasifikace strojového učení.</span><span class="sxs-lookup"><span data-stu-id="7577f-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="7577f-123">Vlastní datové sady můžete použít podobným způsobem, a modelu a kódu vygeneruje se pro vás.</span><span class="sxs-lookup"><span data-stu-id="7577f-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="7577f-124">Stáhněte si [soubor zip The UCI subjektivního hodnocení s popiskem věty datové sady (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho v jakékoli složce zvolíte.</span><span class="sxs-lookup"><span data-stu-id="7577f-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7577f-125">Datové sady v tomto kurzu používá datovou sadu ze "From skupiny na jednotlivé popisky pomocí podrobné funkce" Kotzias a další.</span><span class="sxs-lookup"><span data-stu-id="7577f-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="7577f-126">Konference KDD 2015 a hostované v UCI Machine Learning úložiště – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="7577f-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="7577f-127">UCI strojového učení úložiště [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="7577f-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="7577f-128">Irvine, certifikační Autorita: University of California, z informací o škole a počítačových věd.</span><span class="sxs-lookup"><span data-stu-id="7577f-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="7577f-129">Kopírovat `yelp_labelled.txt` souboru do libovolné složky, kterou jste vytvořili dřív (například `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="7577f-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="7577f-130">Otevřete upřednostňované příkazový řádek a přejděte do složky, kam jste zkopírovali soubor datové sady.</span><span class="sxs-lookup"><span data-stu-id="7577f-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="7577f-131">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7577f-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="7577f-132">Pomocí libovolného textového editoru, jako je Visual Studio Code, můžete otevřít a prozkoumejte `yelp_labelled.txt` soubor datové sady.</span><span class="sxs-lookup"><span data-stu-id="7577f-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="7577f-133">Uvidíte, že struktura je:</span><span class="sxs-lookup"><span data-stu-id="7577f-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="7577f-134">Soubor nemá žádné hlavičky.</span><span class="sxs-lookup"><span data-stu-id="7577f-134">The file has no header.</span></span> <span data-ttu-id="7577f-135">Sloupce indexu bude používat.</span><span class="sxs-lookup"><span data-stu-id="7577f-135">You will use the column's index.</span></span>

    - <span data-ttu-id="7577f-136">Existují jenom dva sloupce:</span><span class="sxs-lookup"><span data-stu-id="7577f-136">There are just two columns:</span></span>

        | <span data-ttu-id="7577f-137">Text (index sloupce 0)</span><span class="sxs-lookup"><span data-stu-id="7577f-137">Text (Column index 0)</span></span> | <span data-ttu-id="7577f-138">Popisek (index sloupce 1)</span><span class="sxs-lookup"><span data-stu-id="7577f-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="7577f-139">WOW... Miluju toto místo.</span><span class="sxs-lookup"><span data-stu-id="7577f-139">Wow... Loved this place.</span></span> | <span data-ttu-id="7577f-140">1</span><span class="sxs-lookup"><span data-stu-id="7577f-140">1</span></span> |
        | <span data-ttu-id="7577f-141">Povrch ovšem není vhodné.</span><span class="sxs-lookup"><span data-stu-id="7577f-141">Crust is not good.</span></span> | <span data-ttu-id="7577f-142">0</span><span class="sxs-lookup"><span data-stu-id="7577f-142">0</span></span> |
        | <span data-ttu-id="7577f-143">Není tasty a byla právě nepříjemným textury.</span><span class="sxs-lookup"><span data-stu-id="7577f-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="7577f-144">0</span><span class="sxs-lookup"><span data-stu-id="7577f-144">0</span></span> |
        | <span data-ttu-id="7577f-145">... MNOHO VÍCE ŘÁDKŮ TEXTU...</span><span class="sxs-lookup"><span data-stu-id="7577f-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="7577f-146">... (1 nebo 0)...</span><span class="sxs-lookup"><span data-stu-id="7577f-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="7577f-147">Ujistěte se, že zavřete soubor datové sady z editoru.</span><span class="sxs-lookup"><span data-stu-id="7577f-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="7577f-148">Nyní jste připraveni začít používat rozhraní příkazového řádku pro tento scénář "Analýza mínění".</span><span class="sxs-lookup"><span data-stu-id="7577f-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7577f-149">Po dokončení tohoto kurzu můžete také zkusit s vlastními datovými sadami, dokud jsou připravená k použití pro všechny úkoly ML aktuálně podporované ve verzi Preview ML.NET rozhraní příkazového řádku, které jsou *"Binární klasifikace", "Roc klasifikaci" a " Regrese "*).</span><span class="sxs-lookup"><span data-stu-id="7577f-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="7577f-150">Spusťte příkaz "mlnet automaticky – train"</span><span class="sxs-lookup"><span data-stu-id="7577f-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="7577f-151">Spusťte následující příkaz rozhraní příkazového řádku ML.NET:</span><span class="sxs-lookup"><span data-stu-id="7577f-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="7577f-152">Tento příkaz spustí  **`mlnet auto-train` příkaz**:</span><span class="sxs-lookup"><span data-stu-id="7577f-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="7577f-153">pro **ML úloh** typu **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="7577f-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="7577f-154">používá **soubor datové sady `yelp_labelled.txt`**  jako trénování a testování datovou sadu (interně rozhraní příkazového řádku se použít křížové ověření nebo rozdělit ji ve dvou datových sad, jeden pro trénování a jeden pro účely testování)</span><span class="sxs-lookup"><span data-stu-id="7577f-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="7577f-155">kde **cíle/cílový sloupec** chcete předpovědět (obvykle říká **"štítku"**) je **sloupec s indexem 1** (to znamená druhý sloupec, protože index je založený na nule )</span><span class="sxs-lookup"><span data-stu-id="7577f-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="7577f-156">nemá **nepoužívat záhlaví souboru** s názvy sloupců, protože tento konkrétní datové sady soubor nemá hlavičku</span><span class="sxs-lookup"><span data-stu-id="7577f-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="7577f-157">**cílené zkoumání čas** experimentu je **10 sekund**</span><span class="sxs-lookup"><span data-stu-id="7577f-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="7577f-158">Zobrazí se výstup z rozhraní příkazového řádku, podobně jako:</span><span class="sxs-lookup"><span data-stu-id="7577f-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="7577f-159">Windows</span><span class="sxs-lookup"><span data-stu-id="7577f-159">Windows</span></span>](#tab/windows)

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="7577f-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="7577f-161">macOS Bash</span></span>](#tab/macosbash)

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="7577f-163">V tomto konkrétním případě v jenom 10 sekund a u malé datové sady k dispozici, nástroj rozhraní příkazového řádku bylo možné spustit poměrně několika iteracích, což znamená více než jednou podle různých kombinací algoritmy/konfigurace s různými daty interních školení transformace a pro algoritmus hyperparametrů.</span><span class="sxs-lookup"><span data-stu-id="7577f-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="7577f-164">A konečně "co nejlepší kvalitu" modelu nalezen za 10 sekund je model s použitím konkrétního trainer/algoritmu s žádnou zvláštní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7577f-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="7577f-165">V závislosti na času zkoumání příkaz může vytvářet jiné výsledky.</span><span class="sxs-lookup"><span data-stu-id="7577f-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="7577f-166">Výběr vychází z více metrik zobrazených, jako například `Accuracy`.</span><span class="sxs-lookup"><span data-stu-id="7577f-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="7577f-167">**Principy metrik kvality modelu**</span><span class="sxs-lookup"><span data-stu-id="7577f-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="7577f-168">První a nejjednodušší metrika k vyhodnocení binární klasifikační model je přesnost, což je srozumitelný.</span><span class="sxs-lookup"><span data-stu-id="7577f-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="7577f-169">"Přesnost je poměr správné předpovědi s testovací datové sady.".</span><span class="sxs-lookup"><span data-stu-id="7577f-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="7577f-170">Blíže na 100 % (1,00), tím lépe.</span><span class="sxs-lookup"><span data-stu-id="7577f-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="7577f-171">Existují však případy, kde právě s metrikou přesnost měření nestačí, zejména v případě, že je v datové sadě testů nevyvážená popisek (0 a 1 v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="7577f-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="7577f-172">Pro další metriky a další **podrobné informace o metriky** například přesnost, AUC, AUCPR F1 skóre používá k vyhodnocení různých modelů, můžete si přečíst [Principy ML.NET metriky](../resources/metrics.md)</span><span class="sxs-lookup"><span data-stu-id="7577f-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    >  <span data-ttu-id="7577f-173">Můžete zkuste tento velmi stejné datové sady a zadejte několik minut, než `--max-exploration-time` (například tři minuty umožňující vám zadat 180 sekund) který najdou lepší "nejlepší model" za vás s konfigurací kanálu různých školení pro tuto datovou sadu (což je velmi malé, řádky 1000).</span><span class="sxs-lookup"><span data-stu-id="7577f-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="7577f-174">Pokud chcete zjistit "kvality nejlepší/dobré" model, který je "připravené pro produkční prostředí model" cílení na větších datových sad, měli byste zajistit experimenty pomocí rozhraní příkazového řádku zadáním obvykle mnohem více času zkoumání v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="7577f-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="7577f-175">Ve skutečnosti v řadě případů může vyžadovat více hodin od času zkoumání zejména v případě, že datová sada je velká na řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="7577f-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="7577f-176">Předchozí provádění příkazu vygenerovalo následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="7577f-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="7577f-177">Serializovaný model soubor .zip ("nejlepší model") připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="7577f-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="7577f-178">C#vytvořit kód pro spuštění/skóre, které model (k následné predikci ve vašich aplikacích koncového uživatele pomocí tohoto modelu).</span><span class="sxs-lookup"><span data-stu-id="7577f-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="7577f-179">C#školení kód používaný k vygenerování tohoto modelu (výukové účely).</span><span class="sxs-lookup"><span data-stu-id="7577f-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="7577f-180">Soubor protokolu s všech iterací s konkrétní podrobnosti o jednotlivých algoritmů s jeho kombinací hyperparametry a data transformace prozkoumali jste ji.</span><span class="sxs-lookup"><span data-stu-id="7577f-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="7577f-181">První dva prostředky (. Model souboru ZIP a C# kód ke spuštění tohoto modelu) lze použít přímo v aplikacích s koncovým uživatelem (webové aplikace ASP.NET Core, služby, aplikace klasické pracovní plochy, atd.) k následné predikci s generovaných modelu ML.</span><span class="sxs-lookup"><span data-stu-id="7577f-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="7577f-182">Třetí asset školení kód ukazuje, jaký kód ML.NET API rozhraní příkazového řádku použil tak moct trénovat vygenerovaný model, takže si můžete zjistit, jaké konkrétní trainer/algoritmus a hyperparametrů nebyly vybrány pomocí rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7577f-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="7577f-183">Tyto prostředky výčtu jsou vysvětlené v následujících krocích tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="7577f-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="7577f-184">Prozkoumejte generované C# kód, který použijete pro spouštění model k predikci</span><span class="sxs-lookup"><span data-stu-id="7577f-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="7577f-185">V sadě Visual Studio (2017 nebo 2019) otevřete řešení, vygeneruje ve složce s názvem `SampleBinaryClassification` v rámci původní cílovou složku (v tomto kurzu se název `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="7577f-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="7577f-186">Měli byste vidět podobně jako řešení:</span><span class="sxs-lookup"><span data-stu-id="7577f-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="7577f-187">V tomto kurzu doporučujeme používat Visual Studio, ale můžete si taky prostudovat generované C# (dva projekty) pomocí libovolného textového editoru kódu a spuštění aplikace vygenerované konzoly v jazyce `dotnet CLI` v systému macOS, počítače s Linuxem nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="7577f-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Řešení VS, které jsou generovány pomocí rozhraní příkazového řádku](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="7577f-189">Vygenerovaný **knihovny tříd** obsahující serializovaná modelu ML (soubor .zip) a datových tříd (datové modely) je něco, co chcete využít přímo ve vaší aplikaci koncový uživatel ještě můžete přímo odkazuje na knihovny tříd (nebo při přenosech kód, jako je dáváte přednost).</span><span class="sxs-lookup"><span data-stu-id="7577f-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="7577f-190">Vygenerovaný **konzolovou aplikaci** obsahuje provádění kód, který musíte zkontrolovat, a potom obvykle budou bodování kód (kód, který spouští modelu ML k následné predikci) tohoto jednoduchého kódu (jenom pár řádků) se přesunete na vaše koncové uživatele aplikace, ve které chcete predikci.</span><span class="sxs-lookup"><span data-stu-id="7577f-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="7577f-191">Otevřít **ModelInput.cs** a **ModelOutput.cs** třídy souborů v projektu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="7577f-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="7577f-192">Uvidíte, že tyto třídy jsou 'datové třídy' nebo POCO třídy sloužící k uchování dat.</span><span class="sxs-lookup"><span data-stu-id="7577f-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="7577f-193">Je "často používaný kód", ale užitečné mít je generována, pokud vaše datová sada obsahuje desítky nebo stovky sloupce.</span><span class="sxs-lookup"><span data-stu-id="7577f-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="7577f-194">`ModelInput` Třída se používá při čtení dat z datové sady.</span><span class="sxs-lookup"><span data-stu-id="7577f-194">The `ModelInput` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="7577f-195">`ModelOutput` Třída se používá k získání výsledku predikcí (předpověď data).</span><span class="sxs-lookup"><span data-stu-id="7577f-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="7577f-196">Otevřete soubor Program.cs a prozkoumejte kód.</span><span class="sxs-lookup"><span data-stu-id="7577f-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="7577f-197">V několika málo řádků budete moct spustit model a předpověď vzorku.</span><span class="sxs-lookup"><span data-stu-id="7577f-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

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

- <span data-ttu-id="7577f-198">První řádek kódu jednoduše vytvoří `MLContext` objektů potřebných při každém spuštění ML.NET kódu.</span><span class="sxs-lookup"><span data-stu-id="7577f-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="7577f-199">Druhý řádek kódu je zakomentovaný, protože není nutné pro trénování, že serializován model, protože byl již školení pro vás pomocí nástroje příkazového řádku a uloží do modelu. Soubor ZIP.</span><span class="sxs-lookup"><span data-stu-id="7577f-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="7577f-200">Ale pokud chcete zobrazit *"jak model se trénuje"* pomocí rozhraní příkazového řádku, mohli byste zrušením komentáře u tohoto řádku a spustit/ladit kód školení použité pro tento konkrétní modelu ML.</span><span class="sxs-lookup"><span data-stu-id="7577f-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="7577f-201">Na třetím řádku kódu načíst model z serializovaný model. Soubor ZIP s `mlContext.Model.Load()` API tím, že poskytuje cestu k tomuto modelu. Soubor ZIP.</span><span class="sxs-lookup"><span data-stu-id="7577f-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="7577f-202">Na čtvrtém řádku kódu můžete načíst vytvořit `PredictionEngine` objektu `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7577f-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="7577f-203">Je nutné `PredictionEngine` objekt vždy, když chcete při předpovědích cílí na jeden vzorek dat (v tomto případě jediný textu k předpovědi jeho mínění).</span><span class="sxs-lookup"><span data-stu-id="7577f-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="7577f-204">Pátý řádek kódu je, kde můžete vytvářet, který *jedna ukázková data* použitého pro předpověď voláním funkce `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="7577f-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="7577f-205">Protože nástroj rozhraní příkazového řádku nebude vědět, jaký druh ukázková data se mají použít, v rámci této funkce nahrávání první řádek datové sady.</span><span class="sxs-lookup"><span data-stu-id="7577f-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="7577f-206">Ale pro tento případ můžete také vytvořit můžete vlastní data "pevně" namísto aktuální implementace `CreateSingleDataSample()` funkce aktualizací takto jednodušší implementaci této funkce:</span><span class="sxs-lookup"><span data-stu-id="7577f-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="7577f-207">Spusťte projekt, buď pomocí původní ukázková data načíst z prvního řádku datové sady nebo tím, že poskytuje vlastní pevně zakódovaný ukázková data.</span><span class="sxs-lookup"><span data-stu-id="7577f-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="7577f-208">By vám měl predikcí srovnatelná s hodnotou:</span><span class="sxs-lookup"><span data-stu-id="7577f-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="7577f-209">Windows</span><span class="sxs-lookup"><span data-stu-id="7577f-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="7577f-210">Spustit konzolovou aplikaci v sadě Visual Studio stisknutím klávesy F5 (tlačítko Přehrát):</span><span class="sxs-lookup"><span data-stu-id="7577f-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="7577f-212">)</span><span class="sxs-lookup"><span data-stu-id="7577f-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="7577f-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="7577f-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="7577f-214">Spuštění aplikace konzoly z příkazového řádku zadáním následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="7577f-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="7577f-216">)</span><span class="sxs-lookup"><span data-stu-id="7577f-216">)</span></span>

    ---

1. <span data-ttu-id="7577f-217">Zkuste změnit pevně zakódované ukázková data do jiných vět s jinou mínění a podívejte, jak tento model předpovídá pozitivní nebo negativní zabarvení.</span><span class="sxs-lookup"><span data-stu-id="7577f-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="7577f-218">Do vašich koncových uživatelů aplikací vnést předpovědí modelu ML</span><span class="sxs-lookup"><span data-stu-id="7577f-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="7577f-219">Můžete použít, podobně jako "ML model bodování kódu" spustit model ve vašich koncových uživatelů aplikace a zkontrolujte předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7577f-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="7577f-220">Například může přímo přesunete tento kód do jakékoli aplikace klasické pracovní plochy Windows, jako **WPF** a **WinForms** a spustit model stejným způsobem, než jste to udělali v aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="7577f-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="7577f-221">Ale způsob, jak implementovat tyto řádky kódu ke spuštění modelu ML by mělo být optimalizované (která je mezipaměť souboru .zip modelu a načtěte ho jednou) a máte objektů typu singleton místo vytvoření u každého požadavku, zejména v případě, že vaše aplikace musí být škálovatelné, jako webové aplikace nebo distribuované služby, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="7577f-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="7577f-222">Spouštění modelů ML.NET škálovatelné webové aplikace ASP.NET Core a služby (vícevláknové aplikace)</span><span class="sxs-lookup"><span data-stu-id="7577f-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="7577f-223">Vytvoření modelu objektu (`ITransformer` načtenou ze souboru ZIP do modelu) a `PredictionEngine` objektu by mělo být optimalizované, zejména pokud provozujete škálovatelných webových aplikací a distribuované služby.</span><span class="sxs-lookup"><span data-stu-id="7577f-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="7577f-224">Pro první případ objekt modelu (`ITransformer`) optimalizace je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="7577f-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="7577f-225">Vzhledem k tomu, `ITransformer` objekt je bezpečná pro vlákno, můžete ukládat do mezipaměti objekt jako singleton nebo statický objekt, načíst model jednou.</span><span class="sxs-lookup"><span data-stu-id="7577f-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="7577f-226">Pro druhý objekt `PredictionEngine` objektu, není to jednoduché vzhledem k tomu `PredictionEngine` objektu není bezpečná pro vlákno, proto nelze vytvořit instanci tohoto objektu jako singleton nebo statických objektů v aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7577f-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="7577f-227">Tento problém bezpečné pro vlákna a škálovatelnost je podmínkou pro výrazně popsané v tomto [Blogový příspěvek](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="7577f-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="7577f-228">Ale bylo mnohem snazší pro vás než jak je vysvětleno v tomto blogovém příspěvku.</span><span class="sxs-lookup"><span data-stu-id="7577f-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="7577f-229">Jsme pro vás byla vhodná v jednodušší přístup a vytvořili dobrý **balíček .NET Core integrace** , snadno můžete ve svých aplikacích ASP.NET Core a služby tak, že zaregistrujete ve službě aplikace DI (injektáž závislostí služby) a pak přímo použít v kódu.</span><span class="sxs-lookup"><span data-stu-id="7577f-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="7577f-230">Zkontrolujte následující kurz a příklad učinit:</span><span class="sxs-lookup"><span data-stu-id="7577f-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="7577f-231">Kurz: Spouštění modelů ML.NET v ASP.NET Core škálovatelné webové aplikace a WebAPIs</span><span class="sxs-lookup"><span data-stu-id="7577f-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="7577f-232">Ukázka: Škálovatelný model ML.NET v ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="7577f-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="7577f-233">Prozkoumejte generované C# kód, který byl použit pro trénování modelu "co nejlepší kvalitu"</span><span class="sxs-lookup"><span data-stu-id="7577f-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="7577f-234">Pro další pokročilé výukové účely, můžete si taky prostudovat generované C# kód, který se použil nástroj rozhraní příkazového řádku pro trénování vytvořený model.</span><span class="sxs-lookup"><span data-stu-id="7577f-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="7577f-235">Že "trénování modelu kódu" je momentálně ve třídě vlastní, vygenerované s názvem `ModelBuilder` tak můžete prozkoumat tento kód školení.</span><span class="sxs-lookup"><span data-stu-id="7577f-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="7577f-236">Důležitější je pro tento konkrétní scénář (modelů analýza mínění) můžete také porovnat, že kód vygenerovaný školení s kódem je popsáno v následujícím kurzu:</span><span class="sxs-lookup"><span data-stu-id="7577f-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="7577f-237">Porovnání: [Kurz: Použít ve scénáři binární klasifikace analýzy subjektivního hodnocení ML.NET](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="7577f-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="7577f-238">To je zajímavé k porovnání zvolené konfigurace algoritmus a kanál v tomto kurzu se kód vygenerovaný pomocí nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7577f-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="7577f-239">V závislosti na tom, kolik času trávíte iterace a vyhledávání pro lepší modely mohou být odlišná spolu s jeho konkrétním hyperparametry a konfigurace kanálu zvolený algoritmus.</span><span class="sxs-lookup"><span data-stu-id="7577f-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="7577f-240">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7577f-240">See also</span></span>

- [<span data-ttu-id="7577f-241">Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="7577f-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="7577f-242">Kurz: Spouštění modelů ML.NET v ASP.NET Core škálovatelné webové aplikace a WebAPIs</span><span class="sxs-lookup"><span data-stu-id="7577f-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="7577f-243">Ukázka: Škálovatelný model ML.NET v ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="7577f-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="7577f-244">Rozhraní příkazového řádku ML.NET automaticky trénování příkaz referenční příručka</span><span class="sxs-lookup"><span data-stu-id="7577f-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="7577f-245">Postup instalace nástroje ML.NET rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="7577f-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="7577f-246">Telemetrie v rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="7577f-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="7577f-247">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7577f-247">Next steps</span></span>

<span data-ttu-id="7577f-248">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="7577f-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7577f-249">Příprava dat pro vybraný úkol ML (problém vyřešit)</span><span class="sxs-lookup"><span data-stu-id="7577f-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> * <span data-ttu-id="7577f-250">Spusťte příkaz "mlnet automaticky – train" v nástroji příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7577f-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> * <span data-ttu-id="7577f-251">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="7577f-251">Review the quality metric results</span></span>
> * <span data-ttu-id="7577f-252">Vysvětlení generované C# kód spustit model (kód pro použití v aplikaci pro koncové uživatele)</span><span class="sxs-lookup"><span data-stu-id="7577f-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> * <span data-ttu-id="7577f-253">Prozkoumejte generované C# kód, který byl použit pro trénování modelu "co nejlepší kvalitu" (výukové účely)</span><span class="sxs-lookup"><span data-stu-id="7577f-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7577f-254">Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="7577f-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
