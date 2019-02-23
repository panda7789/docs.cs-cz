---
title: Použití ML.NET ve scénáři binární klasifikace analýzy mínění
description: Objevte, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí mínění předpovědi proveďte příslušnou akci.
ms.date: 02/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 9afdf1d8369e71f9614ebc2bf327e98d31b988ff
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748385"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="6f39d-103">Kurz: Použití ML.NET ve scénáři binární klasifikace analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="6f39d-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="6f39d-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="6f39d-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="6f39d-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6f39d-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="6f39d-106">Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru mínění prostřednictvím aplikace konzoly .NET Core pomocí jazyka C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6f39d-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="6f39d-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="6f39d-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6f39d-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="6f39d-108">Understand the problem</span></span>
> * <span data-ttu-id="6f39d-109">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="6f39d-109">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="6f39d-110">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="6f39d-110">Prepare your data</span></span>
> * <span data-ttu-id="6f39d-111">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="6f39d-111">Transform the data</span></span>
> * <span data-ttu-id="6f39d-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-112">Train the model</span></span>
> * <span data-ttu-id="6f39d-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-113">Evaluate the model</span></span>
> * <span data-ttu-id="6f39d-114">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-114">Predict with the trained model</span></span>
> * <span data-ttu-id="6f39d-115">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="6f39d-115">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="6f39d-116">Přehled ukázky analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="6f39d-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="6f39d-117">Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="6f39d-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="6f39d-118">Vyhodnocuje také model s druhou datové sady pro analýzy kvality.</span><span class="sxs-lookup"><span data-stu-id="6f39d-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="6f39d-119">Datové sady subjektivního hodnocení jsou z WikiDetox projektu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-119">The sentiment datasets are from the WikiDetox project.</span></span>

<span data-ttu-id="6f39d-120">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="6f39d-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f39d-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f39d-121">Prerequisites</span></span>

* <span data-ttu-id="6f39d-122">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="6f39d-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="6f39d-123">[Souboru (wikiPedia – detox – 250řádku data.tsv) s daty oddělenými tabulátory data řádku detox Wikipedia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="6f39d-123">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="6f39d-124">[Souboru (wikipedia – detox – 250řádku test.tsv) s daty oddělenými tabulátory test řádku detox Wikipedia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="6f39d-124">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="6f39d-125">Pracovní postup Machine learning</span><span class="sxs-lookup"><span data-stu-id="6f39d-125">Machine learning workflow</span></span>

<span data-ttu-id="6f39d-126">V tomto kurzu se řídí strojového učení pracovního postupu, který umožňuje přesunout řádný proces.</span><span class="sxs-lookup"><span data-stu-id="6f39d-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="6f39d-127">Fáze pracovního postupu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6f39d-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="6f39d-128">**Pochopení problému**</span><span class="sxs-lookup"><span data-stu-id="6f39d-128">**Understand the problem**</span></span>
2. <span data-ttu-id="6f39d-129">**Příprava dat**</span><span class="sxs-lookup"><span data-stu-id="6f39d-129">**Prepare your data**</span></span>
   * <span data-ttu-id="6f39d-130">**Načtení dat**</span><span class="sxs-lookup"><span data-stu-id="6f39d-130">**Load the data**</span></span>
   * <span data-ttu-id="6f39d-131">**Extrakce funkce (transformovat data)**</span><span class="sxs-lookup"><span data-stu-id="6f39d-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="6f39d-132">**Sestavení a trénování**</span><span class="sxs-lookup"><span data-stu-id="6f39d-132">**Build and train**</span></span> 
   * <span data-ttu-id="6f39d-133">**Trénování modelu**</span><span class="sxs-lookup"><span data-stu-id="6f39d-133">**Train the model**</span></span>
   * <span data-ttu-id="6f39d-134">**Vyhodnocení modelu**</span><span class="sxs-lookup"><span data-stu-id="6f39d-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="6f39d-135">**Nasazení modelu**</span><span class="sxs-lookup"><span data-stu-id="6f39d-135">**Deploy Model**</span></span>
   * <span data-ttu-id="6f39d-136">**Použijte Model k predikci**</span><span class="sxs-lookup"><span data-stu-id="6f39d-136">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="6f39d-137">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="6f39d-137">Understand the problem</span></span>

<span data-ttu-id="6f39d-138">Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="6f39d-139">Rozdělení problému můžete předpovídat a vyhodnoťte výsledky.</span><span class="sxs-lookup"><span data-stu-id="6f39d-139">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="6f39d-140">Problém pro účely tohoto kurzu je pochopit příchozí subjektivního hodnocení webu komentář, proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="6f39d-140">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="6f39d-141">Problém můžete rozdělit mínění textu a mínění hodnotu pro data chcete trénování modelu s a předpokládané mínění hodnotu, kterou můžete vyhodnotit a pak použít provozně.</span><span class="sxs-lookup"><span data-stu-id="6f39d-141">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="6f39d-142">Potom budete potřebovat **určit** subjektivního hodnocení, které vám pomůžou s strojového učení výběr úkolů.</span><span class="sxs-lookup"><span data-stu-id="6f39d-142">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="6f39d-143">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="6f39d-143">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="6f39d-144">Tento problém víte, k následujícím skutečnostem:</span><span class="sxs-lookup"><span data-stu-id="6f39d-144">With this problem, you know the following facts:</span></span>

<span data-ttu-id="6f39d-145">Cvičná data: komentáře web může být toxické (1) nebo ne toxické (0) (**mínění**).</span><span class="sxs-lookup"><span data-stu-id="6f39d-145">Training data: website comments can be toxic (1) or not toxic (0) (**sentiment**).</span></span>
<span data-ttu-id="6f39d-146">Předpověď **mínění** nový web komentáře, toxické nebo není toxické, jako například v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="6f39d-146">Predict the **sentiment** of a new website comment, either toxic or not toxic, such as in the following examples:</span></span>

* <span data-ttu-id="6f39d-147">Nepřidávejte nesmysl na wikipedii.</span><span class="sxs-lookup"><span data-stu-id="6f39d-147">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="6f39d-148">Je to nejlepší a článek, který by mělo být uvedeno.</span><span class="sxs-lookup"><span data-stu-id="6f39d-148">He is the best, and the article should say that.</span></span>

<span data-ttu-id="6f39d-149">Algoritmu strojového učení klasifikace je nejvhodnější pro tento scénář.</span><span class="sxs-lookup"><span data-stu-id="6f39d-149">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="6f39d-150">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="6f39d-150">About the classification task</span></span>

<span data-ttu-id="6f39d-151">Klasifikace je algoritmus strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky.</span><span class="sxs-lookup"><span data-stu-id="6f39d-151">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="6f39d-152">Například můžete použít klasifikace:</span><span class="sxs-lookup"><span data-stu-id="6f39d-152">For example, you can use classification to:</span></span>

* <span data-ttu-id="6f39d-153">Zjistit mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="6f39d-153">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="6f39d-154">E-mailu klasifikujte jako spam nevyžádané nebo funkční.</span><span class="sxs-lookup"><span data-stu-id="6f39d-154">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="6f39d-155">Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="6f39d-155">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="6f39d-156">Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.</span><span class="sxs-lookup"><span data-stu-id="6f39d-156">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="6f39d-157">Algoritmy klasifikace jsou často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="6f39d-157">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="6f39d-158">Binární soubor: buď A a B.</span><span class="sxs-lookup"><span data-stu-id="6f39d-158">Binary: either A or B.</span></span>
* <span data-ttu-id="6f39d-159">Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-159">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="6f39d-160">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="6f39d-160">Create a console application</span></span>

1. <span data-ttu-id="6f39d-161">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6f39d-161">Open Visual Studio 2017.</span></span> <span data-ttu-id="6f39d-162">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="6f39d-162">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="6f39d-163">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-163">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="6f39d-164">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-164">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="6f39d-165">V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6f39d-165">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="6f39d-166">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="6f39d-166">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="6f39d-167">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="6f39d-167">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="6f39d-168">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="6f39d-168">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="6f39d-169">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="6f39d-169">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="6f39d-170">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6f39d-170">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="6f39d-171">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6f39d-171">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="6f39d-172">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="6f39d-172">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="6f39d-173">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="6f39d-173">Prepare your data</span></span>

1. <span data-ttu-id="6f39d-174">Stáhněte si [Wikipedia detox – 250řádku data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) a [wikipedia – detox – 250řádku test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka.</span><span class="sxs-lookup"><span data-stu-id="6f39d-174">Download the [Wikipedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="6f39d-175">První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="6f39d-175">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="6f39d-176">V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6f39d-176">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="6f39d-177">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="6f39d-177">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="6f39d-178">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="6f39d-178">Create classes and define paths</span></span>

<span data-ttu-id="6f39d-179">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="6f39d-179">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="6f39d-180">Je potřeba vytvořit tři globální pole pro uložení cest k naposledy stažené soubory a globální proměnné pro `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="6f39d-180">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="6f39d-181">`_trainDataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-181">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="6f39d-182">`_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-182">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="6f39d-183">`_modelPath` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-183">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="6f39d-184">`_textLoader` je <xref:Microsoft.ML.Data.TextLoader> lze načíst a transformovat datové sady.</span><span class="sxs-lookup"><span data-stu-id="6f39d-184">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="6f39d-185">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty a `_textLoader` proměnné:</span><span class="sxs-lookup"><span data-stu-id="6f39d-185">Add the following code to the line right above the `Main` method to specify those paths and the `_textLoader` variable:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

<span data-ttu-id="6f39d-186">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6f39d-186">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="6f39d-187">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-187">Add a new class to your project:</span></span>

1. <span data-ttu-id="6f39d-188">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="6f39d-188">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="6f39d-189">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="6f39d-189">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="6f39d-190">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6f39d-190">Then, select the **Add** button.</span></span>

    <span data-ttu-id="6f39d-191">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-191">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="6f39d-192">Přidejte následující `using` příkaz do horní části *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="6f39d-192">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="6f39d-193">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="6f39d-193">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="6f39d-194">`SentimentData` je třída vstupní datová sada a má `float` (`Sentiment`), který má hodnotu pro pozitivní nebo negativní zabarvení a řetězec pro komentář (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="6f39d-194">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="6f39d-195">Obě pole mají `Column` atributy připojené k nim.</span><span class="sxs-lookup"><span data-stu-id="6f39d-195">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="6f39d-196">Popisuje pořadí každé pole v datovém souboru a které je tento atribut `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="6f39d-196">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="6f39d-197">`SentimentPrediction` Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="6f39d-197">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="6f39d-198">Má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="6f39d-198">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="6f39d-199">`Label` Slouží k vytvoření a trénování modelu a jeho datové sady druhé použít také k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-199">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="6f39d-200">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="6f39d-200">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="6f39d-201">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="6f39d-201">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="6f39d-202">Při vytváření modelu s ML.NET začnete vytvořením `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="6f39d-202">When building a model with ML.NET you start by creating an `MLContext`.</span></span> <span data-ttu-id="6f39d-203">Toto je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6f39d-203">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="6f39d-204">Prostředí poskytuje kontext pro vaši úlohu ML, který lze použít pro sledování a protokolování výjimek.</span><span class="sxs-lookup"><span data-stu-id="6f39d-204">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="6f39d-205">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="6f39d-205">Initialize variables in Main</span></span>

<span data-ttu-id="6f39d-206">Vytvořte proměnnou s názvem `mlContext` a inicializujte novou instanci třídy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="6f39d-206">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="6f39d-207">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-207">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="6f39d-208">Další nastavení pro načítání inicializace dat `_textLoader` globální proměnné, aby bylo možné znovu použít.</span><span class="sxs-lookup"><span data-stu-id="6f39d-208">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="6f39d-209">Při vytváření `TextLoader` pomocí `MLContext.Data.CreateTextLoader`, předáte v souvislosti potřebné a <xref:Microsoft.ML.Data.TextLoader.Arguments> třída, která umožňuje přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="6f39d-209">When you create a `TextLoader` using  `MLContext.Data.CreateTextLoader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span>

 <span data-ttu-id="6f39d-210">Zadejte schéma dat předáním pole <xref:Microsoft.ML.Data.TextLoader.Column> zavaděč obsahující všechny názvy sloupců a jejich typy objektů.</span><span class="sxs-lookup"><span data-stu-id="6f39d-210">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the loader containing all the column names and their types.</span></span> <span data-ttu-id="6f39d-211">Definujete schéma dat dříve při vytváření naše `SentimentData` třídy.</span><span class="sxs-lookup"><span data-stu-id="6f39d-211">You defined the data schema previously when you created our `SentimentData` class.</span></span> <span data-ttu-id="6f39d-212">Pro naše schéma z prvního sloupce (popisek) je <xref:System.Boolean> (předpověď) a druhý sloupec (SentimentText) je funkce typu text/řetězec použitý pro predikci mínění.</span><span class="sxs-lookup"><span data-stu-id="6f39d-212">For our schema, the first column (Label) is a <xref:System.Boolean> (the prediction) and the second column (SentimentText) is the feature of type text/string used for predicting the sentiment.</span></span>
<span data-ttu-id="6f39d-213">`TextLoader` Třídy vrátí plně inicializován <xref:Microsoft.ML.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="6f39d-213">The `TextLoader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="6f39d-214">Inicializovat `_textLoader` globální proměnné, aby bylo možné znovu použít pro potřeby datové sady, přidejte následující kód za `mlContext` inicializace:</span><span class="sxs-lookup"><span data-stu-id="6f39d-214">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="6f39d-215">Přidejte následující položky jako další řádek kódu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-215">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

<span data-ttu-id="6f39d-216">`Train` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="6f39d-216">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="6f39d-217">Načte data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-217">Loads the data.</span></span>
* <span data-ttu-id="6f39d-218">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-218">Extracts and transforms the data.</span></span>
* <span data-ttu-id="6f39d-219">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-219">Trains the model.</span></span>
* <span data-ttu-id="6f39d-220">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-220">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="6f39d-221">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-221">Returns the model.</span></span>

<span data-ttu-id="6f39d-222">Vytvořte `Train` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-222">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="6f39d-223">Všimněte si, že dva parametry jsou předány do metody trénování; `MLContext` kontextu (`mlContext`) a <xref:System.String> pro cestu k datové sadě (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="6f39d-223">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and a <xref:System.String> for the dataset path (`dataPath`).</span></span> <span data-ttu-id="6f39d-224">Chystáte se tuto metodu použít více než jednou pro trénování a testování.</span><span class="sxs-lookup"><span data-stu-id="6f39d-224">You're going to use this method more than once for training and testing.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="6f39d-225">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6f39d-225">Load the data</span></span>

<span data-ttu-id="6f39d-226">Budete nahrajte data s využitím `_textLoader` globální proměnné `dataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="6f39d-226">You'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="6f39d-227">Vrátí <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="6f39d-227">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> <span data-ttu-id="6f39d-228">Jako vstup a výstup `Transforms`, `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="6f39d-228">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="6f39d-229">Data jsou v ML.NET, podobně jako zobrazení SQL.</span><span class="sxs-lookup"><span data-stu-id="6f39d-229">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="6f39d-230">Je laxně Vyhodnocená schematizovanými a heterogenní.</span><span class="sxs-lookup"><span data-stu-id="6f39d-230">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="6f39d-231">Objekt představuje první část kanálu a načte data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-231">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="6f39d-232">Pro účely tohoto kurzu načte datovou sadu s komentáři a odpovídající toxické nebo jiných toxické mínění.</span><span class="sxs-lookup"><span data-stu-id="6f39d-232">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="6f39d-233">Slouží k vytvoření modelu a jeho trénování.</span><span class="sxs-lookup"><span data-stu-id="6f39d-233">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="6f39d-234">Přidejte následující kód jako první řádek `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-234">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="6f39d-235">Extrahovat a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="6f39d-235">Extract and transform the data</span></span>

<span data-ttu-id="6f39d-236">Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="6f39d-236">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="6f39d-237">Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6f39d-237">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="6f39d-238">Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="6f39d-238">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="6f39d-239">ML. Kanály transformace vaší sítě vytvořit vlastní sadu transformací, které se použijí pro vaše data před trénování a testování.</span><span class="sxs-lookup"><span data-stu-id="6f39d-239">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="6f39d-240">Hlavním účelem transformace jsou data [snadné](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="6f39d-240">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="6f39d-241">Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) data, abyste dalším krokem je získat z našich algoritmů ML rozpoznat formát naše textová data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-241">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="6f39d-242">Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="6f39d-242">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="6f39d-243">Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` které featurizes textového sloupce (`SentimentText`) sloupec jako číselný vektor nazývá `Features` používá algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="6f39d-243">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="6f39d-244">Toto je obálka volání, které se vrátí <xref:Microsoft.ML.Data.EstimatorChain%601> efektivně, který bude kanál.</span><span class="sxs-lookup"><span data-stu-id="6f39d-244">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="6f39d-245">Pojmenujte toto `pipeline` jako se pak připojí trainer k `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="6f39d-245">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="6f39d-246">Přidáte jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-246">Add this as the next line of code:</span></span>

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

>[!WARNING]
> <span data-ttu-id="6f39d-247">ML.NET verze 0.10 má změnit pořadí parametrů transformace.</span><span class="sxs-lookup"><span data-stu-id="6f39d-247">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="6f39d-248">Tímto krokem se nevygeneruje chybu, dokud při spuštění aplikace a vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-248">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="6f39d-249">Použijte názvy parametrů transformací, jak je znázorněno v předchozím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-249">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="6f39d-250">Jedná se o krok předběžného zpracování a snadné.</span><span class="sxs-lookup"><span data-stu-id="6f39d-250">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="6f39d-251">Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.</span><span class="sxs-lookup"><span data-stu-id="6f39d-251">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="6f39d-252">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="6f39d-252">Choose a learning algorithm</span></span>

<span data-ttu-id="6f39d-253">Přidáte školitele volání `mlContext.Transforms.Text.FeaturizeText` obalující metodu, která vrátí hodnotu <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> objektu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-253">To add the trainer, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="6f39d-254">Toto je learner stromu rozhodnutí, které budete používat v tomto kanálu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-254">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="6f39d-255">`FastTreeBinaryClassificationTrainer` Se připojí `pipeline` a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="6f39d-255">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="6f39d-256">Přidejte následující kód, který `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-256">Add the following code to the `Train` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="6f39d-257">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-257">Train the model</span></span>

<span data-ttu-id="6f39d-258">Trénování modelu, <xref:Microsoft.ML.Data.TransformerChain%601>založená na datovou sadu, která má načíst a transformovat.</span><span class="sxs-lookup"><span data-stu-id="6f39d-258">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="6f39d-259">Po definování odhadu tréninku modelu pomocí <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> současně už načtený trénovací data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-259">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> while providing the already loaded training data.</span></span> <span data-ttu-id="6f39d-260">Vrátí model pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6f39d-260">This returns a model to use for predictions.</span></span> <span data-ttu-id="6f39d-261">`pipeline.Fit()` trénovat kanálu a vrátí `Transformer` na základě `DataView` předán.</span><span class="sxs-lookup"><span data-stu-id="6f39d-261">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="6f39d-262">Experiment není spuštěn, dokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="6f39d-262">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="6f39d-263">Přidejte následující kód, který `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-263">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="6f39d-264">Uložte a vraťte se model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="6f39d-264">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="6f39d-265">V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain%601> , který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="6f39d-265">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="6f39d-266">Model na konci vrátit `Train` metody.</span><span class="sxs-lookup"><span data-stu-id="6f39d-266">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="6f39d-267">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-267">Evaluate the model</span></span>

<span data-ttu-id="6f39d-268">Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování.</span><span class="sxs-lookup"><span data-stu-id="6f39d-268">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="6f39d-269">V `Evaluate` metody, vytvořené v modelu `Train` předaný k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="6f39d-269">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="6f39d-270">Vytvořte `Evaluate` metoda, hned za `Train`, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-270">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="6f39d-271">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="6f39d-271">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="6f39d-272">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="6f39d-272">Loads the test dataset.</span></span>
* <span data-ttu-id="6f39d-273">Vytvoří binární Chyba při vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="6f39d-273">Creates the binary evaluator.</span></span>
* <span data-ttu-id="6f39d-274">Vyhodnotí modelu a vytvoření metriky.</span><span class="sxs-lookup"><span data-stu-id="6f39d-274">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="6f39d-275">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="6f39d-275">Displays the metrics.</span></span>

<span data-ttu-id="6f39d-276">Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-276">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

<span data-ttu-id="6f39d-277">Budete načíst datovou sadu testů pomocí dříve inicializován `_textLoader` globální proměnné `_testDataPath` globální pole.</span><span class="sxs-lookup"><span data-stu-id="6f39d-277">You'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="6f39d-278">Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality.</span><span class="sxs-lookup"><span data-stu-id="6f39d-278">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="6f39d-279">Přidejte následující kód, který `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-279">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

<span data-ttu-id="6f39d-280">V dalším kroku budete pomocí machine learning `model` parametr (transformace) pro vstup funkce a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6f39d-280">Next, you'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="6f39d-281">Přidejte následující kód, který `Evaluate` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="6f39d-281">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

<span data-ttu-id="6f39d-282">`BinaryClassificationContext.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="6f39d-282">The `BinaryClassificationContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="6f39d-283">Vrátí `BinaryClassificationEvaluator.CalibratedResult` objekt obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="6f39d-283">It returns a `BinaryClassificationEvaluator.CalibratedResult` object contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="6f39d-284">Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první.</span><span class="sxs-lookup"><span data-stu-id="6f39d-284">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="6f39d-285">Přidejte následující kód jako další řádek `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-285">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="6f39d-286">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-286">Displaying the metrics for model validation</span></span>

<span data-ttu-id="6f39d-287">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="6f39d-287">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

<span data-ttu-id="6f39d-288">Pokud chcete uložit model do souboru ZIP a teprve potom se informuje, přidejte následující kód k volání `SaveModelAsFile` metody jako další řádek v `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="6f39d-288">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="6f39d-289">Uložit jako soubor a.zip model</span><span class="sxs-lookup"><span data-stu-id="6f39d-289">Save the model as a.zip file</span></span>

<span data-ttu-id="6f39d-290">Vytvořte `SaveModelAsFile` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-290">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="6f39d-291">`SaveModelAsFile` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="6f39d-291">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="6f39d-292">Uloží modelu ve formě souboru .zip.</span><span class="sxs-lookup"><span data-stu-id="6f39d-292">Saves the model as a .zip file.</span></span>

<span data-ttu-id="6f39d-293">Dále vytvořte metodu k uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="6f39d-293">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="6f39d-294">`ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="6f39d-294">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="6f39d-295">Uložit jako soubor zip, vytvoříte `FileStream` bezprostředně před volání `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="6f39d-295">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="6f39d-296">Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="6f39d-296">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
<span data-ttu-id="6f39d-297">Nasazení a predikce v načíst model může také zobrazit, kde soubor byl zapsán napsáním zprávu konzoly `_modelPath`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-297">Deploy and Predict with a loaded model You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="6f39d-298">Předpověď data výsledek testu s modelem uložené</span><span class="sxs-lookup"><span data-stu-id="6f39d-298">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="6f39d-299">Vytvořte `Predict` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-299">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="6f39d-300">`Predict` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="6f39d-300">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="6f39d-301">Vytvoří jeden komentář testovací data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-301">Creates a single comment of test data.</span></span>
* <span data-ttu-id="6f39d-302">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-302">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="6f39d-303">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="6f39d-303">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="6f39d-304">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="6f39d-304">Displays the predicted results.</span></span>

<span data-ttu-id="6f39d-305">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-305">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

<span data-ttu-id="6f39d-306">Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, je potřeba k předpovědím na jednotlivé příklady o velmi běžný scénář produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="6f39d-306">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="6f39d-307"><xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="6f39d-307">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="6f39d-308">Přidejte následující kód k vytvoření `PredictionEngine` jako první řádek `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-308">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
<span data-ttu-id="6f39d-309">Přidejte komentář k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="6f39d-309">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 <span data-ttu-id="6f39d-310">Který můžete použít k predikci toxické nebo jiných toxické mínění jednu instanci data komentáře.</span><span class="sxs-lookup"><span data-stu-id="6f39d-310">You can use that to predict the Toxic or Non Toxic sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="6f39d-311">Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-311">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="6f39d-312">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="6f39d-312">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="6f39d-313">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="6f39d-313">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="6f39d-314">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6f39d-314">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a><span data-ttu-id="6f39d-315">Pomocí modelu: předpověď</span><span class="sxs-lookup"><span data-stu-id="6f39d-315">Using the model: prediction</span></span>

<span data-ttu-id="6f39d-316">Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="6f39d-316">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="6f39d-317">Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady.</span><span class="sxs-lookup"><span data-stu-id="6f39d-317">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="6f39d-318">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-318">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="6f39d-319">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="6f39d-319">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="6f39d-320">Vytvořte `PredictWithModelLoadedFromFile` metoda, těsně před `SaveModelAsFile` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-320">Create the `PredictWithModelLoadedFromFile` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

<span data-ttu-id="6f39d-321">`PredictWithModelLoadedFromFile` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="6f39d-321">The `PredictWithModelLoadedFromFile` method executes the following tasks:</span></span>

* <span data-ttu-id="6f39d-322">Vytvoří služby batch testovací data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-322">Creates batch test data.</span></span>
* <span data-ttu-id="6f39d-323">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="6f39d-323">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="6f39d-324">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="6f39d-324">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="6f39d-325">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="6f39d-325">Displays the predicted results.</span></span>

<span data-ttu-id="6f39d-326">Přidejte volání do nové metody z `Main` metody, v rámci `Predict` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-326">Add a call to the new method from the `Main` method, right under the `Predict` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

<span data-ttu-id="6f39d-327">Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `PredictWithModelLoadedFromFile` metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-327">Add some comments to test the trained model's predictions in the `PredictWithModelLoadedFromFile` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

<span data-ttu-id="6f39d-328">Načíst model</span><span class="sxs-lookup"><span data-stu-id="6f39d-328">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

<span data-ttu-id="6f39d-329">Teď, když máte model, vám pomůže, která předvídat toxické nebo jiných toxické mínění komentář dat pomocí <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6f39d-329">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="6f39d-330">Chcete-li získat predikcí, použijte `Predict` na nová data.</span><span class="sxs-lookup"><span data-stu-id="6f39d-330">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="6f39d-331">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="6f39d-331">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="6f39d-332">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="6f39d-332">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="6f39d-333">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6f39d-333">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="6f39d-334">Přidejte následující kód, který `PredictWithModelLoadedFromFile` metodu předpovědí:</span><span class="sxs-lookup"><span data-stu-id="6f39d-334">Add the following code to the `PredictWithModelLoadedFromFile` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="6f39d-335">Použití načíst model pro předpověď</span><span class="sxs-lookup"><span data-stu-id="6f39d-335">Using the loaded model for prediction</span></span>

<span data-ttu-id="6f39d-336">Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="6f39d-336">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="6f39d-337">Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady.</span><span class="sxs-lookup"><span data-stu-id="6f39d-337">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="6f39d-338">Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="6f39d-338">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

<span data-ttu-id="6f39d-339">Před zobrazením předpokládané výsledky, kombinovat mínění a predikcí společně zobrazíte původním komentářem s jeho predikované mínění.</span><span class="sxs-lookup"><span data-stu-id="6f39d-339">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="6f39d-340">Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda docílit, vedle proto přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="6f39d-340">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="6f39d-341">Teď, když jste kombinovat `SentimentText` a `Sentiment` do třídy, můžete zobrazit výsledky pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="6f39d-341">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

<span data-ttu-id="6f39d-342">Protože odvozené názvy elementů řazené kolekce členů se, že je nová funkce v jazyce C# 7.1 a výchozí jazyková verze projektu C# 7.0, potřebujete změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="6f39d-342">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="6f39d-343">To mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6f39d-343">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="6f39d-344">Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6f39d-344">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="6f39d-345">V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="6f39d-345">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="6f39d-346">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f39d-346">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="6f39d-347">Výsledky</span><span class="sxs-lookup"><span data-stu-id="6f39d-347">Results</span></span>

<span data-ttu-id="6f39d-348">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="6f39d-348">Your results should be similar to the following.</span></span> <span data-ttu-id="6f39d-349">Při zpracování kanálu zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="6f39d-349">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="6f39d-350">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f39d-350">You may see warnings, or processing messages.</span></span> <span data-ttu-id="6f39d-351">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="6f39d-351">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of loaded model with a multiple sample ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: I love this article. | Prediction: Not Toxic | Probability: 0.09454837

```

<span data-ttu-id="6f39d-352">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="6f39d-352">Congratulations!</span></span> <span data-ttu-id="6f39d-353">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění.</span><span class="sxs-lookup"><span data-stu-id="6f39d-353">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="6f39d-354">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="6f39d-354">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6f39d-355">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6f39d-355">Next steps</span></span>

<span data-ttu-id="6f39d-356">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="6f39d-356">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6f39d-357">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="6f39d-357">Understand the problem</span></span>
> * <span data-ttu-id="6f39d-358">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="6f39d-358">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="6f39d-359">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="6f39d-359">Prepare your data</span></span>
> * <span data-ttu-id="6f39d-360">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="6f39d-360">Transform the data</span></span>
> * <span data-ttu-id="6f39d-361">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-361">Train the model</span></span>
> * <span data-ttu-id="6f39d-362">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-362">Evaluate the model</span></span>
> * <span data-ttu-id="6f39d-363">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="6f39d-363">Predict with the trained model</span></span>
> * <span data-ttu-id="6f39d-364">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="6f39d-364">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="6f39d-365">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="6f39d-365">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="6f39d-366">Klasifikace problému</span><span class="sxs-lookup"><span data-stu-id="6f39d-366">Issue Classification</span></span>](github-issue-classification.md)
