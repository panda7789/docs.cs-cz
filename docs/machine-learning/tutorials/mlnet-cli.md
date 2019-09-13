---
title: Analýza mínění pomocí rozhraní příkazového řádku ML.NET
description: Automatické generování modelu ML a souvisejícího C# kódu z ukázkové datové sady
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: f3688b4492d3eb629f86a9d463b9127429260033
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929111"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="cc27f-103">Analýza mínění pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="cc27f-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="cc27f-104">Naučte se používat rozhraní příkazového řádku ML.NET k automatickému generování modelu C# ml.NET a základního kódu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="cc27f-105">Zadáte datovou sadu a úlohu strojového učení, kterou chcete implementovat, a rozhraní příkazového řádku používá modul AutoML k vytvoření generování modelu a zdrojového kódu nasazení a také binárního modelu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="cc27f-106">V tomto kurzu provedete následující kroky:</span><span class="sxs-lookup"><span data-stu-id="cc27f-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cc27f-107">Příprava dat pro vybraný úkol strojového učení</span><span class="sxs-lookup"><span data-stu-id="cc27f-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="cc27f-108">Spuštění příkazu ' mlnet auto-vlak ' z rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="cc27f-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> - <span data-ttu-id="cc27f-109">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="cc27f-109">Review the quality metric results</span></span>
> - <span data-ttu-id="cc27f-110">Pochopení vygenerovaného C# kódu pro použití modelu ve vaší aplikaci</span><span class="sxs-lookup"><span data-stu-id="cc27f-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="cc27f-111">Prozkoumejte vygenerovaný C# kód, který se použil pro výuku modelu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="cc27f-112">Toto téma odkazuje na nástroj CLI ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="cc27f-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="cc27f-113">Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="cc27f-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="cc27f-114">ML.NET CLI je součástí ML.NET a jeho hlavním cílem je "Demokratizujte" ML.NET pro vývojáře na platformě .NET při učení ML.NET, takže nemusíte vytvářet kód od začátku, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="cc27f-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="cc27f-115">ML.NET CLI můžete spustit na jakémkoli příkazovém řádku (Windows, Mac nebo Linux) a vygenerovat dobré kvality ML.NET modely a zdrojový kód na základě školení datových sad, které poskytnete.</span><span class="sxs-lookup"><span data-stu-id="cc27f-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="cc27f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc27f-116">Pre-requisites</span></span>

- <span data-ttu-id="cc27f-117">[.NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo novější</span><span class="sxs-lookup"><span data-stu-id="cc27f-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="cc27f-118">Volitelné [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="cc27f-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="cc27f-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="cc27f-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="cc27f-120">Můžete buď spustit vygenerované C# projekty kódu ze sady Visual Studio nebo pomocí `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="cc27f-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="cc27f-121">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="cc27f-121">Prepare your data</span></span>

<span data-ttu-id="cc27f-122">Použijeme existující datovou sadu, která se používá pro scénář Analýza mínění, což je úloha strojového učení s binární klasifikací.</span><span class="sxs-lookup"><span data-stu-id="cc27f-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="cc27f-123">Můžete použít vlastní datovou sadu podobným způsobem a model a kód budou vygenerovány za vás.</span><span class="sxs-lookup"><span data-stu-id="cc27f-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="cc27f-124">Stáhněte [soubor zip datové sady mínění s popiskem "UCI" (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho do libovolné složky, kterou zvolíte.</span><span class="sxs-lookup"><span data-stu-id="cc27f-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc27f-125">Tento kurz používá datovou sadu ze skupiny "od" až po jednotlivé štítky pomocí hlubokých funkcí, Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="cc27f-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="cc27f-126">KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="cc27f-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="cc27f-127">UCI Machine Learning úložiště [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="cc27f-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="cc27f-128">Irvine, certifikační autorita: University of California, školní informace a počítačové vědy.</span><span class="sxs-lookup"><span data-stu-id="cc27f-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="cc27f-129">Zkopírujte soubor do složky, kterou jste dříve vytvořili ( `/cli-test`například). `yelp_labelled.txt`</span><span class="sxs-lookup"><span data-stu-id="cc27f-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="cc27f-130">Otevřete preferovaný příkazový řádek a přejděte do složky, do které jste zkopírovali soubor DataSet.</span><span class="sxs-lookup"><span data-stu-id="cc27f-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="cc27f-131">Příklad:</span><span class="sxs-lookup"><span data-stu-id="cc27f-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="cc27f-132">Pomocí libovolného textového editoru, jako je Visual Studio Code, můžete otevřít a prozkoumat `yelp_labelled.txt` soubor DataSet.</span><span class="sxs-lookup"><span data-stu-id="cc27f-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="cc27f-133">Můžete vidět, že struktura je:</span><span class="sxs-lookup"><span data-stu-id="cc27f-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="cc27f-134">Soubor nemá žádnou hlavičku.</span><span class="sxs-lookup"><span data-stu-id="cc27f-134">The file has no header.</span></span> <span data-ttu-id="cc27f-135">Budete používat index sloupce.</span><span class="sxs-lookup"><span data-stu-id="cc27f-135">You will use the column's index.</span></span>

    - <span data-ttu-id="cc27f-136">K dispozici jsou pouze dva sloupce:</span><span class="sxs-lookup"><span data-stu-id="cc27f-136">There are just two columns:</span></span>

        | <span data-ttu-id="cc27f-137">Text (index sloupce 0)</span><span class="sxs-lookup"><span data-stu-id="cc27f-137">Text (Column index 0)</span></span> | <span data-ttu-id="cc27f-138">Popisek (index sloupce 1)</span><span class="sxs-lookup"><span data-stu-id="cc27f-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="cc27f-139">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="cc27f-139">Wow... Loved this place.</span></span> | <span data-ttu-id="cc27f-140">1</span><span class="sxs-lookup"><span data-stu-id="cc27f-140">1</span></span> |
        | <span data-ttu-id="cc27f-141">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="cc27f-141">Crust is not good.</span></span> | <span data-ttu-id="cc27f-142">0</span><span class="sxs-lookup"><span data-stu-id="cc27f-142">0</span></span> |
        | <span data-ttu-id="cc27f-143">Není Tasty a textura byla pouze nepříjemný.</span><span class="sxs-lookup"><span data-stu-id="cc27f-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="cc27f-144">0</span><span class="sxs-lookup"><span data-stu-id="cc27f-144">0</span></span> |
        | <span data-ttu-id="cc27f-145">... MNOHO DALŠÍCH TEXTOVÝCH ŘÁDKŮ...</span><span class="sxs-lookup"><span data-stu-id="cc27f-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="cc27f-146">... (1 nebo 0)...</span><span class="sxs-lookup"><span data-stu-id="cc27f-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="cc27f-147">Ujistěte se, že jste zavřeli soubor datové sady z editoru.</span><span class="sxs-lookup"><span data-stu-id="cc27f-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="cc27f-148">Nyní jste připraveni začít používat rozhraní příkazového řádku pro tento scénář Analýza mínění.</span><span class="sxs-lookup"><span data-stu-id="cc27f-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc27f-149">Po dokončení tohoto kurzu můžete také vyzkoušet vlastní datové sady, pokud jsou připravené k použití pro všechny úlohy ML aktuálně podporované ve verzi ML.NET CLI Preview, které jsou *binární klasifikace, klasifikace s více třídami a regrese.* ).</span><span class="sxs-lookup"><span data-stu-id="cc27f-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="cc27f-150">Spuštění příkazu ' mlnet auto-vlak '</span><span class="sxs-lookup"><span data-stu-id="cc27f-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="cc27f-151">Spusťte následující příkaz ML.NET CLI:</span><span class="sxs-lookup"><span data-stu-id="cc27f-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="cc27f-152">Tento příkaz spustí  **`mlnet auto-train` příkaz**:</span><span class="sxs-lookup"><span data-stu-id="cc27f-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="cc27f-153">pro **úlohu typu ml** **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="cc27f-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="cc27f-154">používá **soubor `yelp_labelled.txt` DataSet** jako školicí a testovací datovou sadu (interně rozhraní příkazového řádku použije křížové ověření nebo ho rozdělí ve dvou datových sadách, jeden pro školení a jeden pro testování).</span><span class="sxs-lookup"><span data-stu-id="cc27f-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="cc27f-155">kde **sloupec cíl/cíl** , který chcete odhadnout (obvykle se nazývá **"label"** ), je **sloupec s indexem 1** (to je druhý sloupec, protože index je založený na nule).</span><span class="sxs-lookup"><span data-stu-id="cc27f-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="cc27f-156">**nepoužívá záhlaví souboru** s názvy sloupců, protože tento konkrétní soubor DataSet nemá hlavičku.</span><span class="sxs-lookup"><span data-stu-id="cc27f-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="cc27f-157">**cílený čas průzkumu** experimentu je **10 sekund** .</span><span class="sxs-lookup"><span data-stu-id="cc27f-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="cc27f-158">Zobrazí se výstup z rozhraní příkazového řádku, podobně jako:</span><span class="sxs-lookup"><span data-stu-id="cc27f-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="cc27f-159">Windows</span><span class="sxs-lookup"><span data-stu-id="cc27f-159">Windows</span></span>](#tab/windows)

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="cc27f-161">macOS bash</span><span class="sxs-lookup"><span data-stu-id="cc27f-161">macOS Bash</span></span>](#tab/macosbash)

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="cc27f-163">V tomto konkrétním případě, během pouhých 10 sekund a s malou datovou sadou, mohl nástroj rozhraní příkazového řádku spustit poměrně několik iterací, což znamená, že se bude na základě různých kombinací algoritmů a konfigurací s různými interními daty podařit školení několikrát. transformace a Hyper-parametry algoritmu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="cc27f-164">Nakonec model "nejlepší kvality" nalezený za 10 sekund představuje model používající konkrétní Trainer nebo algoritmus s jakoukoli konkrétní konfigurací.</span><span class="sxs-lookup"><span data-stu-id="cc27f-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="cc27f-165">V závislosti na době průzkumu může příkaz vytvořit jiný výsledek.</span><span class="sxs-lookup"><span data-stu-id="cc27f-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="cc27f-166">Výběr je založen na několika zobrazených metrikách, například `Accuracy`.</span><span class="sxs-lookup"><span data-stu-id="cc27f-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="cc27f-167">**Princip metrik kvality modelu**</span><span class="sxs-lookup"><span data-stu-id="cc27f-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="cc27f-168">První a nejjednodušší metrika pro vyhodnocení modelu binární klasifikace je přesnost, která je snadno srozumitelná.</span><span class="sxs-lookup"><span data-stu-id="cc27f-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="cc27f-169">"Přesnost je poměrem správných předpovědi se sadou testovacích dat.".</span><span class="sxs-lookup"><span data-stu-id="cc27f-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="cc27f-170">Lépe až 100% (1,00), tím lépe.</span><span class="sxs-lookup"><span data-stu-id="cc27f-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="cc27f-171">Nicméně existují případy, kdy měření se metrikou přesnosti není dostatečné, zejména v případě, že je popisek (0 a 1 v tomto případě) v testovací datové sadě nevyvážený.</span><span class="sxs-lookup"><span data-stu-id="cc27f-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="cc27f-172">Další metriky a **podrobnější informace o metrikách** , jako je přesnost, AUC, AUCPR, F1-skore využívané k vyhodnocení různých modelů, si můžete přečíst v tématu [Principy metrik ml.NET](../resources/metrics.md) .</span><span class="sxs-lookup"><span data-stu-id="cc27f-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc27f-173">Tuto velmi stejnou datovou sadu můžete vyzkoušet a zadat několik minut `--max-exploration-time` (např. 3 minuty, takže zadáte 180 sekund), což vám pro tuto datovou sadu vyhledá lepší "nejlepší model", a to s jinou konfigurací školicího kanálu (což je poměrně malé, 1000 řádky).</span><span class="sxs-lookup"><span data-stu-id="cc27f-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="cc27f-174">Aby bylo možné najít model "nejlepší/dobrý kvalita", který je "modelem připraveným pro produkční prostředí", který cílí na větší datové sady, měli byste experimenty s rozhraním příkazového řádku obvykle určit mnohem více času průzkumu v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="cc27f-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="cc27f-175">V mnoha případech se může stát, že budete potřebovat více hodin doby průzkumu, zejména pokud je datová sada velká na řádcích a sloupcích.</span><span class="sxs-lookup"><span data-stu-id="cc27f-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="cc27f-176">Předchozí spuštění příkazu vygenerovalo následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="cc27f-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="cc27f-177">Serializovaný model. zip ("nejlepší model") je připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="cc27f-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="cc27f-178">C#kód pro spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).</span><span class="sxs-lookup"><span data-stu-id="cc27f-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="cc27f-179">C#školicí kód používaný k vygenerování tohoto modelu (výukové účely)</span><span class="sxs-lookup"><span data-stu-id="cc27f-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="cc27f-180">Soubor protokolu se všemi iteracemi, které se prozkoumaly s konkrétními podrobnějšími informacemi o každém algoritmu, se snaží s jeho kombinací Hyper-Parameters a transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="cc27f-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="cc27f-181">První dva prostředky (. Model souboru ZIP a C# kód pro spuštění tohoto modelu) je možné přímo použít v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.), aby se předpovědi s tímto generovaným modelem ml.</span><span class="sxs-lookup"><span data-stu-id="cc27f-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="cc27f-182">Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat, jaké konkrétní Trainer/algoritmus a Hyper-Parameters byly vybrány rozhraním příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cc27f-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="cc27f-183">Tyto vyčíslované prostředky jsou vysvětleny v následujících krocích kurzu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="cc27f-184">Prozkoumejte generovaný C# kód, který se použije ke spuštění modelu pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="cc27f-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="cc27f-185">V sadě Visual Studio (2017 nebo 2019) otevřete řešení vygenerované ve složce s `SampleBinaryClassification` názvem v původní cílové složce (v tomto kurzu se jmenovalo `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="cc27f-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="cc27f-186">Mělo by se zobrazit podobné řešení:</span><span class="sxs-lookup"><span data-stu-id="cc27f-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc27f-187">V tomto kurzu doporučujeme používat Visual Studio, ale můžete také prozkoumat vygenerovaný C# kód (dva projekty) pomocí libovolného textového editoru a spustit vygenerovanou konzolovou aplikaci s použitím `dotnet CLI` počítače s MacOS, Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="cc27f-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Řešení VS vygenerované rozhraním CLI](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="cc27f-189">Vygenerovaná **Knihovna tříd** obsahující serializovaný model ml (soubor. zip) a datové třídy (datové modely) je něco, co můžete přímo použít v aplikaci koncového uživatele, a to i přímo odkazování na tuto knihovnu tříd (nebo přesunutí kódu, jak dáváte přednost ).</span><span class="sxs-lookup"><span data-stu-id="cc27f-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="cc27f-190">Vygenerovaná **aplikace konzoly** obsahuje kód spuštění, který je nutné zkontrolovat, a pak obvykle znovu použijete "kód bodování" (kód, který SPUSTÍ model ml, aby předpovědi) přesunutím tohoto jednoduchého kódu (pouze pár řádků) do aplikace koncového uživatele, kde chcete Nastavte předpovědi.</span><span class="sxs-lookup"><span data-stu-id="cc27f-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="cc27f-191">V projektu knihovny tříd otevřete soubory třídy **ModelInput.cs** a **ModelOutput.cs** .</span><span class="sxs-lookup"><span data-stu-id="cc27f-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="cc27f-192">Uvidíte, že tyto třídy jsou "datové třídy" nebo třídy POCO používané k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="cc27f-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="cc27f-193">Je to "často používaný kód", ale užitečný pro jeho vygenerování, pokud má vaše datová sada desítky nebo dokonce stovky sloupců.</span><span class="sxs-lookup"><span data-stu-id="cc27f-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="cc27f-194">`ModelInput` Třída se používá při čtení dat z datové sady.</span><span class="sxs-lookup"><span data-stu-id="cc27f-194">The `ModelInput` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="cc27f-195">`ModelOutput` Třída slouží k získání výsledku předpovědi (data předpovědi).</span><span class="sxs-lookup"><span data-stu-id="cc27f-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="cc27f-196">Otevřete soubor Program.cs a prozkoumejte kód.</span><span class="sxs-lookup"><span data-stu-id="cc27f-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="cc27f-197">V několika řádcích je možné spustit model a vytvořit ukázku předpovědi.</span><span class="sxs-lookup"><span data-stu-id="cc27f-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

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

- <span data-ttu-id="cc27f-198">První řádek kódu jednoduše vytvoří `MLContext` objekt potřebný při každém spuštění kódu ml.NET.</span><span class="sxs-lookup"><span data-stu-id="cc27f-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="cc27f-199">Druhý řádek kódu je komentovaný, protože model nepotřebujete vyškolit, protože už ho pro vás vyškole nástroj CLI a uložil se do serializovaného modelu. Soubor ZIP.</span><span class="sxs-lookup"><span data-stu-id="cc27f-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="cc27f-200">Pokud ale chcete vidět, *jak byl model vyškolený* rozhraním příkazového řádku, můžete tento řádek odkomentovat a spustit/ladit školicí kód, který se používá pro konkrétní model ml.</span><span class="sxs-lookup"><span data-stu-id="cc27f-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="cc27f-201">Ve třetím řádku kódu načtete model z serializovaného modelu. Soubor zip s `mlContext.Model.Load()` rozhraním API zadáním cesty k tomuto modelu. Soubor ZIP.</span><span class="sxs-lookup"><span data-stu-id="cc27f-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="cc27f-202">Ve čtvrtém řádku kódu, který načtete, `PredictionEngine` vytvořte objekt `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` s rozhraním API.</span><span class="sxs-lookup"><span data-stu-id="cc27f-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="cc27f-203">`PredictionEngine` Objekt budete potřebovat vždy, když chcete vytvořit předpověď, která cílí na jeden vzorek dat (v tomto případě jediný text, který předpovídáte jeho mínění).</span><span class="sxs-lookup"><span data-stu-id="cc27f-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="cc27f-204">Pátý řádek kódu je místo, kde vytvoříte tato *Jednoduchá ukázková data* , která se mají použít pro předpověď voláním funkce `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="cc27f-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="cc27f-205">Vzhledem k tomu, že nástroj rozhraní příkazového řádku neví, jaký druh dat použít, v rámci této funkce načítá první řádek datové sady.</span><span class="sxs-lookup"><span data-stu-id="cc27f-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="cc27f-206">Nicméně v tomto případě můžete také vytvořit vlastní "pevně kódovaná" data namísto aktuální implementace `CreateSingleDataSample()` funkce aktualizací tohoto jednoduššího kódu implementující tuto funkci:</span><span class="sxs-lookup"><span data-stu-id="cc27f-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="cc27f-207">Spusťte projekt, a to buď pomocí původních ukázkových dat načtených z prvního řádku datové sady, nebo poskytnutím vlastních pevně zakódovaných ukázkových dat.</span><span class="sxs-lookup"><span data-stu-id="cc27f-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="cc27f-208">Měli byste dosáhnout předpovědi srovnatelné s:</span><span class="sxs-lookup"><span data-stu-id="cc27f-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="cc27f-209">Windows</span><span class="sxs-lookup"><span data-stu-id="cc27f-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="cc27f-210">Spusťte konzolovou aplikaci ze sady Visual Studio tak, že kliknete na F5 (tlačítko Přehrát):</span><span class="sxs-lookup"><span data-stu-id="cc27f-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="cc27f-212">)</span><span class="sxs-lookup"><span data-stu-id="cc27f-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="cc27f-213">macOS bash</span><span class="sxs-lookup"><span data-stu-id="cc27f-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="cc27f-214">Spusťte konzolovou aplikaci z příkazového řádku zadáním následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="cc27f-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="cc27f-216">)</span><span class="sxs-lookup"><span data-stu-id="cc27f-216">)</span></span>

    ---

1. <span data-ttu-id="cc27f-217">Zkuste změnit pevně kódovaná ukázková data na jiné věty s různými mínění a podívejte se, jak model předpovídá kladné nebo záporné mínění.</span><span class="sxs-lookup"><span data-stu-id="cc27f-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="cc27f-218">Inpředpovědiování aplikací pro koncové uživatele pomocí ML modelu ML</span><span class="sxs-lookup"><span data-stu-id="cc27f-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="cc27f-219">Podobný kód pro vyhodnocování modelu ML můžete použít ke spuštění modelu v aplikaci koncového uživatele a k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="cc27f-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="cc27f-220">Tento kód můžete například přímo přesunout do libovolné aplikace klasické pracovní plochy systému Windows, jako je například **WPF** a **WinForms** , a model spustit stejným způsobem, než byl proveden v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cc27f-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="cc27f-221">Způsob, jakým implementujete tyto řádky kódu ke spuštění modelu ML, by se měl optimalizovat (to znamená, uložit soubor. zip modelu do mezipaměti a načíst ho jednou) a mít objekty singleton místo jejich vytváření na všech žádostech, zvlášť pokud vaše aplikace musí být škálovatelná, třeba Webová aplikace nebo distribuovaná služba, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="cc27f-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="cc27f-222">Spouštění modelů ML.NET v škálovatelných ASP.NET Core webových aplikacích a službách (vícevláknové aplikace)</span><span class="sxs-lookup"><span data-stu-id="cc27f-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="cc27f-223">Vytvoření objektu modelu (`ITransformer` načteného ze souboru. zip modelu) `PredictionEngine` a objektu by mělo být optimalizované hlavně při spuštění na škálovatelných webových aplikacích a distribuovaných službách.</span><span class="sxs-lookup"><span data-stu-id="cc27f-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="cc27f-224">V první případě je objekt modelu (`ITransformer`) optimalizace jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="cc27f-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="cc27f-225">Vzhledem k `ITransformer` tomu, že je objekt bezpečný pro přístup z více vláken, můžete objekt uložit do mezipaměti jako typ singleton nebo static, abyste model načetli pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="cc27f-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="cc27f-226">U druhého objektu `PredictionEngine` objekt není tak snadné, protože objekt není bezpečný pro přístup z `PredictionEngine` více vláken, proto nemůžete vytvořit instanci tohoto objektu jako typ singleton nebo statický objekt v aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc27f-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="cc27f-227">Tento problémový příspěvek k vláknům a škálovatelnosti je v tomto [blogovém příspěvku](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)podrobněji popsán.</span><span class="sxs-lookup"><span data-stu-id="cc27f-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="cc27f-228">Věcí vám ale bylo mnohem jednodušší, než je vysvětleno v tomto blogovém příspěvku.</span><span class="sxs-lookup"><span data-stu-id="cc27f-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="cc27f-229">Pracovali jsme na jednodušším přístupu a vytvořili jste dobrý **balíček integrace .NET Core** , který můžete snadno použít ve svých ASP.NET Corech aplikacích a službách, a to tak, že ho zaregistrujete ve službě Application di Services (služba pro vkládání závislostí) a pak přímo použijte ho z kódu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="cc27f-230">Podívejte se na následující kurz a příklad, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="cc27f-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="cc27f-231">Kurz: Spouštění modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi</span><span class="sxs-lookup"><span data-stu-id="cc27f-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="cc27f-232">Vzorku Škálovatelný ML.NET model na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="cc27f-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="cc27f-233">Prozkoumejte vygenerovaný C# kód, který se použil ke vzdělávání modelu "nejlepší kvality".</span><span class="sxs-lookup"><span data-stu-id="cc27f-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="cc27f-234">Pro pokročilejší účely učení můžete také prozkoumat generovaný C# kód, který byl použit nástrojem CLI k výuce vygenerovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="cc27f-235">Tento kód školicího modelu je aktuálně vygenerován ve vlastní třídě generované s názvem `ModelBuilder` , abyste mohli prozkoumat tento školicí kód.</span><span class="sxs-lookup"><span data-stu-id="cc27f-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="cc27f-236">Důležitější je, že pro tento konkrétní scénář (Analýza mínění model) můžete také porovnat vygenerovaný školicí kód s kódem, který je vysvětlen v následujícím kurzu:</span><span class="sxs-lookup"><span data-stu-id="cc27f-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="cc27f-237">Porovnán [Kurz: Použijte ML.NET v binárním scénáři](sentiment-analysis.md)klasifikace mínění Analysis.</span><span class="sxs-lookup"><span data-stu-id="cc27f-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="cc27f-238">Je zajímavá možnost porovnat zvolený algoritmus a konfiguraci kanálu v kurzu s kódem generovaným nástrojem CLI.</span><span class="sxs-lookup"><span data-stu-id="cc27f-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="cc27f-239">V závislosti na tom, kolik času strávíte iterací a hledáním lepších modelů, se zvolený algoritmus může lišit spolu s jeho konkrétními parametry Hyper-a a konfigurací kanálu.</span><span class="sxs-lookup"><span data-stu-id="cc27f-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc27f-240">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc27f-240">See also</span></span>

- [<span data-ttu-id="cc27f-241">Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="cc27f-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="cc27f-242">Kurz: Spouštění modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi</span><span class="sxs-lookup"><span data-stu-id="cc27f-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="cc27f-243">Vzorku Škálovatelný ML.NET model na ASP.NET Core WebAPI</span><span class="sxs-lookup"><span data-stu-id="cc27f-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="cc27f-244">Referenční příručka k příkazu ML.NET CLI pro automatické učení</span><span class="sxs-lookup"><span data-stu-id="cc27f-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="cc27f-245">Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)</span><span class="sxs-lookup"><span data-stu-id="cc27f-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="cc27f-246">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="cc27f-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="cc27f-247">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cc27f-247">Next steps</span></span>

<span data-ttu-id="cc27f-248">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="cc27f-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cc27f-249">Příprava dat pro vybraný úkol ML (problém, který se má vyřešit)</span><span class="sxs-lookup"><span data-stu-id="cc27f-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="cc27f-250">Spuštění příkazu ' mlnet auto-vlak ' v nástroji CLI</span><span class="sxs-lookup"><span data-stu-id="cc27f-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> - <span data-ttu-id="cc27f-251">Kontrola výsledků metrik kvality</span><span class="sxs-lookup"><span data-stu-id="cc27f-251">Review the quality metric results</span></span>
> - <span data-ttu-id="cc27f-252">Pochopení generovaného C# kódu pro spuštění modelu (kód pro použití v aplikaci koncového uživatele)</span><span class="sxs-lookup"><span data-stu-id="cc27f-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="cc27f-253">Prozkoumejte vygenerovaný C# kód, který se použil ke studiu "nejlepší kvality" modelu (vzdělávací účely).</span><span class="sxs-lookup"><span data-stu-id="cc27f-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc27f-254">Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="cc27f-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
