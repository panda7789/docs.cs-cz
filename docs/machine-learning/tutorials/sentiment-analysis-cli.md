---
title: Analýza mínění pomocí rozhraní příkazového řádku ML.NET
description: Automaticky generovat model ML a související kód v jazyce C# z ukázkové datové sady
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: aab59463daad30748277602b9ab1d8ca2f3fa1f5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767673"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="009bb-103">Analýza mínění pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="009bb-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="009bb-104">Naučte se používat rozhraní příkazového řádku ML.NET k automatickému generování modelu ML.NET a základního kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="009bb-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="009bb-105">Zadáte datovou sadu a úlohu strojového učení, kterou chcete implementovat, a rozhraní příkazového řádku používá modul AutoML k vytvoření generování modelu a zdrojového kódu nasazení a také klasifikační model.</span><span class="sxs-lookup"><span data-stu-id="009bb-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the classification model.</span></span>

<span data-ttu-id="009bb-106">V tomto kurzu provedete následující kroky:</span><span class="sxs-lookup"><span data-stu-id="009bb-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="009bb-107">Příprava dat pro vybraný úkol strojového učení</span><span class="sxs-lookup"><span data-stu-id="009bb-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="009bb-108">Spuštění příkazu "mlnet Classification" z rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="009bb-108">Run the 'mlnet classification' command from the CLI</span></span>
> - <span data-ttu-id="009bb-109">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="009bb-109">Review the quality metric results</span></span>
> - <span data-ttu-id="009bb-110">Pochopení generovaného kódu jazyka C# pro použití modelu ve vaší aplikaci</span><span class="sxs-lookup"><span data-stu-id="009bb-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="009bb-111">Prozkoumat generovaný kód C#, který se použil ke výukě modelu</span><span class="sxs-lookup"><span data-stu-id="009bb-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="009bb-112">Toto téma odkazuje na nástroj CLI ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="009bb-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="009bb-113">Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="009bb-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="009bb-114">ML.NET CLI je součástí ML.NET a jeho hlavním cílem je "Demokratizujte" ML.NET pro vývojáře na platformě .NET při učení ML.NET, takže nemusíte vytvářet kód od začátku, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="009bb-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="009bb-115">ML.NET CLI můžete spustit na jakémkoli příkazovém řádku (Windows, Mac nebo Linux) a vygenerovat dobré kvality ML.NET modely a zdrojový kód na základě školení datových sad, které poskytnete.</span><span class="sxs-lookup"><span data-stu-id="009bb-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="009bb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="009bb-116">Pre-requisites</span></span>

- <span data-ttu-id="009bb-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) nebo novější</span><span class="sxs-lookup"><span data-stu-id="009bb-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) or later</span></span>
- <span data-ttu-id="009bb-118">Volitelné [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="009bb-118">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="009bb-119">Rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="009bb-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="009bb-120">Můžete buď spustit vygenerované projekty kódu C# ze sady Visual Studio nebo pomocí `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="009bb-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="009bb-121">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="009bb-121">Prepare your data</span></span>

<span data-ttu-id="009bb-122">Použijeme existující datovou sadu, která se používá pro scénář Analýza mínění, což je úloha strojového učení s binární klasifikací.</span><span class="sxs-lookup"><span data-stu-id="009bb-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="009bb-123">Můžete použít vlastní datovou sadu podobným způsobem a model a kód budou vygenerovány za vás.</span><span class="sxs-lookup"><span data-stu-id="009bb-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="009bb-124">Stáhněte [soubor zip datové sady mínění s popiskem "UCI" (viz citace v následující poznámce)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho do libovolné složky, kterou zvolíte.</span><span class="sxs-lookup"><span data-stu-id="009bb-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="009bb-125">Tento kurz používá datovou sadu ze skupiny "od" až po jednotlivé štítky pomocí hlubokých funkcí, Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="009bb-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="009bb-126">KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="009bb-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="009bb-127">UCI Machine Learning úložiště [ http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="009bb-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="009bb-128">Irvine, CA: University of California, školní informace a počítačové vědy.</span><span class="sxs-lookup"><span data-stu-id="009bb-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="009bb-129">Zkopírujte `yelp_labelled.txt` soubor do složky, kterou jste dříve vytvořili (například `/cli-test` ).</span><span class="sxs-lookup"><span data-stu-id="009bb-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="009bb-130">Otevřete preferovaný příkazový řádek a přejděte do složky, do které jste zkopírovali soubor DataSet.</span><span class="sxs-lookup"><span data-stu-id="009bb-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="009bb-131">Například:</span><span class="sxs-lookup"><span data-stu-id="009bb-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="009bb-132">Pomocí libovolného textového editoru, jako je Visual Studio Code, můžete otevřít a prozkoumat `yelp_labelled.txt` soubor DataSet.</span><span class="sxs-lookup"><span data-stu-id="009bb-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="009bb-133">Můžete vidět, že struktura je:</span><span class="sxs-lookup"><span data-stu-id="009bb-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="009bb-134">Soubor nemá žádnou hlavičku.</span><span class="sxs-lookup"><span data-stu-id="009bb-134">The file has no header.</span></span> <span data-ttu-id="009bb-135">Budete používat index sloupce.</span><span class="sxs-lookup"><span data-stu-id="009bb-135">You will use the column's index.</span></span>

    - <span data-ttu-id="009bb-136">K dispozici jsou pouze dva sloupce:</span><span class="sxs-lookup"><span data-stu-id="009bb-136">There are just two columns:</span></span>

        | <span data-ttu-id="009bb-137">Text (index sloupce 0)</span><span class="sxs-lookup"><span data-stu-id="009bb-137">Text (Column index 0)</span></span> | <span data-ttu-id="009bb-138">Popisek (index sloupce 1)</span><span class="sxs-lookup"><span data-stu-id="009bb-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="009bb-139">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="009bb-139">Wow... Loved this place.</span></span> | <span data-ttu-id="009bb-140">1</span><span class="sxs-lookup"><span data-stu-id="009bb-140">1</span></span> |
        | <span data-ttu-id="009bb-141">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="009bb-141">Crust is not good.</span></span> | <span data-ttu-id="009bb-142">0</span><span class="sxs-lookup"><span data-stu-id="009bb-142">0</span></span> |
        | <span data-ttu-id="009bb-143">Není Tasty a textura byla pouze nepříjemný.</span><span class="sxs-lookup"><span data-stu-id="009bb-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="009bb-144">0</span><span class="sxs-lookup"><span data-stu-id="009bb-144">0</span></span> |
        | <span data-ttu-id="009bb-145">... MNOHO DALŠÍCH TEXTOVÝCH ŘÁDKŮ...</span><span class="sxs-lookup"><span data-stu-id="009bb-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="009bb-146">... (1 nebo 0)...</span><span class="sxs-lookup"><span data-stu-id="009bb-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="009bb-147">Ujistěte se, že jste zavřeli soubor datové sady z editoru.</span><span class="sxs-lookup"><span data-stu-id="009bb-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="009bb-148">Nyní jste připraveni začít používat rozhraní příkazového řádku pro tento scénář Analýza mínění.</span><span class="sxs-lookup"><span data-stu-id="009bb-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="009bb-149">Po dokončení tohoto kurzu můžete také vyzkoušet vlastní datové sady, pokud jsou připravené k použití pro všechny úlohy ML aktuálně podporované ve verzi ML.NET CLI Preview, které jsou *binární klasifikace, klasifikace, regrese* a *doporučení*.</span><span class="sxs-lookup"><span data-stu-id="009bb-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Classification', 'Regression',* and *'Recommendation'*.</span></span>

## <a name="run-the-mlnet-classification-command"></a><span data-ttu-id="009bb-150">Spuštění příkazu "mlnet Classification"</span><span class="sxs-lookup"><span data-stu-id="009bb-150">Run the 'mlnet classification' command</span></span>

1. <span data-ttu-id="009bb-151">Spusťte následující příkaz ML.NET CLI:</span><span class="sxs-lookup"><span data-stu-id="009bb-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    <span data-ttu-id="009bb-152">Tento příkaz spustí \*\* `mlnet classification` příkaz\*\*:</span><span class="sxs-lookup"><span data-stu-id="009bb-152">This command runs the **`mlnet classification` command**:</span></span>
    - <span data-ttu-id="009bb-153">pro **úlohu klasifikace ml** *klasifikace*</span><span class="sxs-lookup"><span data-stu-id="009bb-153">for the **ML task** of *classification*</span></span>
    - <span data-ttu-id="009bb-154">používá **soubor `yelp_labelled.txt` DataSet** jako školicí a testovací datovou sadu (interně rozhraní příkazového řádku použije křížové ověření nebo ho rozdělí ve dvou datových sadách, jeden pro školení a jeden pro testování).</span><span class="sxs-lookup"><span data-stu-id="009bb-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="009bb-155">kde **sloupec cíl/cíl** , který chcete odhadnout (obvykle se nazývá **"label"**), je **sloupec s indexem 1** (to je druhý sloupec, protože index je založený na nule).</span><span class="sxs-lookup"><span data-stu-id="009bb-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="009bb-156">**nepoužívá záhlaví souboru** s názvy sloupců, protože tento konkrétní soubor DataSet nemá hlavičku.</span><span class="sxs-lookup"><span data-stu-id="009bb-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="009bb-157">**Cílová doba průzkumu a výuky** pro experiment je **10 sekund** .</span><span class="sxs-lookup"><span data-stu-id="009bb-157">the **targeted exploration/train time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="009bb-158">Zobrazí se výstup z rozhraní příkazového řádku, podobně jako:</span><span class="sxs-lookup"><span data-stu-id="009bb-158">You will see output from the CLI, similar to:</span></span>

    ![Klasifikace rozhraní příkazového řádku ML.NET v prostředí PowerShell](./media/mlnet-cli/mlnet-classification-powershell.gif)

    <span data-ttu-id="009bb-160">V tomto konkrétním případě, během 10 sekund a s malou datovou sadou, mohl nástroj rozhraní příkazového řádku spustit poměrně několik iterací, což znamená, že se bude na základě různých kombinací algoritmů a konfigurací s různými interními transformacemi dat a možnostmi Hyper-v algoritmu použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="009bb-160">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="009bb-161">Nakonec model "nejlepší kvality" nalezený za 10 sekund představuje model používající konkrétní Trainer nebo algoritmus s jakoukoli konkrétní konfigurací.</span><span class="sxs-lookup"><span data-stu-id="009bb-161">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="009bb-162">V závislosti na době průzkumu může příkaz vytvořit jiný výsledek.</span><span class="sxs-lookup"><span data-stu-id="009bb-162">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="009bb-163">Výběr je založen na několika zobrazených metrikách, například `Accuracy` .</span><span class="sxs-lookup"><span data-stu-id="009bb-163">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="009bb-164">**Princip metrik kvality modelu**</span><span class="sxs-lookup"><span data-stu-id="009bb-164">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="009bb-165">První a nejjednodušší metrika pro vyhodnocení modelu binární klasifikace je přesnost, která je snadno srozumitelná.</span><span class="sxs-lookup"><span data-stu-id="009bb-165">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="009bb-166">"Přesnost je poměrem správných předpovědi se sadou testovacích dat.".</span><span class="sxs-lookup"><span data-stu-id="009bb-166">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="009bb-167">Lépe až 100% (1,00), tím lépe.</span><span class="sxs-lookup"><span data-stu-id="009bb-167">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="009bb-168">Nicméně existují případy, kdy měření se metrikou přesnosti není dostatečné, zejména v případě, že je popisek (0 a 1 v tomto případě) v testovací datové sadě nevyvážený.</span><span class="sxs-lookup"><span data-stu-id="009bb-168">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="009bb-169">Další metriky a **podrobnější informace o metrikách** , jako je přesnost, AUC, AUCPR a F1 – skóre, které slouží k vyhodnocení různých modelů, najdete v tématu [Principy metrik ml.NET](../resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="009bb-169">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="009bb-170">Můžete vyzkoušet tuto velmi stejnou datovou sadu a zadat několik minut `--max-exploration-time` (například tři minuty, takže zadáte 180 sekund), což vám pro tuto datovou sadu vyhledá lepší "nejlepší model", a to s jinou konfigurací školicího kanálu (což je poměrně malé, 1000 řádků).</span><span class="sxs-lookup"><span data-stu-id="009bb-170">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="009bb-171">Aby bylo možné najít model "nejlepší/dobrý kvalita", který je "modelem připraveným pro produkční prostředí", který cílí na větší datové sady, měli byste experimenty s rozhraním příkazového řádku obvykle určit mnohem více času průzkumu v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="009bb-171">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="009bb-172">V mnoha případech se může stát, že budete potřebovat více hodin doby průzkumu, zejména pokud je datová sada velká na řádcích a sloupcích.</span><span class="sxs-lookup"><span data-stu-id="009bb-172">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="009bb-173">Předchozí spuštění příkazu vygenerovalo následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="009bb-173">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="009bb-174">Serializovaný model. zip ("nejlepší model") je připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="009bb-174">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="009bb-175">Kód jazyka C# ke spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).</span><span class="sxs-lookup"><span data-stu-id="009bb-175">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="009bb-176">Kód školení C# používaný k vygenerování tohoto modelu (Learning).</span><span class="sxs-lookup"><span data-stu-id="009bb-176">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="009bb-177">Soubor protokolu se všemi iteracemi, které se prozkoumaly s konkrétními podrobnějšími informacemi o každém algoritmu, se snaží s jeho kombinací Hyper-Parameters a transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="009bb-177">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="009bb-178">První dva prostředky (. Model souborů ZIP a kód C# ke spuštění tohoto modelu) je možné přímo použít v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.), aby se předpovědi s tímto generovaným modelem ML.</span><span class="sxs-lookup"><span data-stu-id="009bb-178">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="009bb-179">Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat, jaké konkrétní Trainer/algoritmus a Hyper-Parameters byly vybrány rozhraním příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="009bb-179">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="009bb-180">Tyto vyčíslované prostředky jsou vysvětleny v následujících krocích kurzu.</span><span class="sxs-lookup"><span data-stu-id="009bb-180">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="009bb-181">Prozkoumejte generovaný kód C#, který se použije ke spuštění modelu pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="009bb-181">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="009bb-182">V sadě Visual Studio (2017 nebo 2019) otevřete řešení vygenerované ve složce s názvem v `SampleClassification` původní cílové složce (v tomto kurzu se jmenovalo `/cli-test` ).</span><span class="sxs-lookup"><span data-stu-id="009bb-182">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="009bb-183">Mělo by se zobrazit podobné řešení:</span><span class="sxs-lookup"><span data-stu-id="009bb-183">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="009bb-184">V tomto kurzu doporučujeme používat Visual Studio, ale můžete také prozkoumat generovaný kód C# (dva projekty) pomocí libovolného textového editoru a spustit aplikaci generovanou konzolou s použitím `dotnet CLI` počítače s MacOS, Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="009bb-184">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Řešení VS vygenerované rozhraním CLI](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - <span data-ttu-id="009bb-186">Vygenerovaná **Knihovna tříd** obsahující serializovaný model ml (soubor. zip) a datové třídy (datové modely) je něco, co můžete přímo použít v aplikaci koncového uživatele, a to i přímo odkazování na tuto knihovnu tříd (nebo přesunutí kódu, jak dáváte přednost).</span><span class="sxs-lookup"><span data-stu-id="009bb-186">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="009bb-187">Vygenerovaná **aplikace konzoly** obsahuje kód spuštění, který je nutné zkontrolovat, a pak obvykle znovu použijete "hodnoticí kód" (kód, který SPUSTÍ model ml, aby předpovědi) přesunutím tohoto jednoduchého kódu (pouze pár řádků) do aplikace koncového uživatele, kde chcete vytvořit předpovědi.</span><span class="sxs-lookup"><span data-stu-id="009bb-187">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="009bb-188">V projektu knihovny tříd otevřete soubory třídy **ModelInput.cs** a **ModelOutput.cs** .</span><span class="sxs-lookup"><span data-stu-id="009bb-188">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="009bb-189">Uvidíte, že tyto třídy jsou "datové třídy" nebo třídy POCO používané k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="009bb-189">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="009bb-190">Je to "často používaný kód", ale užitečný pro jeho vygenerování, pokud má vaše datová sada desítky nebo dokonce stovky sloupců.</span><span class="sxs-lookup"><span data-stu-id="009bb-190">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="009bb-191">`ModelInput`Třída se používá při čtení dat z datové sady.</span><span class="sxs-lookup"><span data-stu-id="009bb-191">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="009bb-192">`ModelOutput`Třída slouží k získání výsledku předpovědi (data předpovědi).</span><span class="sxs-lookup"><span data-stu-id="009bb-192">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="009bb-193">Otevřete soubor Program.cs a prozkoumejte kód.</span><span class="sxs-lookup"><span data-stu-id="009bb-193">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="009bb-194">V několika řádcích je možné spustit model a vytvořit ukázku předpovědi.</span><span class="sxs-lookup"><span data-stu-id="009bb-194">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - První řádky kódu vytvářejí *Jednoduchá ukázková data*, v tomto případě na základě prvního řádku datové sady, která se má použít pro předpověď. <span data-ttu-id="009bb-196">Můžete také vytvořit vlastní "pevně zakódované" data aktualizací kódu:</span><span class="sxs-lookup"><span data-stu-id="009bb-196">You can also create you own 'hard-coded' data by updating the code:</span></span>

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - <span data-ttu-id="009bb-197">Další řádek kódu používá `ConsumeModel.Predict()` metodu pro zadaná vstupní data k vytvoření předpovědi a vrácení výsledků (na základě schématu ModelOutput.cs).</span><span class="sxs-lookup"><span data-stu-id="009bb-197">The next line of code uses the `ConsumeModel.Predict()` method on the specified input data to make a prediction and return the results (based on the ModelOutput.cs schema).</span></span>
    - <span data-ttu-id="009bb-198">Poslední řádky kódu tisknou vlastnosti vzorových dat (v tomto případě komentář) a také předpověď mínění a odpovídající skóre pro kladné mínění (1) a záporné mínění (2).</span><span class="sxs-lookup"><span data-stu-id="009bb-198">The last lines of code print out the proprties of the sample data (in this case the Comment) as well as the Sentiment prediction and corresponding Scores for positive sentiment (1) and negative sentiment (2).</span></span>

1. <span data-ttu-id="009bb-199">Spusťte projekt, a to buď pomocí původních ukázkových dat načtených z prvního řádku datové sady, nebo poskytnutím vlastních pevně zakódovaných ukázkových dat.</span><span class="sxs-lookup"><span data-stu-id="009bb-199">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="009bb-200">Měli byste dosáhnout předpovědi srovnatelné s:</span><span class="sxs-lookup"><span data-stu-id="009bb-200">You should get a prediction comparable to:</span></span>

![ML.NET CLI spustí aplikaci ze sady Visual Studio.](./media/mlnet-cli/mlnet-cli-console-app.png)<span data-ttu-id="009bb-202">)</span><span class="sxs-lookup"><span data-stu-id="009bb-202">)</span></span>

1. <span data-ttu-id="009bb-203">Zkuste změnit pevně kódovaná ukázková data na jiné věty s různými mínění a podívejte se, jak model předpovídá kladné nebo záporné mínění.</span><span class="sxs-lookup"><span data-stu-id="009bb-203">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="009bb-204">Inpředpovědiování aplikací pro koncové uživatele pomocí ML modelu ML</span><span class="sxs-lookup"><span data-stu-id="009bb-204">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="009bb-205">Podobný kód pro vyhodnocování modelu ML můžete použít ke spuštění modelu v aplikaci koncového uživatele a k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="009bb-205">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="009bb-206">Tento kód můžete například přímo přesunout do libovolné aplikace klasické pracovní plochy systému Windows, jako je například **WPF** a **WinForms** , a model spustit stejným způsobem, než byl proveden v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="009bb-206">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="009bb-207">Způsob, jakým implementujete tyto řádky kódu ke spuštění modelu ML, by se měl optimalizovat (to znamená ukládat do mezipaměti soubor. zip modelu a načíst ho jednou) a mít objekty singleton místo jejich vytváření na všech žádostech, zejména v případě, že vaše aplikace musí být škálovatelná, jako je webová aplikace nebo distribuovaná služba, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="009bb-207">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="009bb-208">Spouštění modelů ML.NET v škálovatelných ASP.NET Core webových aplikacích a službách (vícevláknové aplikace)</span><span class="sxs-lookup"><span data-stu-id="009bb-208">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="009bb-209">Vytvoření objektu modelu ( `ITransformer` načteného ze souboru. zip modelu) a `PredictionEngine` objektu by mělo být optimalizované hlavně při spuštění na škálovatelných webových aplikacích a distribuovaných službách.</span><span class="sxs-lookup"><span data-stu-id="009bb-209">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="009bb-210">V první případě je objekt modelu ( `ITransformer` ) optimalizace jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="009bb-210">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="009bb-211">Vzhledem k `ITransformer` tomu, že je objekt bezpečný pro přístup z více vláken, můžete objekt uložit do mezipaměti jako typ singleton nebo static, abyste model načetli pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="009bb-211">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="009bb-212">U druhého objektu `PredictionEngine` objekt není tak snadné, protože objekt není bezpečný pro přístup z `PredictionEngine` více vláken, proto nemůžete vytvořit instanci tohoto objektu jako typ singleton nebo statický objekt v aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="009bb-212">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="009bb-213">Tento problémový příspěvek k vláknům a škálovatelnosti je v tomto [blogovém příspěvku](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)podrobněji popsán.</span><span class="sxs-lookup"><span data-stu-id="009bb-213">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="009bb-214">Věcí vám ale bylo mnohem jednodušší, než je vysvětleno v tomto blogovém příspěvku.</span><span class="sxs-lookup"><span data-stu-id="009bb-214">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="009bb-215">Pracovali jsme na jednodušším přístupu a vytvořili jste dobrý **balíček integrace .NET Core** , který můžete snadno použít ve svých ASP.NET Corech aplikacích a službách, a to tak, že ho zaregistrujete ve službě Application di Services (služba pro vkládání závislostí) a pak ho přímo použijete z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="009bb-215">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="009bb-216">Podívejte se na následující kurz a příklad, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="009bb-216">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="009bb-217">Kurz: používání modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi</span><span class="sxs-lookup"><span data-stu-id="009bb-217">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="009bb-218">Ukázka: škálovatelný ML.NET model na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="009bb-218">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="009bb-219">Prozkoumejte vygenerovaný kód C#, který se použil ke vzdělávání modelu nejlepší kvality.</span><span class="sxs-lookup"><span data-stu-id="009bb-219">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="009bb-220">Pro pokročilejší účely učení můžete také prozkoumat generovaný kód C#, který byl použit nástrojem CLI k výuce vygenerovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="009bb-220">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="009bb-221">Tento kód školicího modelu je aktuálně vygenerován ve vlastní třídě generované s názvem, `ModelBuilder` abyste mohli prozkoumat tento školicí kód.</span><span class="sxs-lookup"><span data-stu-id="009bb-221">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="009bb-222">Důležitější je, že pro tento konkrétní scénář (Analýza mínění model) můžete také porovnat vygenerovaný školicí kód s kódem, který je vysvětlen v následujícím kurzu:</span><span class="sxs-lookup"><span data-stu-id="009bb-222">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="009bb-223">Porovnání: [kurz: použití ml.NET v binárním scénáři klasifikace mínění Analysis](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="009bb-223">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="009bb-224">Je zajímavá možnost porovnat zvolený algoritmus a konfiguraci kanálu v kurzu s kódem generovaným nástrojem CLI.</span><span class="sxs-lookup"><span data-stu-id="009bb-224">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="009bb-225">V závislosti na tom, kolik času strávíte iterací a hledáním lepších modelů, se zvolený algoritmus může lišit spolu s jeho konkrétními parametry Hyper-a a konfigurací kanálu.</span><span class="sxs-lookup"><span data-stu-id="009bb-225">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="009bb-226">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="009bb-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="009bb-227">Příprava dat pro vybraný úkol ML (problém, který se má vyřešit)</span><span class="sxs-lookup"><span data-stu-id="009bb-227">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="009bb-228">Spuštění příkazu "mlnet Classification" v nástroji CLI</span><span class="sxs-lookup"><span data-stu-id="009bb-228">Run the 'mlnet classification' command in the CLI tool</span></span>
> - <span data-ttu-id="009bb-229">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="009bb-229">Review the quality metric results</span></span>
> - <span data-ttu-id="009bb-230">Pochopení generovaného kódu C# ke spuštění modelu (kód pro použití v aplikaci koncového uživatele)</span><span class="sxs-lookup"><span data-stu-id="009bb-230">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="009bb-231">Prozkoumejte vygenerovaný kód C#, který se použil ke vzdělávání modelu nejlepší kvality (k tomuto využití).</span><span class="sxs-lookup"><span data-stu-id="009bb-231">Explore the generated C# code that was used to train the "best quality" model (earning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="009bb-232">Viz také</span><span class="sxs-lookup"><span data-stu-id="009bb-232">See also</span></span>

- [<span data-ttu-id="009bb-233">Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="009bb-233">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="009bb-234">Kurz: používání modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi</span><span class="sxs-lookup"><span data-stu-id="009bb-234">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="009bb-235">Ukázka: škálovatelný ML.NET model na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="009bb-235">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="009bb-236">Referenční příručka k příkazu ML.NET CLI pro automatické učení</span><span class="sxs-lookup"><span data-stu-id="009bb-236">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="009bb-237">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="009bb-237">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
