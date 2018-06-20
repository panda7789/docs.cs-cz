---
title: Použití ML.NET ve scénáři postojích analysis binární klasifikace
description: Zjistit, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí postojích předpovědi proveďte příslušnou akci.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 85fb55582d891c67f172effa4952f15ac5604d50
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207661"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="663eb-103">Kurz: Použití ML.NET ve scénáři postojích analysis binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="663eb-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="663eb-104">Toto téma označuje ML.NET, který je aktuálně ve verzi Preview, a materiálů, mohou se měnit.</span><span class="sxs-lookup"><span data-stu-id="663eb-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="663eb-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="663eb-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="663eb-106">V tomto kurzu ukázka znázorňuje pomocí ML.NET vytvoření klasifikátoru postojích prostřednictvím aplikace konzoly .NET Core pomocí jazyka C# v Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="663eb-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="663eb-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="663eb-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="663eb-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="663eb-108">Understand the problem</span></span>
> * <span data-ttu-id="663eb-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="663eb-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="663eb-110">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="663eb-110">Prepare your data</span></span>
> * <span data-ttu-id="663eb-111">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="663eb-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="663eb-112">Načíst třídění</span><span class="sxs-lookup"><span data-stu-id="663eb-112">Load a classifier</span></span>
> * <span data-ttu-id="663eb-113">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="663eb-113">Train the model</span></span>
> * <span data-ttu-id="663eb-114">Vyhodnocení modelu s jinou datové sady</span><span class="sxs-lookup"><span data-stu-id="663eb-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="663eb-115">Předpověď výstupy testovací data s modelem</span><span class="sxs-lookup"><span data-stu-id="663eb-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="663eb-116">Přehled ukázkové postojích analýzy</span><span class="sxs-lookup"><span data-stu-id="663eb-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="663eb-117">Ukázka je konzolovou aplikaci, která používá ML.NET k natrénování modelu, který klasifikuje a předpovídá postojích jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="663eb-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="663eb-118">Vyhodnotí také model s druhou datovou sadu pro analýzu kvality.</span><span class="sxs-lookup"><span data-stu-id="663eb-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="663eb-119">Datové sady postojích jsou z WikiDetox projektu.</span><span class="sxs-lookup"><span data-stu-id="663eb-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="663eb-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="663eb-120">Prerequisites</span></span>

* <span data-ttu-id="663eb-121">[Visual Studio 2017 15,6 nebo novější](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.</span><span class="sxs-lookup"><span data-stu-id="663eb-121">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="663eb-122">[Karta data řádku detox Wikipedia oddělený soubor (wikiPedia-detox – 250řádku data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="663eb-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="663eb-123">[Karta testu řádku detox Wikipedia oddělený soubor (wikipedia-detox – 250řádku test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="663eb-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="663eb-124">Pracovní postup Machine learning</span><span class="sxs-lookup"><span data-stu-id="663eb-124">Machine learning workflow</span></span>

<span data-ttu-id="663eb-125">V tomto kurzu následuje machine learning pracovního postupu, který umožňuje proces přesunout normálním způsobem.</span><span class="sxs-lookup"><span data-stu-id="663eb-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="663eb-126">Fáze pracovního postupu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="663eb-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="663eb-127">**Porozumět problému**</span><span class="sxs-lookup"><span data-stu-id="663eb-127">**Understand the problem**</span></span>
2. <span data-ttu-id="663eb-128">**Zpracování příjmu dat**</span><span class="sxs-lookup"><span data-stu-id="663eb-128">**Ingest the data**</span></span>
3. <span data-ttu-id="663eb-129">**Předběžné zpracování dat a konstruování**</span><span class="sxs-lookup"><span data-stu-id="663eb-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="663eb-130">**Trénování a předpovědi modelu**</span><span class="sxs-lookup"><span data-stu-id="663eb-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="663eb-131">**Vyhodnocení modelu**</span><span class="sxs-lookup"><span data-stu-id="663eb-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="663eb-132">**Model operationalization**</span><span class="sxs-lookup"><span data-stu-id="663eb-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="663eb-133">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="663eb-133">Understand the problem</span></span>

<span data-ttu-id="663eb-134">Nejdřív musíte pochopit problém, takže lze ho rozdělit na části, které podporují vytváření a cvičení modelu.</span><span class="sxs-lookup"><span data-stu-id="663eb-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="663eb-135">Pozastavení problém dolů k předvídání a vyhodnoťte výsledky.</span><span class="sxs-lookup"><span data-stu-id="663eb-135">Breaking the problem down you to predict and evaluate the results.</span></span>

<span data-ttu-id="663eb-136">Problém pro účely tohoto kurzu je pochopit příchozí postojích webu komentář k proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="663eb-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="663eb-137">Problém můžete rozdělit postojích text a postojích hodnotu pro data chcete trénování modelu s a předpokládaných postojích hodnotu, která můžete vyhodnotit a pak použít provozně.</span><span class="sxs-lookup"><span data-stu-id="663eb-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="663eb-138">Bude potřeba **určit** postojích, který vám pomůže s strojového učení výběr úkolů.</span><span class="sxs-lookup"><span data-stu-id="663eb-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="663eb-139">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="663eb-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="663eb-140">S tímto problémem znáte tyto skutečnosti:</span><span class="sxs-lookup"><span data-stu-id="663eb-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="663eb-141">Cvičení data: komentáře webu může být kladná nebo záporná (**postojích**).</span><span class="sxs-lookup"><span data-stu-id="663eb-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="663eb-142">Předpověď **postojích** nové komentáře webu, kladná nebo záporná, například v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="663eb-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="663eb-143">Nepoužívejte přidávání nesmysl do Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="663eb-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="663eb-144">Je nejvhodnější a by mělo být uvedeno článek, který.</span><span class="sxs-lookup"><span data-stu-id="663eb-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="663eb-145">Úloha klasifikace machine learning je nejvhodnější pro tento scénář.</span><span class="sxs-lookup"><span data-stu-id="663eb-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="663eb-146">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="663eb-146">About the classification task</span></span>

<span data-ttu-id="663eb-147">Klasifikace je strojové učení úkol, který používá data **určit** kategorie, typu nebo třídy řádek dat nebo položky.</span><span class="sxs-lookup"><span data-stu-id="663eb-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="663eb-148">Například můžete použít klasifikaci pro:</span><span class="sxs-lookup"><span data-stu-id="663eb-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="663eb-149">Identifikujte postojích jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="663eb-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="663eb-150">E-mailu klasifikujte jako nevyžádané pošty, nevyžádanou poštou nebo funkční.</span><span class="sxs-lookup"><span data-stu-id="663eb-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="663eb-151">Určete, zda je cancerous ukázka pacientova testovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="663eb-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="663eb-152">Rozdělit kategorií podle jejich tendenci reagovat na prodejní kampaně.</span><span class="sxs-lookup"><span data-stu-id="663eb-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="663eb-153">Klasifikace úlohy jsou často jednu z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="663eb-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="663eb-154">Binární: buď A nebo B.</span><span class="sxs-lookup"><span data-stu-id="663eb-154">Binary: either A or B.</span></span>
* <span data-ttu-id="663eb-155">Multiclass: více kategorií, které můžete funkci lze použít jeden model.</span><span class="sxs-lookup"><span data-stu-id="663eb-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="663eb-156">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="663eb-156">Create a console application</span></span>

1. <span data-ttu-id="663eb-157">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="663eb-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="663eb-158">Vyberte **soubor** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="663eb-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="663eb-159">V *nový projekt*\* dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="663eb-159">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="663eb-160">Vyberte **konzolové aplikace (.NET Core)** šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="663eb-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="663eb-161">V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="663eb-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="663eb-162">Vytvořte adresář s názvem *Data* ve vašem projektu a uložte si své soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="663eb-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="663eb-163">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="663eb-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="663eb-164">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="663eb-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="663eb-165">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="663eb-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="663eb-166">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="663eb-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="663eb-167">Zvolte "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, vyhledávat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="663eb-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="663eb-168">Vyberte **OK** tlačítko **zobrazení náhledu změn** dialogové okno a potom vyberte **souhlasím** na tlačítko **přijetí licence** dialogové okno Pokud jste souhlas s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="663eb-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="663eb-169">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="663eb-169">Prepare your data</span></span>

1. <span data-ttu-id="663eb-170">Stáhnout [WikiPedia detox – 250řádku data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) a [wikipedia-detox – 250řádku test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data nastaví a uložte je do *Data* složku dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="663eb-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="663eb-171">První datovou sadu nastaví model strojového učení a druhý je možné zjistit, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="663eb-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="663eb-172">V Průzkumníku řešení klikněte pravým tlačítkem na každý z \*TSV, soubory a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="663eb-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="663eb-173">V části **Upřesnit**, změňte hodnotu **kopírovat do výstupního adresáře** k **vždy**.</span><span class="sxs-lookup"><span data-stu-id="663eb-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="663eb-174">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="663eb-174">Create classes and define paths</span></span>

<span data-ttu-id="663eb-175">Přidejte následující další `using` příkazů do horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="663eb-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="663eb-176">Potřebujete vytvořit tři globální proměnné, do kterých cestu k naposledy stažené soubory:</span><span class="sxs-lookup"><span data-stu-id="663eb-176">You need to create three global variables to hold the path to the recently downloaded files:</span></span>

* <span data-ttu-id="663eb-177">`_dataPath` nemá cestu k datové sadě použity při cvičení modelu.</span><span class="sxs-lookup"><span data-stu-id="663eb-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="663eb-178">`_testDataPath` nemá cestu k datové sadě používají k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="663eb-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="663eb-179">`_modelPath` má cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="663eb-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="663eb-180">Přidejte následující kód řádku vpravo nahoře `Main` metoda k určení naposledy stažené soubory:</span><span class="sxs-lookup"><span data-stu-id="663eb-180">Add the following code to the line right above the `Main` method to specify the recently downloaded files:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="663eb-181">Budete muset vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="663eb-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="663eb-182">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="663eb-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="663eb-183">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="663eb-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="663eb-184">V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="663eb-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="663eb-185">Pak vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="663eb-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="663eb-186">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="663eb-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="663eb-187">Přidejte následující `using` příkaz do horní části *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="663eb-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="663eb-188">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, na *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="663eb-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="663eb-189">`SentimentData` je třída vstupní datové sady a `float` (`Sentiment`), má hodnotu pro postojích kladné nebo záporné a řetězec pro komentář (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="663eb-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="663eb-190">Mají obě pole `Column` atributy připojené k nim.</span><span class="sxs-lookup"><span data-stu-id="663eb-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="663eb-191">Popisuje pořadí každé pole v datovém souboru a který je tento atribut `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="663eb-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="663eb-192">`SentimentPrediction` Třída slouží k předpovědi po modelu má cvičena.</span><span class="sxs-lookup"><span data-stu-id="663eb-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="663eb-193">Obsahuje jednu logickou hodnotu (`Sentiment`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="663eb-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="663eb-194">`Label` Se používá k vytvoření a cvičení modelu a jeho také používá s druhou datovou sadu k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="663eb-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="663eb-195">`PredictedLabel` Se používá během předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="663eb-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="663eb-196">Zkušební verze se používají vstup s Cvičná data, předpovězené hodnoty a modelu.</span><span class="sxs-lookup"><span data-stu-id="663eb-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="663eb-197">V *Program.cs* změňte `Main` podpis metody nahrazením `void` s `async Task`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="663eb-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="663eb-198">Přidání `async` k `Main` s <xref:System.Threading.Tasks.Task> návratový typ, protože ukládání modelu do souboru zip později, a program musí počkat, až po dokončení této úlohy externí.</span><span class="sxs-lookup"><span data-stu-id="663eb-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="663eb-199">*Asynchronní hlavní* metoda umožňuje používat `await` ve vaší `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="663eb-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="663eb-200">Další informace najdete v tématu [asynchronní hlavní](../../../docs/csharp/programming-guide/main-and-command-args/index.md) v Průvodci programovacího jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="663eb-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="663eb-201">Nahraďte `Console.WriteLine("Hello World!")` řádku v následujícím kódem `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="663eb-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="663eb-202">`Train` Metoda provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="663eb-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="663eb-203">Načte nebo ingestuje data.</span><span class="sxs-lookup"><span data-stu-id="663eb-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="663eb-204">Upraví a featurizes data.</span><span class="sxs-lookup"><span data-stu-id="663eb-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="663eb-205">Nastaví model.</span><span class="sxs-lookup"><span data-stu-id="663eb-205">Trains the model.</span></span>
* <span data-ttu-id="663eb-206">Předpovídá postojích na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="663eb-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="663eb-207">Vytvořte `Train` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="663eb-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static PredictionModel<SentimentData, SentimentPrediction> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="663eb-208">Zpracování příjmu dat</span><span class="sxs-lookup"><span data-stu-id="663eb-208">Ingest the data</span></span>

<span data-ttu-id="663eb-209">Inicializuje novou instanci třídy <xref:Microsoft.ML.LearningPipeline> , bude obsahovat načítání dat, zpracování dat nebo featurization a modelu.</span><span class="sxs-lookup"><span data-stu-id="663eb-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="663eb-210">Přidejte následující kód jako první řádek `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="663eb-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="663eb-211"><xref:Microsoft.ML.Data.TextLoader> Objekt představuje první část kanálu a načte data souboru školení.</span><span class="sxs-lookup"><span data-stu-id="663eb-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="663eb-212">Předběžné zpracování dat a konstruování</span><span class="sxs-lookup"><span data-stu-id="663eb-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="663eb-213">Předběžné zpracování a vyčištění dat jsou důležité úkoly, které udělat předtím, než datové sady je využívány efektivně pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="663eb-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="663eb-214">Nezpracovaná data, je často aktivní nebo nespolehlivé a může být chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="663eb-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="663eb-215">Pomocí dat bez těchto úloh modelování může vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="663eb-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="663eb-216">ML. Kanály transformace na NET umožňují vytvořit vlastní sadu transformace, které se použijí pro vaše data před cvičení nebo testování.</span><span class="sxs-lookup"><span data-stu-id="663eb-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="663eb-217">Primárním účelem transformací je data featurization.</span><span class="sxs-lookup"><span data-stu-id="663eb-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="663eb-218">Transformace kanálu výhod je, že po definice transformace kanálu, uložení kanálu a použijte ji k testování data.</span><span class="sxs-lookup"><span data-stu-id="663eb-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="663eb-219">Použít <xref:Microsoft.ML.Transforms.TextFeaturizer> převést `SentimentText` sloupce do [číselné vektoru](../resources/glossary.md#numerical-feature-vector) názvem `Features` používá algoritmus machine learning.</span><span class="sxs-lookup"><span data-stu-id="663eb-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="663eb-220">Toto je předběžné zpracování nebo featurization krok.</span><span class="sxs-lookup"><span data-stu-id="663eb-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="663eb-221">Pomocí další součásti, které jsou k dispozici v ML.NET můžete povolit lepší výsledky se svým modelem.</span><span class="sxs-lookup"><span data-stu-id="663eb-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="663eb-222">Přidat `TextFeaturizer` do kanálu jako dalším řádku kódu:</span><span class="sxs-lookup"><span data-stu-id="663eb-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="663eb-223">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="663eb-223">Choose a learning algorithm</span></span>

<span data-ttu-id="663eb-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Objekt je student stromu rozhodnutí budete používat v kanálu.</span><span class="sxs-lookup"><span data-stu-id="663eb-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="663eb-225">Podobně jako v kroku featurization vyzkoušení různých inteligentních algoritmů k dispozici v ML.NET a změna jejich parametrů vede k odlišným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="663eb-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="663eb-226">Pro ladění, můžete nastavit [hyperparameters](../resources/glossary.md#hyperparameter) jako <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, a <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span><span class="sxs-lookup"><span data-stu-id="663eb-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="663eb-227">Tyto hyperparameters jsou nastavené před nic ovlivňuje modelu a jsou specifické pro model.</span><span class="sxs-lookup"><span data-stu-id="663eb-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="663eb-228">Slouží k vyladění rozhodovací strom pro výkon, takže vyšší hodnoty může mít negativní vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="663eb-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="663eb-229">Přidejte následující kód, který `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="663eb-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="663eb-230">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="663eb-230">Train the model</span></span>

<span data-ttu-id="663eb-231">Trénování modelu, <xref:Microsoft.ML.PredictionModel%602>, na základě sady dat, která byla načtena a transformovat.</span><span class="sxs-lookup"><span data-stu-id="663eb-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="663eb-232">`pipeline.Train<SentimentData, SentimentPrediction>()` Nastaví kanál (načte data, vlaky featurizer a Student).</span><span class="sxs-lookup"><span data-stu-id="663eb-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="663eb-233">Experiment není provést, dokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="663eb-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="663eb-234">Přidejte následující kód, který `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="663eb-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="663eb-235">Uložte a vraťte se Trénink modelu pro vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="663eb-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="663eb-236">V tuto chvíli máte model, který se dá integrovat do některé z vašich aplikací .NET existující nebo nové.</span><span class="sxs-lookup"><span data-stu-id="663eb-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="663eb-237">Váš model uložit do souboru ZIP a před vrácením, přidejte následující kód na další řádek v `Train`:</span><span class="sxs-lookup"><span data-stu-id="663eb-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="663eb-238">Vrátí modelu na konci `Train` metoda.</span><span class="sxs-lookup"><span data-stu-id="663eb-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="663eb-239">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="663eb-239">Evaluate the model</span></span>

<span data-ttu-id="663eb-240">Teď, když jste vytvořili a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro zajištění kvality a ověření.</span><span class="sxs-lookup"><span data-stu-id="663eb-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="663eb-241">V `Evaluate` metoda, vytvořené v modelu `Train` je předaná k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="663eb-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="663eb-242">Vytvořte `Evaluate` metoda, hned za `Train`, jako v následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="663eb-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="663eb-243">`Evaluate` Metoda provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="663eb-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="663eb-244">Načte testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="663eb-244">Loads the test dataset.</span></span>
* <span data-ttu-id="663eb-245">Vytvoří binární vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="663eb-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="663eb-246">Vyhodnotí modelu a vytvoření metriky.</span><span class="sxs-lookup"><span data-stu-id="663eb-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="663eb-247">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="663eb-247">Displays the metrics.</span></span>

<span data-ttu-id="663eb-248">Přidejte volání do nové metody z `Main` metoda, v rámci `Train` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="663eb-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="663eb-249"><xref:Microsoft.ML.Data.TextLoader> Třída načte nová datová sada testů se stejným schématem.</span><span class="sxs-lookup"><span data-stu-id="663eb-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="663eb-250">Použití této datové sady pro kontrolu kvality modelu můžete vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="663eb-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="663eb-251">Přidejte následující kód, který `Evaluate` metoda:</span><span class="sxs-lookup"><span data-stu-id="663eb-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="663eb-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Vypočítá metriky kvality pro objekt `PredictionModel` pomocí zadané sady dat.</span><span class="sxs-lookup"><span data-stu-id="663eb-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="663eb-253">Pokud chcete zobrazit tyto metriky, přidejte vyhodnocování jako na další řádek v `Evaluate` metoda následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="663eb-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="663eb-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> Obsahuje metriky celkového vypočítávají podle binární klasifikace vyhodnocovací filtry.</span><span class="sxs-lookup"><span data-stu-id="663eb-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="663eb-255">Pokud chcete zobrazit tyto k určení kvality modelu, potřebujete získat metriky první.</span><span class="sxs-lookup"><span data-stu-id="663eb-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="663eb-256">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="663eb-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="663eb-257">Zobrazení metriky pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="663eb-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="663eb-258">Zobrazování metrik, sdílet výsledky a potom s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="663eb-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="663eb-259">Předpověď výstupy testovací data s modelem</span><span class="sxs-lookup"><span data-stu-id="663eb-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="663eb-260">Vytvořte `Predict` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="663eb-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="663eb-261">`Predict` Metoda provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="663eb-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="663eb-262">Vytvoří testovací data.</span><span class="sxs-lookup"><span data-stu-id="663eb-262">Creates test data.</span></span>
* <span data-ttu-id="663eb-263">Předpovídá postojích na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="663eb-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="663eb-264">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="663eb-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="663eb-265">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="663eb-265">Displays the predicted results.</span></span>

<span data-ttu-id="663eb-266">Přidejte volání do nové metody z `Main` metoda, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="663eb-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="663eb-267">Přidání některé komentářů k testování pro cvičný model predikce v `Predict` metoda:</span><span class="sxs-lookup"><span data-stu-id="663eb-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="663eb-268">Teď, když máte model, můžete pomocí nich předpovědi kladné a záporné postojích komentář dat pomocí <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="663eb-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="663eb-269">Chcete-li získat předpovědi, použijte `Predict` na nová data.</span><span class="sxs-lookup"><span data-stu-id="663eb-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="663eb-270">Upozorňujeme, že se vstupní data je řetězec a tento model zahrnuje featurization.</span><span class="sxs-lookup"><span data-stu-id="663eb-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="663eb-271">Vaše kanálu se synchronizuje během školení a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="663eb-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="663eb-272">Neměly napsat kód předběžného zpracování nebo featurization speciálně pro předpovědi a rozhraní API stejné postará batch a jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="663eb-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="663eb-273">Model operationalization: předpovědi</span><span class="sxs-lookup"><span data-stu-id="663eb-273">Model operationalization: prediction</span></span>

<span data-ttu-id="663eb-274">Zobrazení `SentimentText` a odpovídající postojích předpovědi, aby bylo možné sdílet výsledky a s nimi pracovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="663eb-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="663eb-275">Tomu se říká operationalization, pomocí vrácená data v rámci provozní zásady.</span><span class="sxs-lookup"><span data-stu-id="663eb-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="663eb-276">Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="663eb-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="663eb-277">Před zobrazením předpokládaných výsledky, zkombinovat postojích předpovědi společně zobrazíte původní komentář s jeho předpokládaných postojích.</span><span class="sxs-lookup"><span data-stu-id="663eb-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="663eb-278">Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda toho docílit, další proto přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="663eb-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="663eb-279">Teď, když jste kombinaci `SentimentText` a `Sentiment` do tříd, můžete zobrazit pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metoda:</span><span class="sxs-lookup"><span data-stu-id="663eb-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="663eb-280">Protože odvodit, že jsou názvy elementu řazené kolekce členů, že je nová funkce v C# 7.1 a výchozí jazykovou verzi projektu C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="663eb-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="663eb-281">To lze provést, klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="663eb-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="663eb-282">Vyberte **sestavení** a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="663eb-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="663eb-283">V rozevírací nabídce, a vyberte **C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="663eb-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="663eb-284">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="663eb-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="663eb-285">Výsledky</span><span class="sxs-lookup"><span data-stu-id="663eb-285">Results</span></span>

<span data-ttu-id="663eb-286">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="663eb-286">Your results should be similar to the following.</span></span> <span data-ttu-id="663eb-287">Jako kanálu zpracovává, zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="663eb-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="663eb-288">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="663eb-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="663eb-289">Tyto byly odebrány z následující výsledky pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="663eb-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="663eb-290">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="663eb-290">Congratulations!</span></span> <span data-ttu-id="663eb-291">Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a predikci postojích zprávy.</span><span class="sxs-lookup"><span data-stu-id="663eb-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="663eb-292">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="663eb-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="663eb-293">Další kroky</span><span class="sxs-lookup"><span data-stu-id="663eb-293">Next steps</span></span>

<span data-ttu-id="663eb-294">V tomto kurzu jste se dozvěděli, jak:</span><span class="sxs-lookup"><span data-stu-id="663eb-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="663eb-295">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="663eb-295">Understand the problem</span></span>
> * <span data-ttu-id="663eb-296">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="663eb-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="663eb-297">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="663eb-297">Prepare your data</span></span>
> * <span data-ttu-id="663eb-298">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="663eb-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="663eb-299">Načíst třídění</span><span class="sxs-lookup"><span data-stu-id="663eb-299">Load a classifier</span></span>
> * <span data-ttu-id="663eb-300">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="663eb-300">Train the model</span></span>
> * <span data-ttu-id="663eb-301">Vyhodnocení modelu s jinou datové sady</span><span class="sxs-lookup"><span data-stu-id="663eb-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="663eb-302">Předpověď výstupy testovací data s modelem</span><span class="sxs-lookup"><span data-stu-id="663eb-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="663eb-303">Přechodu na další informace v dalším kurzu</span><span class="sxs-lookup"><span data-stu-id="663eb-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="663eb-304">Předpověď taxíkem tarif</span><span class="sxs-lookup"><span data-stu-id="663eb-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
