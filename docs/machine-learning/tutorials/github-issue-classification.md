---
title: V případě GitHub problém klasifikace víc tříd použít ML.NET
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy Githubu pro jejich přiřazení k dané oblasti.
ms.date: 01/22/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3983fe1dae98deb485585cb3b3868bdbb68c8c39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746681"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="60536-103">Kurz: Použijte ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy s úložištěm GitHub.</span><span class="sxs-lookup"><span data-stu-id="60536-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues.</span></span>

<span data-ttu-id="60536-104">Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru problém Githubu prostřednictvím aplikace konzoly .NET Core using C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="60536-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="60536-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="60536-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="60536-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="60536-106">Understand the problem</span></span>
> * <span data-ttu-id="60536-107">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="60536-107">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="60536-108">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="60536-108">Prepare your data</span></span>
> * <span data-ttu-id="60536-109">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="60536-109">Create the learning pipeline</span></span>
> * <span data-ttu-id="60536-110">Načíst třídění</span><span class="sxs-lookup"><span data-stu-id="60536-110">Load a classifier</span></span>
> * <span data-ttu-id="60536-111">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="60536-111">Train the model</span></span>
> * <span data-ttu-id="60536-112">Vyhodnocení modelu s jinou datovou sadu</span><span class="sxs-lookup"><span data-stu-id="60536-112">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="60536-113">Předpověď jednu instanci data výsledek testu s modelem</span><span class="sxs-lookup"><span data-stu-id="60536-113">Predict a single instance of test data outcome with the model</span></span>
> * <span data-ttu-id="60536-114">Předpověď výsledků dat testu se načíst model</span><span class="sxs-lookup"><span data-stu-id="60536-114">Predict the test data outcomes with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="60536-115">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="60536-115">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="60536-116">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="60536-116">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="60536-117">Přehled ukázky problém Githubu</span><span class="sxs-lookup"><span data-stu-id="60536-117">GitHub issue sample overview</span></span>

<span data-ttu-id="60536-118">Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje popisek oblasti pro problém na Githubu.</span><span class="sxs-lookup"><span data-stu-id="60536-118">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="60536-119">Vyhodnocuje také model s druhou datové sady pro analýzy kvality.</span><span class="sxs-lookup"><span data-stu-id="60536-119">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="60536-120">Problém datové sady jsou v úložišti dotnet/corefx Githubu.</span><span class="sxs-lookup"><span data-stu-id="60536-120">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="60536-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60536-121">Prerequisites</span></span>

* <span data-ttu-id="60536-122">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="60536-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="60536-123">[Githubu problémy s daty oddělenými tabulátory souboru (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="60536-123">The [Github issues tab separated file (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="60536-124">[Problémy Githubu testovací soubor oddělených tabulátory (issues_test.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="60536-124">The [Github issues test tab separated file (issues_test.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="60536-125">Pracovní postup Machine learning</span><span class="sxs-lookup"><span data-stu-id="60536-125">Machine learning workflow</span></span>

<span data-ttu-id="60536-126">V tomto kurzu se řídí strojového učení pracovního postupu, který umožňuje přesunout řádný proces.</span><span class="sxs-lookup"><span data-stu-id="60536-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="60536-127">Fáze pracovního postupu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="60536-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="60536-128">**Pochopení problému**</span><span class="sxs-lookup"><span data-stu-id="60536-128">**Understand the problem**</span></span>
2. <span data-ttu-id="60536-129">**Příprava dat**</span><span class="sxs-lookup"><span data-stu-id="60536-129">**Prepare your data**</span></span>
   * <span data-ttu-id="60536-130">**Načtení dat**</span><span class="sxs-lookup"><span data-stu-id="60536-130">**Load the data**</span></span>
   * <span data-ttu-id="60536-131">**Extrakce funkce (transformovat data)**</span><span class="sxs-lookup"><span data-stu-id="60536-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="60536-132">**Sestavení a trénování**</span><span class="sxs-lookup"><span data-stu-id="60536-132">**Build and train**</span></span> 
   * <span data-ttu-id="60536-133">**Trénování modelu**</span><span class="sxs-lookup"><span data-stu-id="60536-133">**Train the model**</span></span>
   * <span data-ttu-id="60536-134">**Vyhodnocení modelu**</span><span class="sxs-lookup"><span data-stu-id="60536-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="60536-135">**Spuštění**</span><span class="sxs-lookup"><span data-stu-id="60536-135">**Run**</span></span>
   * <span data-ttu-id="60536-136">**Využití modelu**</span><span class="sxs-lookup"><span data-stu-id="60536-136">**Model consumption**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="60536-137">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="60536-137">Understand the problem</span></span>

<span data-ttu-id="60536-138">Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="60536-139">Popis vnitřních principů problému můžete předpovídat a vyhodnoťte výsledky.</span><span class="sxs-lookup"><span data-stu-id="60536-139">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="60536-140">Problém pro účely tohoto kurzu je pochopit, co příchozí problémy Githubu oblasti patří aby bylo možné správně popisek pro stanovení priorit a plánování.</span><span class="sxs-lookup"><span data-stu-id="60536-140">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="60536-141">Problém můžete rozdělit takto:</span><span class="sxs-lookup"><span data-stu-id="60536-141">You can break down the problem to the following:</span></span>

* <span data-ttu-id="60536-142">text nadpisu problém</span><span class="sxs-lookup"><span data-stu-id="60536-142">the issue title text</span></span>
* <span data-ttu-id="60536-143">popis problému</span><span class="sxs-lookup"><span data-stu-id="60536-143">the issue description text</span></span>
* <span data-ttu-id="60536-144">hodnotu oblasti pro trénovací data modelu</span><span class="sxs-lookup"><span data-stu-id="60536-144">an area value for the model training data</span></span>
* <span data-ttu-id="60536-145">Předpokládaná oblasti hodnotu, kterou můžete vyhodnotit a pak použít provozně</span><span class="sxs-lookup"><span data-stu-id="60536-145">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="60536-146">Potom budete potřebovat **určit** oblast, která vám pomůže s strojového učení výběr úkolů.</span><span class="sxs-lookup"><span data-stu-id="60536-146">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="60536-147">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="60536-147">Select the appropriate machine learning task</span></span>

<span data-ttu-id="60536-148">Tento problém víte, k následujícím skutečnostem:</span><span class="sxs-lookup"><span data-stu-id="60536-148">With this problem, you know the following facts:</span></span>

<span data-ttu-id="60536-149">Cvičná data:</span><span class="sxs-lookup"><span data-stu-id="60536-149">Training data:</span></span>

<span data-ttu-id="60536-150">Problémy Githubu můžete označené v několika oblastech (**oblasti**) jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="60536-150">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="60536-151">area-System.Numerics</span><span class="sxs-lookup"><span data-stu-id="60536-151">area-System.Numerics</span></span>
* <span data-ttu-id="60536-152">area-System.Xml</span><span class="sxs-lookup"><span data-stu-id="60536-152">area-System.Xml</span></span>
* <span data-ttu-id="60536-153">oblasti infrastruktury</span><span class="sxs-lookup"><span data-stu-id="60536-153">area-Infrastructure</span></span>
* <span data-ttu-id="60536-154">area-System.Linq</span><span class="sxs-lookup"><span data-stu-id="60536-154">area-System.Linq</span></span>
* <span data-ttu-id="60536-155">System.IO oblasti</span><span class="sxs-lookup"><span data-stu-id="60536-155">area-System.IO</span></span>

<span data-ttu-id="60536-156">Předpověď **oblasti** z nový problém Githubu například v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="60536-156">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="60536-157">Vs Contract.Assert Debug.Assert –</span><span class="sxs-lookup"><span data-stu-id="60536-157">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="60536-158">Nastavte pole jen pro čtení v System.Xml</span><span class="sxs-lookup"><span data-stu-id="60536-158">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="60536-159">Úloha klasifikace machine learning je nejvhodnější pro tento scénář.</span><span class="sxs-lookup"><span data-stu-id="60536-159">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="60536-160">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="60536-160">About the classification task</span></span>

<span data-ttu-id="60536-161">Klasifikace je úloha strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky.</span><span class="sxs-lookup"><span data-stu-id="60536-161">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="60536-162">Například můžete použít klasifikace:</span><span class="sxs-lookup"><span data-stu-id="60536-162">For example, you can use classification to:</span></span>

* <span data-ttu-id="60536-163">Zjistit mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="60536-163">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="60536-164">E-mailu klasifikujte jako spam nevyžádané nebo funkční.</span><span class="sxs-lookup"><span data-stu-id="60536-164">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="60536-165">Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="60536-165">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="60536-166">Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.</span><span class="sxs-lookup"><span data-stu-id="60536-166">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="60536-167">Úlohy klasifikace jsou často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="60536-167">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="60536-168">Binární soubor: buď A a B.</span><span class="sxs-lookup"><span data-stu-id="60536-168">Binary: either A or B.</span></span>
* <span data-ttu-id="60536-169">Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-169">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="60536-170">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="60536-170">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="60536-171">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="60536-171">Create a project</span></span>

1. <span data-ttu-id="60536-172">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="60536-172">Open Visual Studio 2017.</span></span> <span data-ttu-id="60536-173">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="60536-173">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="60536-174">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="60536-174">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="60536-175">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="60536-175">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="60536-176">V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="60536-176">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="60536-177">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="60536-177">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="60536-178">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="60536-178">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="60536-179">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="60536-179">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="60536-180">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="60536-180">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="60536-181">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="60536-181">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="60536-182">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="60536-182">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="60536-183">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="60536-183">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="60536-184">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="60536-184">Prepare your data</span></span>

1. <span data-ttu-id="60536-185">Stáhněte si [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka.</span><span class="sxs-lookup"><span data-stu-id="60536-185">Download the [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="60536-186">První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="60536-186">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="60536-187">V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="60536-187">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="60536-188">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="60536-188">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="60536-189">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="60536-189">Create classes and define paths</span></span>

<span data-ttu-id="60536-190">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="60536-190">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="60536-191">Je potřeba vytvořit tři globální pole pro uložení cest k naposledy stažené soubory a globální proměnné pro `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="60536-191">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="60536-192">`_trainDataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-192">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="60536-193">`_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-193">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="60536-194">`_modelPath` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-194">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="60536-195">`_mlContext` je <xref:Microsoft.ML.MLContext> , která poskytuje kontext zpracování.</span><span class="sxs-lookup"><span data-stu-id="60536-195">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="60536-196">`_trainingDataView` je <xref:Microsoft.ML.Data.IDataView> používají ke zpracování trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="60536-196">`_trainingDataView` is the <xref:Microsoft.ML.Data.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="60536-197">`_predEngine` je <xref:Microsoft.ML.PredictionEngine%602> používá pro jeden předpovědi.</span><span class="sxs-lookup"><span data-stu-id="60536-197">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="60536-198">`_reader` je <xref:Microsoft.ML.Data.TextLoader> lze načíst a transformovat datové sady.</span><span class="sxs-lookup"><span data-stu-id="60536-198">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="60536-199">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="60536-199">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="60536-200">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="60536-200">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="60536-201">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="60536-201">Add a new class to your project:</span></span>

1. <span data-ttu-id="60536-202">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="60536-202">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="60536-203">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="60536-203">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="60536-204">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="60536-204">Then, select the **Add** button.</span></span>

    <span data-ttu-id="60536-205">*GitHubIssueData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="60536-205">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="60536-206">Přidejte následující `using` příkaz do horní části *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="60536-206">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="60536-207">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, možnosti *GitHubIssueData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="60536-207">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="60536-208">`GitHubIssue` je třída vstupní datová sada a má následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="60536-208">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="60536-209">`ID` obsahuje hodnotu pro ID problému Githubu</span><span class="sxs-lookup"><span data-stu-id="60536-209">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="60536-210">`Area` obsahuje hodnotu `Area` popisek</span><span class="sxs-lookup"><span data-stu-id="60536-210">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="60536-211">`Title` obsahuje název problému Githubu</span><span class="sxs-lookup"><span data-stu-id="60536-211">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="60536-212">`Description` obsahuje popis problému Githubu</span><span class="sxs-lookup"><span data-stu-id="60536-212">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="60536-213">`IssuePrediction` Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="60536-213">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="60536-214">Má jediný `string` (`Area`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="60536-214">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="60536-215">`Label` Slouží k vytvoření a trénování modelu a jeho datové sady druhé použít také k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-215">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="60536-216">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="60536-216">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="60536-217">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="60536-217">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="60536-218">Při vytváření modelu s ML.NET, začněte vytvořením <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="60536-218">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="60536-219">Toto je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="60536-219">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="60536-220">Prostředí poskytuje kontext pro vaši úlohu ML, který lze použít pro sledování a protokolování výjimek.</span><span class="sxs-lookup"><span data-stu-id="60536-220">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="60536-221">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="60536-221">Initialize variables in Main</span></span>

<span data-ttu-id="60536-222">Inicializovat `_mlContext` globální proměnnou s novou instanci třídy `MLContext` s náhodná počáteční hodnota (`seed: 0`) pro opakovatelné/deterministické výsledky napříč více školení.</span><span class="sxs-lookup"><span data-stu-id="60536-222">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="60536-223">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-223">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="60536-224">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="60536-224">Load the data</span></span>

<span data-ttu-id="60536-225">V dalším kroku inicializovat `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> globální proměnné a načtení dat pomocí `_trainDataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="60536-225">Next, initialize the `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="60536-226">Jako vstup a výstup `Transforms`, `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="60536-226">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="60536-227">Data jsou v ML.NET, podobně jako `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="60536-227">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="60536-228">Je laxně Vyhodnocená schematizovanými a heterogenní.</span><span class="sxs-lookup"><span data-stu-id="60536-228">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="60536-229">Objekt představuje první část kanálu a načte data.</span><span class="sxs-lookup"><span data-stu-id="60536-229">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="60536-230">Pro účely tohoto kurzu načte datovou sadu s problém názvy, popisy a odpovídající oblasti Githubu popisek.</span><span class="sxs-lookup"><span data-stu-id="60536-230">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="60536-231">`DataView` Slouží k vytvoření a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-231">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="60536-232">Od dříve vytvořeného `GitHubIssue` typ modelu dat odpovídá schématu datové sady, inicializace, mapování a datová sada načítání do jednoho řádku kódu lze kombinovat.</span><span class="sxs-lookup"><span data-stu-id="60536-232">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="60536-233">První část řádku (`CreateTextReader<GitHubIssue>(hasHeader: true)`) vytvoří <xref:Microsoft.ML.Data.TextLoader> podle odvozování schématu datové sady z `GitHubIssue` datového modelu, typu a pomocí hlavičky datové sady.</span><span class="sxs-lookup"><span data-stu-id="60536-233">The first part of the line (`CreateTextReader<GitHubIssue>(hasHeader: true)`) creates a <xref:Microsoft.ML.Data.TextLoader> by inferencing the dataset schema from the `GitHubIssue` data model type and using the dataset header.</span></span>

<span data-ttu-id="60536-234">Definujete schéma dat dříve při vytváření `GitHubIssue` třídy.</span><span class="sxs-lookup"><span data-stu-id="60536-234">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="60536-235">Pro schéma:</span><span class="sxs-lookup"><span data-stu-id="60536-235">For your schema:</span></span>

* <span data-ttu-id="60536-236">první sloupec `ID` (ID problému Githubu)</span><span class="sxs-lookup"><span data-stu-id="60536-236">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="60536-237">druhý sloupec `Area` (Předpověď pro školení)</span><span class="sxs-lookup"><span data-stu-id="60536-237">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="60536-238">třetí sloupec `Title` (název problému Githubu) je prvním [funkce](../resources/glossary.md##feature) používá pro predikci `Area`</span><span class="sxs-lookup"><span data-stu-id="60536-238">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="60536-239">čtvrtý sloupec `Description` je druhá funkce používá pro predikci `Area`</span><span class="sxs-lookup"><span data-stu-id="60536-239">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="60536-240">Druhá část řádku (`.Read(_trainDataPath)`) používá <xref:Microsoft.ML.Data.TextLoader.Read%2A> metoda načíst text školení soubor pomocí `_trainDataPath` do `IDataView` (`_trainingDataView`) globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="60536-240">The second part of the line  (`.Read(_trainDataPath)`) uses <xref:Microsoft.ML.Data.TextLoader.Read%2A> method to load the training text file using `_trainDataPath` into the `IDataView` (`_trainingDataView`) global variable.</span></span>  

<span data-ttu-id="60536-241">K inicializaci a načíst `_trainingDataView` globální proměnné, aby bylo možné používat pro kanál, přidejte následující kód za `mlContext` inicializace:</span><span class="sxs-lookup"><span data-stu-id="60536-241">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


<span data-ttu-id="60536-242">Přidejte následující položky jako další řádek kódu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-242">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="60536-243">`ProcessData` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="60536-243">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="60536-244">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="60536-244">Extracts and transforms the data.</span></span>
* <span data-ttu-id="60536-245">Vrátí kanálu zpracování.</span><span class="sxs-lookup"><span data-stu-id="60536-245">Returns the processing pipeline.</span></span>

<span data-ttu-id="60536-246">Vytvořte `ProcessData` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-246">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="60536-247">Extrahovat a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="60536-247">Extract and transform the data</span></span>

<span data-ttu-id="60536-248">Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="60536-248">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="60536-249">Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="60536-249">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="60536-250">Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="60536-250">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="60536-251">ML. Kanály transformace vaší sítě vytvořit vlastní sadu transformací, které se použijí pro vaše data před trénování a testování.</span><span class="sxs-lookup"><span data-stu-id="60536-251">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="60536-252">Hlavním účelem transformace jsou data [snadné](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="60536-252">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="60536-253">Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) data, abyste dalším krokem je získat z našich algoritmů ML rozpoznat formát naše textová data.</span><span class="sxs-lookup"><span data-stu-id="60536-253">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="60536-254">Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="60536-254">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="60536-255">V dalších krocích, budeme odkazovat na sloupce pomocí názvy definované v `GitHubIssue` třídy.</span><span class="sxs-lookup"><span data-stu-id="60536-255">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="60536-256">Když je model trénují a vyhodnocují, ve výchozím nastavení, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat.</span><span class="sxs-lookup"><span data-stu-id="60536-256">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="60536-257">Jelikož chceme předpovědět popisek oblasti Githubu pro `GitHubIssue`, kopie `Area` sloupce do **popisek** sloupec.</span><span class="sxs-lookup"><span data-stu-id="60536-257">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="60536-258">Chcete-li to mohli udělat, použijte `MLContext.Transforms.Conversion.MapValueToKey`, který tvoří obálku pro <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="60536-258">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="60536-259">`MapValueToKey` Vrátí <xref:Microsoft.ML.Data.EstimatorChain%601> efektivně, který bude kanál.</span><span class="sxs-lookup"><span data-stu-id="60536-259">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="60536-260">Pojmenujte toto `pipeline` jako se pak připojí trainer k `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="60536-260">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="60536-261">Přidáte jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-261">Add this as the next line of code:</span></span>

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="60536-262">Algoritmus, který trénovat modelu vyžaduje **číselné** volání funkcí, abyste získali další, `mlContext.Transforms.Text.FeaturizeText` které featurizes text (`Title` a `Description`) sloupce jako číselné vektor pro každou volá `TitleFeaturized` a `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="60536-262">The algorithm that trains the model requires **numeric** features, so you have Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="60536-263">Featurizing přiřadí různé číselné hodnoty klíče na různé hodnoty v každém sloupci a je používán algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="60536-263">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span>
<span data-ttu-id="60536-264">Snadné pro oba sloupce pro přidání do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="60536-264">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="60536-265">Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce `Concatenate` třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="60536-265">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="60536-266">Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="60536-266">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="60536-267">Připojte tuto transformaci na kanál s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="60536-267">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="60536-268">V dalším kroku připojit <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> pro ukládání do mezipaměti DataView, takže při iteraci přes data s využitím více než jednou mezipaměti může dosahovat vyšších výkonů, stejně jako u následujícího kódu</span><span class="sxs-lookup"><span data-stu-id="60536-268">Next, append a <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code</span></span>

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

<span data-ttu-id="60536-269">Kanál na konci vrátit `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="60536-269">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="60536-270">Tento krok zpracovává předběžného zpracování a snadné.</span><span class="sxs-lookup"><span data-stu-id="60536-270">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="60536-271">Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.</span><span class="sxs-lookup"><span data-stu-id="60536-271">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="60536-272">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="60536-272">Build and train the model</span></span>

<span data-ttu-id="60536-273">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-273">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="60536-274">`BuildAndTrainModel` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="60536-274">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="60536-275">Vytvoří třídu algoritmus školení.</span><span class="sxs-lookup"><span data-stu-id="60536-275">Creates the training algorithm class.</span></span>
* <span data-ttu-id="60536-276">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-276">Trains the model.</span></span>
* <span data-ttu-id="60536-277">Předpovídá oblasti založené na trénovací data.</span><span class="sxs-lookup"><span data-stu-id="60536-277">Predicts area based on training data.</span></span>
* <span data-ttu-id="60536-278">Uloží model, který má `.zip` souboru.</span><span class="sxs-lookup"><span data-stu-id="60536-278">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="60536-279">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="60536-279">Returns the model.</span></span>

<span data-ttu-id="60536-280">Vytvořte `BuildAndTrainModel` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-280">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static void BuildAndTrainModel()
{

}
```

<span data-ttu-id="60536-281">Všimněte si, že dva parametry jsou předány do metody BuildAndTrainModel; `IDataView` pro trénovací datové sady (`trainingDataView`) a <xref:Microsoft.ML.Data.EstimatorChain%601> pro zpracování kanálu, který vytvořili v ProcessData (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="60536-281">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="60536-282">Přidejte následující kód jako první řádek `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-282">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-trainer-algorithm"></a><span data-ttu-id="60536-283">Vyberte algoritmus trainer</span><span class="sxs-lookup"><span data-stu-id="60536-283">Choose a trainer algorithm</span></span>

<span data-ttu-id="60536-284">Chcete-li přidat algoritmus trainer, zavolejte `mlContext.Transforms.Text.FeaturizeText` obalující metodu, která vrátí hodnotu <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> objektu.</span><span class="sxs-lookup"><span data-stu-id="60536-284">To add the trainer algorithm, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span> <span data-ttu-id="60536-285">Toto je learner stromu rozhodnutí, které budete používat v tomto kanálu.</span><span class="sxs-lookup"><span data-stu-id="60536-285">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="60536-286">`SdcaMultiClassTrainer` Se připojí `pipeline` a přijímá natrénuje `Title` a `Description` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="60536-286">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="60536-287">Přidejte následující kód, který `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-287">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[SdcaMultiClassTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SdcaMultiClassTrainer)]

<span data-ttu-id="60536-288">Teď, když jste vytvořili trainer algoritmus, připojte ho k `pipeline`.</span><span class="sxs-lookup"><span data-stu-id="60536-288">Now that you've created a trainer algorithm, append it to the `pipeline`.</span></span> <span data-ttu-id="60536-289">Potřebujete také mapovat popisku na hodnotu, která vrátí k původnímu čitelné.</span><span class="sxs-lookup"><span data-stu-id="60536-289">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="60536-290">Proveďte obě tyto akce s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="60536-290">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="60536-291">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="60536-291">Train the model</span></span>

<span data-ttu-id="60536-292">Trénování modelu, <xref:Microsoft.ML.Data.TransformerChain%601>založená na datovou sadu, která má načíst a transformovat.</span><span class="sxs-lookup"><span data-stu-id="60536-292">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="60536-293">Po definování odhadu tréninku modelu pomocí <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> současně už načtený trénovací data.</span><span class="sxs-lookup"><span data-stu-id="60536-293">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="60536-294">Vrátí model pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="60536-294">This returns a model to use for predictions.</span></span> <span data-ttu-id="60536-295">`trainingPipeline.Fit()` trénovat kanálu a vrátí `Transformer` na základě `DataView` předán.</span><span class="sxs-lookup"><span data-stu-id="60536-295">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="60536-296">Experiment není spuštěn, dokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="60536-296">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="60536-297">Přidejte následující kód, který `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-297">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="60536-298">Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, je potřeba k předpovědím na jednotlivé příklady o velmi běžný scénář produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="60536-298">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="60536-299"><xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="60536-299">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="60536-300">Přidejte následující kód k vytvoření `PredictionEngine` jako další řádek `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-300">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="60536-301">Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="60536-301">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="60536-302">Který můžete použít k předpovědi `Area` popisek jednu instanci data problém.</span><span class="sxs-lookup"><span data-stu-id="60536-302">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="60536-303">Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data.</span><span class="sxs-lookup"><span data-stu-id="60536-303">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="60536-304">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="60536-304">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="60536-305">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="60536-305">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="60536-306">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="60536-306">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="60536-307">Operacionalizace modelu: předpověď</span><span class="sxs-lookup"><span data-stu-id="60536-307">Model operationalization: prediction</span></span>

<span data-ttu-id="60536-308">Zobrazení `GitHubIssue` a odpovídající `Area` popisek predikcí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="60536-308">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="60536-309">Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady.</span><span class="sxs-lookup"><span data-stu-id="60536-309">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="60536-310">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-310">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="60536-311">Uložte a vraťte se, že model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="60536-311">Save and return the model trained to use for evaluation</span></span>

<span data-ttu-id="60536-312">V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain%601> , který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="60536-312">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="60536-313">Uložte soubor .zip trénovaného modelu, přidejte následující kód k volání `SaveModelAsFile` metody jako další řádek v `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="60536-313">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

<span data-ttu-id="60536-314">Model na konci vrátit `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="60536-314">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="60536-315">Uložit jako soubor a.zip model</span><span class="sxs-lookup"><span data-stu-id="60536-315">Save the model as a.zip file</span></span>

<span data-ttu-id="60536-316">Vytvořte `SaveModelAsFile` metoda, hned za `BuildAndTrainModel` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-316">Create the `SaveModelAsFile` method, just after the `BuildAndTrainModel` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="60536-317">`SaveModelAsFile` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="60536-317">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="60536-318">Uloží modelu ve formě souboru .zip.</span><span class="sxs-lookup"><span data-stu-id="60536-318">Saves the model as a .zip file.</span></span>

<span data-ttu-id="60536-319">Dále vytvořte metodu k uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="60536-319">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="60536-320">`ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="60536-320">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="60536-321">Uložit jako soubor zip, vytvoříte `FileStream` bezprostředně před volání `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="60536-321">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="60536-322">Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="60536-322">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="60536-323">Může také zobrazit, kde soubor byl zapsán napsáním zprávu konzoly `_modelPath`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-323">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="60536-324">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="60536-324">Evaluate the model</span></span>

<span data-ttu-id="60536-325">Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování.</span><span class="sxs-lookup"><span data-stu-id="60536-325">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="60536-326">V `Evaluate` metody, vytvořené v modelu `BuildAndTrainModel` předaný k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="60536-326">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="60536-327">Vytvořte `Evaluate` metoda, hned za `BuildAndTrainModel`, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-327">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="60536-328">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="60536-328">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="60536-329">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="60536-329">Loads the test dataset.</span></span>
* <span data-ttu-id="60536-330">Vytvoří víc tříd Chyba při vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="60536-330">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="60536-331">Vyhodnotí modelu a vytvoření metriky.</span><span class="sxs-lookup"><span data-stu-id="60536-331">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="60536-332">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="60536-332">Displays the metrics.</span></span>

<span data-ttu-id="60536-333">Přidejte volání do nové metody z `Main` metody, v rámci `BuildAndTrainModel` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-333">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="60536-334">Stejně jako dříve trénovací datové sady, můžete kombinovat inicializace, mapování a otestovat datovou sadu načítání do jednoho řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="60536-334">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="60536-335">Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality.</span><span class="sxs-lookup"><span data-stu-id="60536-335">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="60536-336">Přidejte následující kód, který `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="60536-336">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="60536-337">`MulticlassClassificationContext.Evaluate` Tvoří obálku pro <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> metodu, která vypočítá metrik kvality pro model pomocí zadaného objektu dataset.</span><span class="sxs-lookup"><span data-stu-id="60536-337">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="60536-338">Vrátí <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení klasifikace víc tříd.</span><span class="sxs-lookup"><span data-stu-id="60536-338">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="60536-339">Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první.</span><span class="sxs-lookup"><span data-stu-id="60536-339">To display these to determine the quality of the model, you need to get the metrics first.</span></span>
<span data-ttu-id="60536-340">Všimněte si použití `Transform` metoda služby machine learning `_trainedModel` globální proměnné (transformace) k zadání funkce a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="60536-340">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="60536-341">Přidejte následující kód, který `Evaluate` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="60536-341">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="60536-342">Klasifikace víc tříd, se vyhodnotí následující metriky:</span><span class="sxs-lookup"><span data-stu-id="60536-342">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="60536-343">Micro přesnost – každá dvojice ukázkovou třídu přispívá stejně metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="60536-343">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="60536-344">Chcete, aby Micro přesnost, aby byly co nejblíže 1 nejvíce.</span><span class="sxs-lookup"><span data-stu-id="60536-344">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="60536-345">Přesnost – makro – každá třída přispívá stejně metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="60536-345">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="60536-346">Třídy minority disponují stejnou váhu jako větší třídy.</span><span class="sxs-lookup"><span data-stu-id="60536-346">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="60536-347">Chcete, aby byly co nejblíže 1 nejvíce přesnost – makro.</span><span class="sxs-lookup"><span data-stu-id="60536-347">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="60536-348">Protokol ztrát – naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="60536-348">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="60536-349">Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="60536-349">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="60536-350">Od ztráty protokolu snížení - [-inf, 100], kde 100 je ideální předpovědi a 0 označuje střední předpovědi.</span><span class="sxs-lookup"><span data-stu-id="60536-350">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="60536-351">Chcete, aby omezení ztráty protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="60536-351">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="60536-352">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="60536-352">Displaying the metrics for model validation</span></span>

<span data-ttu-id="60536-353">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="60536-353">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="60536-354">Předpověď data výsledek testu s modelem uložené</span><span class="sxs-lookup"><span data-stu-id="60536-354">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="60536-355">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-355">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="60536-356">Vytvořte `PredictIssue` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-356">Create the `PredictIssue` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="60536-357">`PredictIssue` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="60536-357">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="60536-358">Vytvoří jen jeden problém testovací data.</span><span class="sxs-lookup"><span data-stu-id="60536-358">Creates a single issue of test data.</span></span>
* <span data-ttu-id="60536-359">Předpovídá oblasti na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="60536-359">Predicts Area based on test data.</span></span>
* <span data-ttu-id="60536-360">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="60536-360">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="60536-361">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="60536-361">Displays the predicted results.</span></span>

<span data-ttu-id="60536-362">Nejdřív načtěte model, který jste si předtím uložili následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="60536-362">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="60536-363">Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="60536-363">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="60536-364">Teď, když máte model, který můžete použít k predikci popisek oblasti Githubu jedné instance dat problém Githubu.</span><span class="sxs-lookup"><span data-stu-id="60536-364">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="60536-365">Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data.</span><span class="sxs-lookup"><span data-stu-id="60536-365">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="60536-366">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="60536-366">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="60536-367">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="60536-367">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="60536-368">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="60536-368">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="60536-369">Přidejte následující kód, který `PredictIssue` metodu předpovědí:</span><span class="sxs-lookup"><span data-stu-id="60536-369">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="60536-370">Operacionalizace modelu: předpověď</span><span class="sxs-lookup"><span data-stu-id="60536-370">Model operationalization: prediction</span></span>

<span data-ttu-id="60536-371">Zobrazení `Area` kategorizace problém a příslušně na ně reagovat na něj.</span><span class="sxs-lookup"><span data-stu-id="60536-371">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="60536-372">Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady.</span><span class="sxs-lookup"><span data-stu-id="60536-372">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="60536-373">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="60536-373">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="60536-374">Výsledky</span><span class="sxs-lookup"><span data-stu-id="60536-374">Results</span></span>

<span data-ttu-id="60536-375">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="60536-375">Your results should be similar to the following.</span></span> <span data-ttu-id="60536-376">Při zpracování kanálu zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="60536-376">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="60536-377">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="60536-377">You may see warnings, or processing messages.</span></span> <span data-ttu-id="60536-378">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="60536-378">These have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="60536-379">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="60536-379">Congratulations!</span></span> <span data-ttu-id="60536-380">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat popisek oblasti pro problém na Githubu.</span><span class="sxs-lookup"><span data-stu-id="60536-380">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="60536-381">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.</span><span class="sxs-lookup"><span data-stu-id="60536-381">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="60536-382">Další kroky</span><span class="sxs-lookup"><span data-stu-id="60536-382">Next steps</span></span>

<span data-ttu-id="60536-383">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="60536-383">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="60536-384">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="60536-384">Understand the problem</span></span>
> * <span data-ttu-id="60536-385">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="60536-385">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="60536-386">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="60536-386">Prepare your data</span></span>
> * <span data-ttu-id="60536-387">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="60536-387">Create the learning pipeline</span></span>
> * <span data-ttu-id="60536-388">Načíst třídění</span><span class="sxs-lookup"><span data-stu-id="60536-388">Load a classifier</span></span>
> * <span data-ttu-id="60536-389">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="60536-389">Train the model</span></span>
> * <span data-ttu-id="60536-390">Vyhodnocení modelu s jinou datovou sadu</span><span class="sxs-lookup"><span data-stu-id="60536-390">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="60536-391">Předpověď výsledků dat testu s modelem</span><span class="sxs-lookup"><span data-stu-id="60536-391">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="60536-392">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="60536-392">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="60536-393">Prediktivní tarif taxislužby města</span><span class="sxs-lookup"><span data-stu-id="60536-393">Taxi Fare Predictor</span></span>](taxi-fare.md)
