---
title: Použití ML.NET ve scénáři binární klasifikace analýzy mínění
description: Objevte, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí mínění předpovědi proveďte příslušnou akci.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7d2935fafe9dbad28205c8a896d97d80474a686f
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838820"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="334e4-103">Kurz: Použití ML.NET ve scénáři binární klasifikace analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="334e4-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="334e4-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="334e4-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="334e4-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="334e4-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="334e4-106">Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru mínění prostřednictvím aplikace konzoly .NET Core pomocí jazyka C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="334e4-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="334e4-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="334e4-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="334e4-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="334e4-108">Understand the problem</span></span>
> * <span data-ttu-id="334e4-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="334e4-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="334e4-110">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="334e4-110">Prepare your data</span></span>
> * <span data-ttu-id="334e4-111">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="334e4-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="334e4-112">Načíst třídění</span><span class="sxs-lookup"><span data-stu-id="334e4-112">Load a classifier</span></span>
> * <span data-ttu-id="334e4-113">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="334e4-113">Train the model</span></span>
> * <span data-ttu-id="334e4-114">Vyhodnocení modelu s jinou datovou sadu</span><span class="sxs-lookup"><span data-stu-id="334e4-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="334e4-115">Předpověď výsledků dat testu s modelem</span><span class="sxs-lookup"><span data-stu-id="334e4-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="334e4-116">Přehled ukázky analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="334e4-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="334e4-117">Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="334e4-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="334e4-118">Vyhodnocuje také model s druhou datové sady pro analýzy kvality.</span><span class="sxs-lookup"><span data-stu-id="334e4-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="334e4-119">Datové sady subjektivního hodnocení jsou z WikiDetox projektu.</span><span class="sxs-lookup"><span data-stu-id="334e4-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="334e4-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="334e4-120">Prerequisites</span></span>

* <span data-ttu-id="334e4-121">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="334e4-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="334e4-122">[Souboru (wikiPedia – detox – 250řádku data.tsv) s daty oddělenými tabulátory data řádku detox Wikipedia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="334e4-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="334e4-123">[Souboru (wikipedia – detox – 250řádku test.tsv) s daty oddělenými tabulátory test řádku detox Wikipedia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="334e4-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="334e4-124">Pracovní postup Machine learning</span><span class="sxs-lookup"><span data-stu-id="334e4-124">Machine learning workflow</span></span>

<span data-ttu-id="334e4-125">V tomto kurzu se řídí strojového učení pracovního postupu, který umožňuje přesunout řádný proces.</span><span class="sxs-lookup"><span data-stu-id="334e4-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="334e4-126">Fáze pracovního postupu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="334e4-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="334e4-127">**Pochopení problému**</span><span class="sxs-lookup"><span data-stu-id="334e4-127">**Understand the problem**</span></span>
2. <span data-ttu-id="334e4-128">**Zpracování příjmu dat**</span><span class="sxs-lookup"><span data-stu-id="334e4-128">**Ingest the data**</span></span>
3. <span data-ttu-id="334e4-129">**Předběžné zpracování dat a návrh funkcí**</span><span class="sxs-lookup"><span data-stu-id="334e4-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="334e4-130">**Trénování a předpověď modelu**</span><span class="sxs-lookup"><span data-stu-id="334e4-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="334e4-131">**Vyhodnocení modelu**</span><span class="sxs-lookup"><span data-stu-id="334e4-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="334e4-132">**Operacionalizace modelu**</span><span class="sxs-lookup"><span data-stu-id="334e4-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="334e4-133">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="334e4-133">Understand the problem</span></span>

<span data-ttu-id="334e4-134">Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="334e4-135">Rozdělení problému můžete předpovídat a vyhodnoťte výsledky.</span><span class="sxs-lookup"><span data-stu-id="334e4-135">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="334e4-136">Problém pro účely tohoto kurzu je pochopit příchozí subjektivního hodnocení webu komentář, proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="334e4-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="334e4-137">Problém můžete rozdělit mínění textu a mínění hodnotu pro data chcete trénování modelu s a předpokládané mínění hodnotu, kterou můžete vyhodnotit a pak použít provozně.</span><span class="sxs-lookup"><span data-stu-id="334e4-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="334e4-138">Potom budete potřebovat **určit** subjektivního hodnocení, které vám pomůžou s strojového učení výběr úkolů.</span><span class="sxs-lookup"><span data-stu-id="334e4-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="334e4-139">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="334e4-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="334e4-140">Tento problém víte, k následujícím skutečnostem:</span><span class="sxs-lookup"><span data-stu-id="334e4-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="334e4-141">Cvičná data: komentáře web může být kladná nebo záporná (**mínění**).</span><span class="sxs-lookup"><span data-stu-id="334e4-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="334e4-142">Předpověď **mínění** nový web komentáře, kladná nebo záporná, jako například v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="334e4-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="334e4-143">Nepřidávejte nesmysl na wikipedii.</span><span class="sxs-lookup"><span data-stu-id="334e4-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="334e4-144">Je to nejlepší a článek, který by mělo být uvedeno.</span><span class="sxs-lookup"><span data-stu-id="334e4-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="334e4-145">Úloha klasifikace machine learning je nejvhodnější pro tento scénář.</span><span class="sxs-lookup"><span data-stu-id="334e4-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="334e4-146">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="334e4-146">About the classification task</span></span>

<span data-ttu-id="334e4-147">Klasifikace je úloha strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky.</span><span class="sxs-lookup"><span data-stu-id="334e4-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="334e4-148">Například můžete použít klasifikace:</span><span class="sxs-lookup"><span data-stu-id="334e4-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="334e4-149">Zjistit mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="334e4-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="334e4-150">E-mailu klasifikujte jako spam nevyžádané nebo funkční.</span><span class="sxs-lookup"><span data-stu-id="334e4-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="334e4-151">Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="334e4-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="334e4-152">Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.</span><span class="sxs-lookup"><span data-stu-id="334e4-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="334e4-153">Úlohy klasifikace jsou často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="334e4-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="334e4-154">Binární soubor: buď A a B.</span><span class="sxs-lookup"><span data-stu-id="334e4-154">Binary: either A or B.</span></span>
* <span data-ttu-id="334e4-155">Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="334e4-156">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="334e4-156">Create a console application</span></span>

1. <span data-ttu-id="334e4-157">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="334e4-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="334e4-158">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="334e4-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="334e4-159">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="334e4-159">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="334e4-160">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="334e4-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="334e4-161">V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="334e4-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="334e4-162">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="334e4-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="334e4-163">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="334e4-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="334e4-164">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="334e4-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="334e4-165">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="334e4-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="334e4-166">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="334e4-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="334e4-167">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="334e4-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="334e4-168">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="334e4-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="334e4-169">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="334e4-169">Prepare your data</span></span>

1. <span data-ttu-id="334e4-170">Stáhněte si [WikiPedia detox – 250řádku data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) a [wikipedia – detox – 250řádku test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka.</span><span class="sxs-lookup"><span data-stu-id="334e4-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="334e4-171">První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="334e4-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="334e4-172">V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="334e4-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="334e4-173">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="334e4-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="334e4-174">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="334e4-174">Create classes and define paths</span></span>

<span data-ttu-id="334e4-175">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="334e4-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="334e4-176">Je potřeba vytvořit tři globální pole pro uložení cest k naposledy stažené soubory:</span><span class="sxs-lookup"><span data-stu-id="334e4-176">You need to create three global fields to hold the paths to the recently downloaded files:</span></span>

* <span data-ttu-id="334e4-177">`_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="334e4-178">`_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="334e4-179">`_modelPath` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="334e4-180">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="334e4-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="334e4-181">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="334e4-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="334e4-182">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="334e4-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="334e4-183">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="334e4-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="334e4-184">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="334e4-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="334e4-185">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="334e4-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="334e4-186">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="334e4-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="334e4-187">Přidejte následující `using` příkaz do horní části *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="334e4-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="334e4-188">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="334e4-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="334e4-189">`SentimentData` je třída vstupní datová sada a má `float` (`Sentiment`), který má hodnotu pro pozitivní nebo negativní zabarvení a řetězec pro komentář (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="334e4-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="334e4-190">Obě pole mají `Column` atributy připojené k nim.</span><span class="sxs-lookup"><span data-stu-id="334e4-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="334e4-191">Popisuje pořadí každé pole v datovém souboru a které je tento atribut `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="334e4-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="334e4-192">`SentimentPrediction` Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="334e4-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="334e4-193">Má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="334e4-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="334e4-194">`Label` Slouží k vytvoření a trénování modelu a jeho datové sady druhé použít také k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="334e4-195">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="334e4-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="334e4-196">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="334e4-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="334e4-197">V *Program.cs* změňte `Main` podpis metody tak, že nahradíte `void` s `async Task`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="334e4-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="334e4-198">Přidáte `async` k `Main` s <xref:System.Threading.Tasks.Task> návratový typ, protože ukládání modelu do souboru zip později, a program musí počkat až do dokončení této úlohy externí.</span><span class="sxs-lookup"><span data-stu-id="334e4-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="334e4-199">*Asynchronní funkce main* metoda vám umožňuje používat `await` ve vaší `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="334e4-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="334e4-200">Další informace najdete v tématu [asynchronní funkce main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) v Průvodci programovacího jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="334e4-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="334e4-201">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="334e4-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="334e4-202">`Train` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="334e4-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="334e4-203">Načte nebo ingestuje data.</span><span class="sxs-lookup"><span data-stu-id="334e4-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="334e4-204">Předzpracuje a featurizes data.</span><span class="sxs-lookup"><span data-stu-id="334e4-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="334e4-205">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-205">Trains the model.</span></span>
* <span data-ttu-id="334e4-206">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="334e4-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="334e4-207">Vytvořte `Train` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="334e4-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="334e4-208">Zpracování příjmu dat</span><span class="sxs-lookup"><span data-stu-id="334e4-208">Ingest the data</span></span>

<span data-ttu-id="334e4-209">Inicializuje novou instanci třídy <xref:Microsoft.ML.LearningPipeline> , který bude obsahovat načítání dat, zpracování dat a snadné a modelu.</span><span class="sxs-lookup"><span data-stu-id="334e4-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="334e4-210">Přidejte následující kód jako první řádek `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="334e4-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="334e4-211"><xref:Microsoft.ML.Data.TextLoader> Objektu je první částí kanálu a načte soubor trénovací data.</span><span class="sxs-lookup"><span data-stu-id="334e4-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="334e4-212">Předběžné zpracování dat a návrh funkcí</span><span class="sxs-lookup"><span data-stu-id="334e4-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="334e4-213">Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="334e4-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="334e4-214">Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="334e4-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="334e4-215">Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="334e4-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="334e4-216">ML. NET pro transformace kanály umožňují napsat vlastní sadu transformací, které se použijí pro vaše data před trénování a testování.</span><span class="sxs-lookup"><span data-stu-id="334e4-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="334e4-217">Hlavním účelem transformace je pro snadné data.</span><span class="sxs-lookup"><span data-stu-id="334e4-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="334e4-218">Výhodou transformace kanálu, který je po definici kanál transformace, uložit kanálu, který má být použit testovací data.</span><span class="sxs-lookup"><span data-stu-id="334e4-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="334e4-219">Použít <xref:Microsoft.ML.Transforms.TextFeaturizer> převést `SentimentText` sloupec [číselné vektoru](../resources/glossary.md#numerical-feature-vector) volá `Features` používá algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="334e4-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="334e4-220">Jedná se o krok předběžného zpracování a snadné.</span><span class="sxs-lookup"><span data-stu-id="334e4-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="334e4-221">Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.</span><span class="sxs-lookup"><span data-stu-id="334e4-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="334e4-222">Přidat `TextFeaturizer` do kanálu jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="334e4-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="334e4-223">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="334e4-223">Choose a learning algorithm</span></span>

<span data-ttu-id="334e4-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Je objekt learner stromu rozhodnutí v tomto kanálu použijete.</span><span class="sxs-lookup"><span data-stu-id="334e4-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="334e4-225">Podobně jako v kroku snadné, vyzkoušejte si různé inteligentních algoritmů k dispozici v ML.NET a změna jejich parametrů vede k jiné výsledky.</span><span class="sxs-lookup"><span data-stu-id="334e4-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="334e4-226">Pro ladění, můžete nastavit [hyperparameters](../resources/glossary.md#hyperparameter) jako <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, a <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span><span class="sxs-lookup"><span data-stu-id="334e4-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="334e4-227">Tyto hyperparameters nastavují před nic ovlivňuje modelu a jsou specifické pro model.</span><span class="sxs-lookup"><span data-stu-id="334e4-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="334e4-228">Slouží k vyladění rozhodovací strom pro výkon, takže vyšší hodnoty může mít negativní vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="334e4-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="334e4-229">Přidejte následující kód, který `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="334e4-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="334e4-230">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="334e4-230">Train the model</span></span>

<span data-ttu-id="334e4-231">Trénování modelu, <xref:Microsoft.ML.PredictionModel%602>založená na datovou sadu, která má načíst a transformovat.</span><span class="sxs-lookup"><span data-stu-id="334e4-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="334e4-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trénovat kanálu (načítá data, železniční featurizer a learner).</span><span class="sxs-lookup"><span data-stu-id="334e4-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="334e4-233">Experiment není spuštěn, dokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="334e4-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="334e4-234">Přidejte následující kód, který `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="334e4-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="334e4-235">Uložte a vraťte se model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="334e4-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="334e4-236">V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="334e4-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="334e4-237">Chcete-li uložit model do souboru ZIP a teprve potom se informuje, přidejte následující kód na další řádek v `Train`:</span><span class="sxs-lookup"><span data-stu-id="334e4-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="334e4-238">Model na konci vrátit `Train` metody.</span><span class="sxs-lookup"><span data-stu-id="334e4-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="334e4-239">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="334e4-239">Evaluate the model</span></span>

<span data-ttu-id="334e4-240">Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování.</span><span class="sxs-lookup"><span data-stu-id="334e4-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="334e4-241">V `Evaluate` metody, vytvořené v modelu `Train` předaný k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="334e4-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="334e4-242">Vytvořte `Evaluate` metoda, hned za `Train`, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="334e4-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="334e4-243">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="334e4-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="334e4-244">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="334e4-244">Loads the test dataset.</span></span>
* <span data-ttu-id="334e4-245">Vytvoří binární Chyba při vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="334e4-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="334e4-246">Vyhodnotí modelu a vytvoření metriky.</span><span class="sxs-lookup"><span data-stu-id="334e4-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="334e4-247">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="334e4-247">Displays the metrics.</span></span>

<span data-ttu-id="334e4-248">Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="334e4-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="334e4-249"><xref:Microsoft.ML.Data.TextLoader> Třídy načte nová datová sada testů s stejné schéma.</span><span class="sxs-lookup"><span data-stu-id="334e4-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="334e4-250">Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality.</span><span class="sxs-lookup"><span data-stu-id="334e4-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="334e4-251">Přidejte následující kód, který `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="334e4-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="334e4-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Vypočítá metrik kvality pro objekt `PredictionModel` pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="334e4-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="334e4-253">Pokud chcete zobrazit tyto metriky, přidejte Chyba při vyhodnocování jako na další řádek v `Evaluate` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="334e4-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="334e4-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> Obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="334e4-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="334e4-255">Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první.</span><span class="sxs-lookup"><span data-stu-id="334e4-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="334e4-256">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="334e4-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="334e4-257">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="334e4-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="334e4-258">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="334e4-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="334e4-259">Předpověď výsledků dat testu s modelem</span><span class="sxs-lookup"><span data-stu-id="334e4-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="334e4-260">Vytvořte `Predict` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="334e4-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="334e4-261">`Predict` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="334e4-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="334e4-262">Vytvoří testovací data.</span><span class="sxs-lookup"><span data-stu-id="334e4-262">Creates test data.</span></span>
* <span data-ttu-id="334e4-263">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="334e4-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="334e4-264">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="334e4-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="334e4-265">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="334e4-265">Displays the predicted results.</span></span>

<span data-ttu-id="334e4-266">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="334e4-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="334e4-267">Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="334e4-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="334e4-268">Teď, když máte model, vám pomůže, která předvídat pozitivní nebo negativní zabarvení komentář dat pomocí <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="334e4-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="334e4-269">Chcete-li získat predikcí, použijte `Predict` na nová data.</span><span class="sxs-lookup"><span data-stu-id="334e4-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="334e4-270">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="334e4-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="334e4-271">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="334e4-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="334e4-272">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="334e4-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="334e4-273">Operacionalizace modelu: předpověď</span><span class="sxs-lookup"><span data-stu-id="334e4-273">Model operationalization: prediction</span></span>

<span data-ttu-id="334e4-274">Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="334e4-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="334e4-275">Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady.</span><span class="sxs-lookup"><span data-stu-id="334e4-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="334e4-276">Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="334e4-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="334e4-277">Před zobrazením předpokládané výsledky, kombinovat mínění a predikcí společně zobrazíte původním komentářem s jeho predikované mínění.</span><span class="sxs-lookup"><span data-stu-id="334e4-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="334e4-278">Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda docílit, vedle proto přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="334e4-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="334e4-279">Teď, když jste kombinovat `SentimentText` a `Sentiment` do třídy, můžete zobrazit výsledky pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="334e4-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="334e4-280">Protože odvozené názvy elementů řazené kolekce členů se, že je nová funkce v jazyce C# 7.1 a výchozí jazyková verze projektu C# 7.0, potřebujete změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="334e4-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="334e4-281">To mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="334e4-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="334e4-282">Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="334e4-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="334e4-283">V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="334e4-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="334e4-284">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="334e4-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="334e4-285">výsledky</span><span class="sxs-lookup"><span data-stu-id="334e4-285">Results</span></span>

<span data-ttu-id="334e4-286">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="334e4-286">Your results should be similar to the following.</span></span> <span data-ttu-id="334e4-287">Při zpracování kanálu zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="334e4-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="334e4-288">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="334e4-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="334e4-289">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="334e4-289">These have been removed from the following results for clarity.</span></span>

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

<span data-ttu-id="334e4-290">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="334e4-290">Congratulations!</span></span> <span data-ttu-id="334e4-291">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění.</span><span class="sxs-lookup"><span data-stu-id="334e4-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="334e4-292">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="334e4-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="334e4-293">Další kroky</span><span class="sxs-lookup"><span data-stu-id="334e4-293">Next steps</span></span>

<span data-ttu-id="334e4-294">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="334e4-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="334e4-295">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="334e4-295">Understand the problem</span></span>
> * <span data-ttu-id="334e4-296">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="334e4-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="334e4-297">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="334e4-297">Prepare your data</span></span>
> * <span data-ttu-id="334e4-298">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="334e4-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="334e4-299">Načíst třídění</span><span class="sxs-lookup"><span data-stu-id="334e4-299">Load a classifier</span></span>
> * <span data-ttu-id="334e4-300">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="334e4-300">Train the model</span></span>
> * <span data-ttu-id="334e4-301">Vyhodnocení modelu s jinou datovou sadu</span><span class="sxs-lookup"><span data-stu-id="334e4-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="334e4-302">Předpověď výsledků dat testu s modelem</span><span class="sxs-lookup"><span data-stu-id="334e4-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="334e4-303">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="334e4-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="334e4-304">Prediktivní tarif taxislužby města</span><span class="sxs-lookup"><span data-stu-id="334e4-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
