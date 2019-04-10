---
title: V případě GitHub problém klasifikace víc tříd použít ML.NET
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy Githubu pro jejich přiřazení k dané oblasti.
ms.date: 03/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e25f044247064db26e4e1e74590d6f4970fe4477
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318777"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="b3641-103">Kurz: Použití ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy s úložištěm GitHub</span><span class="sxs-lookup"><span data-stu-id="b3641-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues</span></span>

<span data-ttu-id="b3641-104">Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru problém Githubu prostřednictvím aplikace konzoly .NET Core using C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b3641-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="b3641-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="b3641-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b3641-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="b3641-106">Understand the problem</span></span>
> * <span data-ttu-id="b3641-107">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="b3641-107">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="b3641-108">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b3641-108">Prepare your data</span></span>
> * <span data-ttu-id="b3641-109">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="b3641-109">Transform the data</span></span>
> * <span data-ttu-id="b3641-110">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-110">Train the model</span></span>
> * <span data-ttu-id="b3641-111">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-111">Evaluate the model</span></span>
> * <span data-ttu-id="b3641-112">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-112">Predict with the trained model</span></span>
> * <span data-ttu-id="b3641-113">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="b3641-113">Deploy and Predict with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="b3641-114">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="b3641-114">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b3641-115">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b3641-115">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b3641-116">Tento kurz a související ukázkové právě používáte **ML.NET verze 0,11**.</span><span class="sxs-lookup"><span data-stu-id="b3641-116">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="b3641-117">Další informace najdete v tématu poznámky k verzi v [úložišti dotnet/machinelearning githubu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="b3641-117">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="b3641-118">Přehled ukázky problém Githubu</span><span class="sxs-lookup"><span data-stu-id="b3641-118">GitHub issue sample overview</span></span>

<span data-ttu-id="b3641-119">Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje popisek oblasti pro problém na Githubu.</span><span class="sxs-lookup"><span data-stu-id="b3641-119">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="b3641-120">Vyhodnocuje také model s druhou datové sady pro analýzy kvality.</span><span class="sxs-lookup"><span data-stu-id="b3641-120">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="b3641-121">Problém datové sady jsou v úložišti dotnet/corefx Githubu.</span><span class="sxs-lookup"><span data-stu-id="b3641-121">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

<span data-ttu-id="b3641-122">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.</span><span class="sxs-lookup"><span data-stu-id="b3641-122">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b3641-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3641-123">Prerequisites</span></span>

* <span data-ttu-id="b3641-124">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="b3641-124">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="b3641-125">[Githubu problémy s daty oddělenými tabulátory souboru (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="b3641-125">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="b3641-126">[Problémy Githubu testovací soubor oddělených tabulátory (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="b3641-126">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="b3641-127">Pracovní postup Machine learning</span><span class="sxs-lookup"><span data-stu-id="b3641-127">Machine learning workflow</span></span>

<span data-ttu-id="b3641-128">V tomto kurzu se řídí strojového učení pracovního postupu, který umožňuje přesunout řádný proces.</span><span class="sxs-lookup"><span data-stu-id="b3641-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="b3641-129">Fáze pracovního postupu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="b3641-129">The workflow phases are as follows:</span></span>

1. **<span data-ttu-id="b3641-130">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="b3641-130">Understand the problem</span></span>**
2. **<span data-ttu-id="b3641-131">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b3641-131">Prepare your data</span></span>**
   * **<span data-ttu-id="b3641-132">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b3641-132">Load the data</span></span>**
   * **<span data-ttu-id="b3641-133">Extrakce funkce (transformovat data)</span><span class="sxs-lookup"><span data-stu-id="b3641-133">Extract features (Transform your data)</span></span>**
3. **<span data-ttu-id="b3641-134">Sestavení a trénování</span><span class="sxs-lookup"><span data-stu-id="b3641-134">Build and train</span></span>** 
   * **<span data-ttu-id="b3641-135">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-135">Train the model</span></span>**
   * **<span data-ttu-id="b3641-136">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-136">Evaluate the model</span></span>**
4. **<span data-ttu-id="b3641-137">Nasazení modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-137">Deploy Model</span></span>**
   * **<span data-ttu-id="b3641-138">Použijte Model k predikci</span><span class="sxs-lookup"><span data-stu-id="b3641-138">Use the Model to predict</span></span>**

### <a name="understand-the-problem"></a><span data-ttu-id="b3641-139">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="b3641-139">Understand the problem</span></span>

<span data-ttu-id="b3641-140">Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="b3641-141">Popis vnitřních principů problému můžete předpovídat a vyhodnoťte výsledky.</span><span class="sxs-lookup"><span data-stu-id="b3641-141">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="b3641-142">Problém pro účely tohoto kurzu je pochopit, co příchozí problémy Githubu oblasti patří aby bylo možné správně popisek pro stanovení priorit a plánování.</span><span class="sxs-lookup"><span data-stu-id="b3641-142">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="b3641-143">Problém můžete rozdělit do následujících částí:</span><span class="sxs-lookup"><span data-stu-id="b3641-143">You can break down the problem to the following parts:</span></span>

* <span data-ttu-id="b3641-144">text nadpisu problém</span><span class="sxs-lookup"><span data-stu-id="b3641-144">the issue title text</span></span>
* <span data-ttu-id="b3641-145">popis problému</span><span class="sxs-lookup"><span data-stu-id="b3641-145">the issue description text</span></span>
* <span data-ttu-id="b3641-146">hodnotu oblasti pro trénovací data modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-146">an area value for the model training data</span></span>
* <span data-ttu-id="b3641-147">Předpokládaná oblasti hodnotu, kterou můžete vyhodnotit a pak použít provozně</span><span class="sxs-lookup"><span data-stu-id="b3641-147">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="b3641-148">Potom budete potřebovat **určit** oblast, která vám pomůže s strojového učení výběr úkolů.</span><span class="sxs-lookup"><span data-stu-id="b3641-148">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="b3641-149">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="b3641-149">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="b3641-150">Tento problém víte, k následujícím skutečnostem:</span><span class="sxs-lookup"><span data-stu-id="b3641-150">With this problem, you know the following facts:</span></span>

<span data-ttu-id="b3641-151">Cvičná data:</span><span class="sxs-lookup"><span data-stu-id="b3641-151">Training data:</span></span>

<span data-ttu-id="b3641-152">Problémy Githubu můžete označené v několika oblastech (**oblasti**) jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="b3641-152">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="b3641-153">area-System.Numerics</span><span class="sxs-lookup"><span data-stu-id="b3641-153">area-System.Numerics</span></span>
* <span data-ttu-id="b3641-154">area-System.Xml</span><span class="sxs-lookup"><span data-stu-id="b3641-154">area-System.Xml</span></span>
* <span data-ttu-id="b3641-155">oblasti infrastruktury</span><span class="sxs-lookup"><span data-stu-id="b3641-155">area-Infrastructure</span></span>
* <span data-ttu-id="b3641-156">area-System.Linq</span><span class="sxs-lookup"><span data-stu-id="b3641-156">area-System.Linq</span></span>
* <span data-ttu-id="b3641-157">System.IO oblasti</span><span class="sxs-lookup"><span data-stu-id="b3641-157">area-System.IO</span></span>

<span data-ttu-id="b3641-158">Předpověď **oblasti** z nový problém Githubu například v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="b3641-158">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="b3641-159">Vs Contract.Assert Debug.Assert –</span><span class="sxs-lookup"><span data-stu-id="b3641-159">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="b3641-160">Nastavte pole jen pro čtení v System.Xml</span><span class="sxs-lookup"><span data-stu-id="b3641-160">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="b3641-161">Algoritmu strojového učení klasifikace je nejvhodnější pro tento scénář.</span><span class="sxs-lookup"><span data-stu-id="b3641-161">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-learning-algorithm"></a><span data-ttu-id="b3641-162">O algoritmu učení klasifikace</span><span class="sxs-lookup"><span data-stu-id="b3641-162">About the classification learning algorithm</span></span>

<span data-ttu-id="b3641-163">Klasifikace je algoritmus strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky.</span><span class="sxs-lookup"><span data-stu-id="b3641-163">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="b3641-164">Například můžete použít klasifikace:</span><span class="sxs-lookup"><span data-stu-id="b3641-164">For example, you can use classification to:</span></span>

* <span data-ttu-id="b3641-165">Zjistit mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="b3641-165">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="b3641-166">E-mailu klasifikujte jako spam nevyžádané nebo funkční.</span><span class="sxs-lookup"><span data-stu-id="b3641-166">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="b3641-167">Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="b3641-167">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="b3641-168">Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.</span><span class="sxs-lookup"><span data-stu-id="b3641-168">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="b3641-169">Použití algoritmu učení klasifikace případy jsou často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="b3641-169">Classification learning algorithm use cases are frequently one of the following types:</span></span>

* <span data-ttu-id="b3641-170">Binární soubor: buď A a B.</span><span class="sxs-lookup"><span data-stu-id="b3641-170">Binary: either A or B.</span></span>
* <span data-ttu-id="b3641-171">Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-171">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="b3641-172">Pro tento typ problému používejte klasifikaci Multiclass učení algoritmu, protože predikci kategorii problému může být jeden z více kategorií (multiclass) místo jen dvou (binární).</span><span class="sxs-lookup"><span data-stu-id="b3641-172">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b3641-173">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="b3641-173">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="b3641-174">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="b3641-174">Create a project</span></span>

1. <span data-ttu-id="b3641-175">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b3641-175">Open Visual Studio 2017.</span></span> <span data-ttu-id="b3641-176">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="b3641-176">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b3641-177">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="b3641-177">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="b3641-178">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="b3641-178">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b3641-179">V **název** textového pole zadejte "GitHubIssueClassification" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b3641-179">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="b3641-180">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="b3641-180">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="b3641-181">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="b3641-181">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b3641-182">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="b3641-182">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="b3641-183">Vytvořte adresář *modely* ve vašem projektu a uložit model:</span><span class="sxs-lookup"><span data-stu-id="b3641-183">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="b3641-184">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="b3641-184">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b3641-185">Zadejte "Modely" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="b3641-185">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="b3641-186">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b3641-186">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="b3641-187">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b3641-187">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b3641-188">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b3641-188">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b3641-189">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="b3641-189">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="b3641-190">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b3641-190">Prepare your data</span></span>

1. <span data-ttu-id="b3641-191">Stáhněte si [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka.</span><span class="sxs-lookup"><span data-stu-id="b3641-191">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="b3641-192">První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="b3641-192">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="b3641-193">V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b3641-193">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="b3641-194">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="b3641-194">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="b3641-195">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="b3641-195">Create classes and define paths</span></span>

<span data-ttu-id="b3641-196">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b3641-196">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="b3641-197">Vytvořte tři globální pole pro uložení cest k naposledy stažené soubory a globálních proměnných pro `MLContext`,`DataView`, `PredictionEngine`, a `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="b3641-197">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, `PredictionEngine`, and `TextLoader`:</span></span>

* `_trainDataPath` <span data-ttu-id="b3641-198">obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-198">has the path to the dataset used to train the model.</span></span>
* `_testDataPath` <span data-ttu-id="b3641-199">obsahuje cestu k datové sadě k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-199">has the path to the dataset used to evaluate the model.</span></span>
* `_modelPath` <span data-ttu-id="b3641-200">obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-200">has the path where the trained model is saved.</span></span>
* `_mlContext` <span data-ttu-id="b3641-201">je <xref:Microsoft.ML.MLContext> , která poskytuje kontext zpracování.</span><span class="sxs-lookup"><span data-stu-id="b3641-201">is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* `_trainingDataView` <span data-ttu-id="b3641-202">je <xref:Microsoft.Data.DataView.IDataView> používají ke zpracování trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="b3641-202">is the <xref:Microsoft.Data.DataView.IDataView> used to process the training dataset.</span></span>
* `_predEngine` <span data-ttu-id="b3641-203">je <xref:Microsoft.ML.PredictionEngine%602> používá pro jeden předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3641-203">is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* `_reader` <span data-ttu-id="b3641-204">je <xref:Microsoft.ML.Data.TextLoader> lze načíst a transformovat datové sady.</span><span class="sxs-lookup"><span data-stu-id="b3641-204">is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="b3641-205">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="b3641-205">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="b3641-206">Vytvořte některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3641-206">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="b3641-207">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="b3641-207">Add a new class to your project:</span></span>

1. <span data-ttu-id="b3641-208">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="b3641-208">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="b3641-209">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b3641-209">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="b3641-210">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b3641-210">Then, select the **Add** button.</span></span>

    <span data-ttu-id="b3641-211">*GitHubIssueData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="b3641-211">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="b3641-212">Přidejte následující `using` příkaz do horní části *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b3641-212">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="b3641-213">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, možnosti *GitHubIssueData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b3641-213">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` <span data-ttu-id="b3641-214">je třída vstupní datová sada a má následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="b3641-214">is the input dataset class and has the following <xref:System.String> fields:</span></span>

* `ID` <span data-ttu-id="b3641-215">obsahuje hodnotu pro ID problému Githubu</span><span class="sxs-lookup"><span data-stu-id="b3641-215">contains a value for the GitHub issue ID</span></span>
* `Area` <span data-ttu-id="b3641-216">obsahuje hodnotu `Area` popisek</span><span class="sxs-lookup"><span data-stu-id="b3641-216">contains a value for the `Area` label</span></span>
* `Title` <span data-ttu-id="b3641-217">obsahuje název problému Githubu</span><span class="sxs-lookup"><span data-stu-id="b3641-217">contains the GitHub issue title</span></span>
* `Description` <span data-ttu-id="b3641-218">obsahuje popis problému Githubu</span><span class="sxs-lookup"><span data-stu-id="b3641-218">contains the GitHub issue description</span></span>

`IssuePrediction` <span data-ttu-id="b3641-219">Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="b3641-219">is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="b3641-220">Má jediný `string` (`Area`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="b3641-220">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="b3641-221">`Label` Slouží k vytvoření a trénování modelu a jeho datové sady druhé použít také k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-221">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="b3641-222">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b3641-222">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="b3641-223">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="b3641-223">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="b3641-224">Při vytváření modelu s ML.NET, začněte vytvořením <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="b3641-224">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> `MLContext` <span data-ttu-id="b3641-225">je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b3641-225">is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="b3641-226">Prostředí poskytuje kontext pro vaši úlohu ML, který lze použít pro sledování a protokolování výjimek.</span><span class="sxs-lookup"><span data-stu-id="b3641-226">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="b3641-227">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="b3641-227">Initialize variables in Main</span></span>

<span data-ttu-id="b3641-228">Inicializovat `_mlContext` globální proměnnou s novou instanci třídy `MLContext` s náhodná počáteční hodnota (`seed: 0`) pro opakovatelné/deterministické výsledky napříč více školení.</span><span class="sxs-lookup"><span data-stu-id="b3641-228">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="b3641-229">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="b3641-229">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="b3641-230">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b3641-230">Load the data</span></span>

<span data-ttu-id="b3641-231">V dalším kroku inicializovat `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> globální proměnné a načtení dat pomocí `_trainDataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="b3641-231">Next, initialize the `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="b3641-232">Jako vstup a výstup [ `Transforms` ](../basic-concepts-model-training-in-mldotnet.md#transformer), `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="b3641-232">As the input and output of [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="b3641-233">Data jsou v ML.NET, podobně jako `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="b3641-233">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="b3641-234">Je laxně Vyhodnocená schematizovanými a heterogenní.</span><span class="sxs-lookup"><span data-stu-id="b3641-234">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="b3641-235">Objekt představuje první část kanálu a načte data.</span><span class="sxs-lookup"><span data-stu-id="b3641-235">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="b3641-236">Pro účely tohoto kurzu načte datovou sadu s problém názvy, popisy a odpovídající oblasti Githubu popisek.</span><span class="sxs-lookup"><span data-stu-id="b3641-236">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="b3641-237">`DataView` Slouží k vytvoření a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-237">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="b3641-238">Od dříve vytvořeného `GitHubIssue` typ modelu dat odpovídá schématu datové sady, inicializace, mapování a datová sada načítání do jednoho řádku kódu lze kombinovat.</span><span class="sxs-lookup"><span data-stu-id="b3641-238">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="b3641-239">Načtení dat pomocí `MLContext.Data.LoadFromTextFile` obálky pro [LoadFromTextFile metoda](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="b3641-239">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="b3641-240">Vrátí <xref:Microsoft.Data.DataView.IDataView> které odvodí schéma datové sady z `GitHubIssue` typ modelu dat a záhlaví datové sady používá.</span><span class="sxs-lookup"><span data-stu-id="b3641-240">It returns a <xref:Microsoft.Data.DataView.IDataView> which infers the dataset schema from the `GitHubIssue` data model type and uses the dataset header.</span></span> 

<span data-ttu-id="b3641-241">Definujete schéma dat dříve při vytváření `GitHubIssue` třídy.</span><span class="sxs-lookup"><span data-stu-id="b3641-241">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="b3641-242">Pro schéma:</span><span class="sxs-lookup"><span data-stu-id="b3641-242">For your schema:</span></span>

* <span data-ttu-id="b3641-243">první sloupec `ID` (ID problému Githubu)</span><span class="sxs-lookup"><span data-stu-id="b3641-243">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="b3641-244">druhý sloupec `Area` (Předpověď pro školení)</span><span class="sxs-lookup"><span data-stu-id="b3641-244">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="b3641-245">třetí sloupec `Title` (název problému Githubu) je prvním [funkce](../resources/glossary.md##feature) používá pro predikci</span><span class="sxs-lookup"><span data-stu-id="b3641-245">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the</span></span> `Area`
* <span data-ttu-id="b3641-246">čtvrtý sloupec `Description` je druhá funkce používá pro predikci</span><span class="sxs-lookup"><span data-stu-id="b3641-246">the fourth column  `Description` is the second feature used for predicting the</span></span> `Area`

<span data-ttu-id="b3641-247">K inicializaci a načíst `_trainingDataView` globální proměnné, aby bylo možné používat pro kanál, přidejte následující kód za `mlContext` inicializace:</span><span class="sxs-lookup"><span data-stu-id="b3641-247">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="b3641-248">Přidejte následující položky jako další řádek kódu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="b3641-248">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="b3641-249">`ProcessData` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b3641-249">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="b3641-250">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="b3641-250">Extracts and transforms the data.</span></span>
* <span data-ttu-id="b3641-251">Vrátí kanálu zpracování.</span><span class="sxs-lookup"><span data-stu-id="b3641-251">Returns the processing pipeline.</span></span>

<span data-ttu-id="b3641-252">Vytvořte `ProcessData` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-252">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="b3641-253">Extrakce funkce a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="b3641-253">Extract Features and transform the data</span></span>

<span data-ttu-id="b3641-254">Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="b3641-254">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="b3641-255">Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b3641-255">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="b3641-256">Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="b3641-256">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="b3641-257">ML. Kanály transformace vaší NET napsat vlastní `transforms`sada, která se použije pro vaše data před trénování a testování.</span><span class="sxs-lookup"><span data-stu-id="b3641-257">ML.NET's transform pipelines compose a custom `transforms`set that is applied to your data before training or testing.</span></span> <span data-ttu-id="b3641-258">Hlavním účelem transformace jsou data [snadné](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="b3641-258">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="b3641-259">Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) data, abyste dalším krokem je získat z našich algoritmů ML rozpoznat formát naše textová data.</span><span class="sxs-lookup"><span data-stu-id="b3641-259">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="b3641-260">Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="b3641-260">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="b3641-261">V dalších krocích, budeme odkazovat na sloupce pomocí názvy definované v `GitHubIssue` třídy.</span><span class="sxs-lookup"><span data-stu-id="b3641-261">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="b3641-262">Když je model trénují a vyhodnocují, ve výchozím nastavení, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat.</span><span class="sxs-lookup"><span data-stu-id="b3641-262">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="b3641-263">Jelikož chceme předpovědět popisek oblasti Githubu pro `GitHubIssue`, kopie `Area` sloupce do **popisek** sloupec.</span><span class="sxs-lookup"><span data-stu-id="b3641-263">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="b3641-264">Chcete-li to mohli udělat, použijte `MLContext.Transforms.Conversion.MapValueToKey`, který tvoří obálku pro <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="b3641-264">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="b3641-265">`MapValueToKey` Vrátí <xref:Microsoft.ML.Data.EstimatorChain%601> efektivně, který bude kanál.</span><span class="sxs-lookup"><span data-stu-id="b3641-265">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="b3641-266">Pojmenujte toto `pipeline` jako se pak připojí trainer k `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="b3641-266">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="b3641-267">Přidáte další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-267">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 <span data-ttu-id="b3641-268">Featurizing přiřadí různé číselné hodnoty klíče na různé hodnoty v každém sloupci a je používán algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="b3641-268">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span> <span data-ttu-id="b3641-269">Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` které featurizes text (`Title` a `Description`) sloupce jako číselné vektor pro každou volá `TitleFeaturized` a `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="b3641-269">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="b3641-270">Snadné pro oba sloupce pro přidání do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b3641-270">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> <span data-ttu-id="b3641-271">ML.NET verze 0.10 má změnit pořadí parametrů transformace.</span><span class="sxs-lookup"><span data-stu-id="b3641-271">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="b3641-272">Tímto krokem se nevygeneruje chybu, dokud sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3641-272">This will not error out until you build.</span></span> <span data-ttu-id="b3641-273">Použijte názvy parametrů transformací, jak je znázorněno v předchozím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="b3641-273">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="b3641-274">Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce `Concatenate` třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="b3641-274">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="b3641-275">Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="b3641-275">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="b3641-276">Připojte tuto transformaci na kanál s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b3641-276">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="b3641-277">V dalším kroku připojit <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> pro ukládání do mezipaměti DataView, takže při iteraci přes data s využitím více než jednou mezipaměti může dosahovat vyšších výkonů, stejně jako u následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-277">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="b3641-278">Můžete snížit dobu výuky AppendCacheCheckpoint pro malé a střední datové sady.</span><span class="sxs-lookup"><span data-stu-id="b3641-278">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="b3641-279">Nepoužívejte ho (odebrat. AppendCacheCheckpoint()) při zpracování velmi velkých datových sad.</span><span class="sxs-lookup"><span data-stu-id="b3641-279">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="b3641-280">Kanál na konci vrátit `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="b3641-280">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="b3641-281">Tento krok zpracovává předběžného zpracování a snadné.</span><span class="sxs-lookup"><span data-stu-id="b3641-281">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="b3641-282">Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.</span><span class="sxs-lookup"><span data-stu-id="b3641-282">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="b3641-283">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-283">Build and train the model</span></span>

<span data-ttu-id="b3641-284">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="b3641-284">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="b3641-285">`BuildAndTrainModel` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b3641-285">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="b3641-286">Vytvoří třídu algoritmus školení.</span><span class="sxs-lookup"><span data-stu-id="b3641-286">Creates the training algorithm class.</span></span>
* <span data-ttu-id="b3641-287">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-287">Trains the model.</span></span>
* <span data-ttu-id="b3641-288">Předpovídá oblasti založené na trénovací data.</span><span class="sxs-lookup"><span data-stu-id="b3641-288">Predicts area based on training data.</span></span>
* <span data-ttu-id="b3641-289">Uloží model, který má `.zip` souboru.</span><span class="sxs-lookup"><span data-stu-id="b3641-289">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="b3641-290">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="b3641-290">Returns the model.</span></span>

<span data-ttu-id="b3641-291">Vytvořte `BuildAndTrainModel` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-291">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

<span data-ttu-id="b3641-292">Všimněte si, že dva parametry jsou předány do metody BuildAndTrainModel; `IDataView` pro trénovací datové sady (`trainingDataView`) a <xref:Microsoft.ML.Data.EstimatorChain%601> pro zpracování kanálu, který vytvořili v ProcessData (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="b3641-292">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="b3641-293">Přidejte následující kód jako první řádek `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="b3641-293">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-learning-algorithm"></a><span data-ttu-id="b3641-294">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="b3641-294">Choose a learning algorithm</span></span>

<span data-ttu-id="b3641-295">Chcete-li přidat algoritmu učení, zavolejte `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` obalující metodu, která vrátí hodnotu <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> objektu.</span><span class="sxs-lookup"><span data-stu-id="b3641-295">To add the learning algorithm, call the `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span>  <span data-ttu-id="b3641-296">`SdcaMultiClassTrainer` Se připojí `pipeline` a přijímá natrénuje `Title` a `Description` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="b3641-296">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span> <span data-ttu-id="b3641-297">Potřebujete také mapovat popisku na hodnotu, která vrátí k původnímu čitelné.</span><span class="sxs-lookup"><span data-stu-id="b3641-297">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="b3641-298">Proveďte obě tyto akce s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b3641-298">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="b3641-299">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-299">Train the model</span></span>

<span data-ttu-id="b3641-300">Trénování modelu, <xref:Microsoft.ML.Data.TransformerChain%601>založená na datovou sadu, která má načíst a transformovat.</span><span class="sxs-lookup"><span data-stu-id="b3641-300">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="b3641-301">Po definování odhadu tréninku modelu pomocí <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> současně už načtený trénovací data.</span><span class="sxs-lookup"><span data-stu-id="b3641-301">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="b3641-302">Tato metoda vrátí model pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3641-302">This  method returns a model to use for predictions.</span></span> `trainingPipeline.Fit()` <span data-ttu-id="b3641-303">trénovat kanálu a vrátí `Transformer` na základě `DataView` předán.</span><span class="sxs-lookup"><span data-stu-id="b3641-303">trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="b3641-304">Dokud není spuštěn experimentu `.Fit()` metoda spuštění.</span><span class="sxs-lookup"><span data-stu-id="b3641-304">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="b3641-305">Přidejte následující kód, který `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="b3641-305">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="b3641-306">Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, třeba k předpovědím na jednotlivé příklady je běžný scénář produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="b3641-306">While the `model` is a `transformer` that operates on many rows of data, a need for predictions on individual examples is a common production scenario.</span></span> <span data-ttu-id="b3641-307"><xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="b3641-307">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="b3641-308">Přidejte následující kód k vytvoření `PredictionEngine` jako další řádek `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="b3641-308">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="b3641-309">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-309">Predict with the trained model</span></span>

<span data-ttu-id="b3641-310">Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="b3641-310">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="b3641-311">Který můžete použít k předpovědi `Area` popisek jednu instanci data problém.</span><span class="sxs-lookup"><span data-stu-id="b3641-311">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="b3641-312">Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data.</span><span class="sxs-lookup"><span data-stu-id="b3641-312">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="b3641-313">Vstupní data je řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="b3641-313">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="b3641-314">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="b3641-314">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="b3641-315">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3641-315">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="b3641-316">Pomocí modelu: předpověď výsledků</span><span class="sxs-lookup"><span data-stu-id="b3641-316">Using the model: prediction results</span></span>

<span data-ttu-id="b3641-317">Zobrazení `GitHubIssue` a odpovídající `Area` popisek predikcí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="b3641-317">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="b3641-318">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-318">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="b3641-319">Vrátí že model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="b3641-319">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="b3641-320">Model na konci vrátit `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="b3641-320">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="b3641-321">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-321">Evaluate the model</span></span>

<span data-ttu-id="b3641-322">Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování.</span><span class="sxs-lookup"><span data-stu-id="b3641-322">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="b3641-323">V `Evaluate` metody, vytvořené v modelu `BuildAndTrainModel` předaný k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b3641-323">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="b3641-324">Vytvořte `Evaluate` metoda, hned za `BuildAndTrainModel`, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-324">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="b3641-325">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b3641-325">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="b3641-326">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="b3641-326">Loads the test dataset.</span></span>
* <span data-ttu-id="b3641-327">Vytvoří víc tříd Chyba při vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="b3641-327">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="b3641-328">Vyhodnotí modelu a vytvoření metriky.</span><span class="sxs-lookup"><span data-stu-id="b3641-328">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="b3641-329">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="b3641-329">Displays the metrics.</span></span>

<span data-ttu-id="b3641-330">Přidejte volání do nové metody z `Main` metody, v rámci `BuildAndTrainModel` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-330">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="b3641-331">Stejně jako dříve trénovací datové sady, můžete kombinovat inicializace, mapování a otestovat datovou sadu načítání do jednoho řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="b3641-331">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="b3641-332">Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality.</span><span class="sxs-lookup"><span data-stu-id="b3641-332">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="b3641-333">Přidejte následující kód, který `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="b3641-333">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="b3641-334">`MulticlassClassificationContext.Evaluate` Tvoří obálku pro <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> metodu, která vypočítá metrik kvality pro model pomocí zadaného objektu dataset.</span><span class="sxs-lookup"><span data-stu-id="b3641-334">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="b3641-335">Vrátí <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení klasifikace víc tříd.</span><span class="sxs-lookup"><span data-stu-id="b3641-335">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="b3641-336">Pokud chcete zobrazit metriky pro určení kvality tohoto modelu, musíte je získat první.</span><span class="sxs-lookup"><span data-stu-id="b3641-336">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="b3641-337">Všimněte si použití `Transform` metoda služby machine learning `_trainedModel` globální proměnné (transformace) k zadání funkce a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3641-337">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="b3641-338">Přidejte následující kód, který `Evaluate` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="b3641-338">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="b3641-339">Klasifikace víc tříd, se vyhodnotí následující metriky:</span><span class="sxs-lookup"><span data-stu-id="b3641-339">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="b3641-340">Micro přesnost – každá dvojice ukázkovou třídu přispívá stejně metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="b3641-340">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="b3641-341">Chcete, aby Micro přesnost, aby byly co nejblíže 1 nejvíce.</span><span class="sxs-lookup"><span data-stu-id="b3641-341">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="b3641-342">Přesnost – makro – každá třída přispívá stejně metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="b3641-342">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="b3641-343">Třídy minority disponují stejnou váhu jako větší třídy.</span><span class="sxs-lookup"><span data-stu-id="b3641-343">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="b3641-344">Chcete, aby byly co nejblíže 1 nejvíce přesnost – makro.</span><span class="sxs-lookup"><span data-stu-id="b3641-344">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="b3641-345">Protokol ztrát – naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="b3641-345">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="b3641-346">Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="b3641-346">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="b3641-347">Od ztráty protokolu snížení - [-inf, 100], kde 100 je ideální předpovědi a 0 označuje střední předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3641-347">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="b3641-348">Chcete, aby omezení ztráty protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="b3641-348">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="b3641-349">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-349">Displaying the metrics for model validation</span></span>

<span data-ttu-id="b3641-350">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b3641-350">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a><span data-ttu-id="b3641-351">Uložení natrénovaného a vyhodnocené modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-351">Save the trained and evaluated model</span></span>

<span data-ttu-id="b3641-352">V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain%601> , který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="b3641-352">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="b3641-353">Uložte soubor .zip trénovaného modelu, přidejte následující kód k volání `SaveModelAsFile` metody jako další řádek v `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="b3641-353">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="b3641-354">Model uložit jako soubor ZIP</span><span class="sxs-lookup"><span data-stu-id="b3641-354">Save the model as a .zip file</span></span>

<span data-ttu-id="b3641-355">Vytvořte `SaveModelAsFile` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-355">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="b3641-356">`SaveModelAsFile` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b3641-356">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="b3641-357">Uloží modelu ve formě souboru .zip.</span><span class="sxs-lookup"><span data-stu-id="b3641-357">Saves the model as a .zip file.</span></span>

<span data-ttu-id="b3641-358">Dále vytvořte metodu k uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="b3641-358">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="b3641-359">`ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="b3641-359">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="b3641-360">Model uložit jako soubor zip, vytvoříte `FileStream` bezprostředně před volání `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="b3641-360">To save the model as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="b3641-361">Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="b3641-361">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="b3641-362">Může také zobrazit, kde soubor byl zapsán napsáním zprávu konzoly `_modelPath`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-362">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="b3641-363">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="b3641-363">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="b3641-364">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-364">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="b3641-365">Vytvořit `PredictIssue` metoda, hned za `Evaluate` – metoda (a těsně před `SaveModelAsFile` metoda), pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-365">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="b3641-366">`PredictIssue` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b3641-366">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="b3641-367">Vytvoří jen jeden problém testovací data.</span><span class="sxs-lookup"><span data-stu-id="b3641-367">Creates a single issue of test data.</span></span>
* <span data-ttu-id="b3641-368">Předpovídá oblasti na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="b3641-368">Predicts Area based on test data.</span></span>
* <span data-ttu-id="b3641-369">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="b3641-369">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="b3641-370">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="b3641-370">Displays the predicted results.</span></span>

<span data-ttu-id="b3641-371">Nejdřív načtěte model, který jste si předtím uložili následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b3641-371">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="b3641-372">Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="b3641-372">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="b3641-373">Teď, když máte model, který můžete použít k predikci popisek oblasti Githubu jedné instance dat problém Githubu.</span><span class="sxs-lookup"><span data-stu-id="b3641-373">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="b3641-374">Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data.</span><span class="sxs-lookup"><span data-stu-id="b3641-374">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="b3641-375">Vstupní data je řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="b3641-375">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="b3641-376">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="b3641-376">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="b3641-377">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3641-377">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="b3641-378">Přidejte následující kód, který `PredictIssue` metodu předpovědí:</span><span class="sxs-lookup"><span data-stu-id="b3641-378">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="b3641-379">Použití načíst model pro předpověď</span><span class="sxs-lookup"><span data-stu-id="b3641-379">Using the loaded model for prediction</span></span>

<span data-ttu-id="b3641-380">Zobrazení `Area` kategorizace problém a příslušně na ně reagovat na něj.</span><span class="sxs-lookup"><span data-stu-id="b3641-380">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="b3641-381">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="b3641-381">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="b3641-382">Výsledky</span><span class="sxs-lookup"><span data-stu-id="b3641-382">Results</span></span>

<span data-ttu-id="b3641-383">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="b3641-383">Your results should be similar to the following.</span></span> <span data-ttu-id="b3641-384">Při zpracování kanálu zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="b3641-384">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="b3641-385">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="b3641-385">You may see warnings, or processing messages.</span></span> <span data-ttu-id="b3641-386">Tyto zprávy se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="b3641-386">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="b3641-387">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="b3641-387">Congratulations!</span></span> <span data-ttu-id="b3641-388">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat popisek oblasti pro problém na Githubu.</span><span class="sxs-lookup"><span data-stu-id="b3641-388">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="b3641-389">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.</span><span class="sxs-lookup"><span data-stu-id="b3641-389">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b3641-390">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b3641-390">Next steps</span></span>

<span data-ttu-id="b3641-391">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="b3641-391">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b3641-392">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="b3641-392">Understand the problem</span></span>
> * <span data-ttu-id="b3641-393">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="b3641-393">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="b3641-394">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b3641-394">Prepare your data</span></span>
> * <span data-ttu-id="b3641-395">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="b3641-395">Transform the data</span></span>
> * <span data-ttu-id="b3641-396">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-396">Train the model</span></span>
> * <span data-ttu-id="b3641-397">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-397">Evaluate the model</span></span>
> * <span data-ttu-id="b3641-398">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="b3641-398">Predict with the trained model</span></span>
> * <span data-ttu-id="b3641-399">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="b3641-399">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="b3641-400">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="b3641-400">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b3641-401">Prediktivní tarif taxislužby města</span><span class="sxs-lookup"><span data-stu-id="b3641-401">Taxi Fare Predictor</span></span>](taxi-fare.md)
