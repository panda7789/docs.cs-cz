---
title: Použití ML.NET ve scénáři binární klasifikace analýzy mínění
description: Objevte, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí mínění předpovědi proveďte příslušnou akci.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: c5373f63927ff39e7c819cd1fc0bc2bec1843b3e
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921114"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="8e78e-103">Kurz: Použití ML.NET ve scénáři binární klasifikace analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="8e78e-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="8e78e-104">Tento ukázkový kurz ukazuje vytvoření klasifikátoru subjektivního hodnocení pro předpověď pozitivní nebo negativní zabarvení prostřednictvím using aplikace konzoly .NET Core pomocí ML.NET C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8e78e-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to predict either positive or negative sentiment via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="8e78e-105">Ve světě služby machine learning tohoto typu predikcí se nazývá binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="8e78e-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="8e78e-106">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="8e78e-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="8e78e-107">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8e78e-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="8e78e-108">Tento kurz a související ukázkové právě používáte **ML.NET verze 0,11**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-108">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="8e78e-109">Další informace najdete v tématu poznámky k verzi v [dotnet/machinelearning úložiště GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="8e78e-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="8e78e-110">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="8e78e-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8e78e-111">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="8e78e-111">Understand the problem</span></span>
> * <span data-ttu-id="8e78e-112">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="8e78e-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="8e78e-113">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-113">Prepare your data</span></span>
> * <span data-ttu-id="8e78e-114">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-114">Transform the data</span></span>
> * <span data-ttu-id="8e78e-115">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-115">Train the model</span></span>
> * <span data-ttu-id="8e78e-116">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-116">Evaluate the model</span></span>
> * <span data-ttu-id="8e78e-117">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-117">Predict with the trained model</span></span>
> * <span data-ttu-id="8e78e-118">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="8e78e-118">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="8e78e-119">Přehled ukázky analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="8e78e-119">Sentiment analysis sample overview</span></span>

<span data-ttu-id="8e78e-120">Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="8e78e-120">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="8e78e-121">Tato datová sada Yelp mínění je z University of California, Irvine (UCI), který je rozdělený do datové sady pro trénování a datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="8e78e-121">The Yelp sentiment dataset is from University of California, Irvine (UCI), which is split into a train dataset and a test dataset.</span></span> <span data-ttu-id="8e78e-122">Ukázka vyhodnotí model s testovací datové analýzy kvality.</span><span class="sxs-lookup"><span data-stu-id="8e78e-122">The sample evaluates the model with the test dataset for quality analysis.</span></span> 

<span data-ttu-id="8e78e-123">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="8e78e-123">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8e78e-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e78e-124">Prerequisites</span></span>

* <span data-ttu-id="8e78e-125">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="8e78e-125">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="8e78e-126">Soubor zip UCI subjektivního hodnocení s popiskem věty datové sady</span><span class="sxs-lookup"><span data-stu-id="8e78e-126">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a><span data-ttu-id="8e78e-127">Pracovní postup Machine learning</span><span class="sxs-lookup"><span data-stu-id="8e78e-127">Machine learning workflow</span></span>

<span data-ttu-id="8e78e-128">V tomto kurzu se řídí strojového učení pracovního postupu, který umožňuje přesunout řádný proces.</span><span class="sxs-lookup"><span data-stu-id="8e78e-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="8e78e-129">Fáze pracovního postupu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8e78e-129">The workflow phases are as follows:</span></span>

1. **<span data-ttu-id="8e78e-130">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="8e78e-130">Understand the problem</span></span>**
2. **<span data-ttu-id="8e78e-131">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-131">Prepare your data</span></span>**
   * **<span data-ttu-id="8e78e-132">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-132">Load the data</span></span>**
   * **<span data-ttu-id="8e78e-133">Extrakce funkce (transformovat data)</span><span class="sxs-lookup"><span data-stu-id="8e78e-133">Extract features (Transform your data)</span></span>**
3. **<span data-ttu-id="8e78e-134">Sestavení a trénování</span><span class="sxs-lookup"><span data-stu-id="8e78e-134">Build and train</span></span>** 
   * **<span data-ttu-id="8e78e-135">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-135">Train the model</span></span>**
   * **<span data-ttu-id="8e78e-136">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-136">Evaluate the model</span></span>**
4. **<span data-ttu-id="8e78e-137">Nasazení modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-137">Deploy Model</span></span>**
   * **<span data-ttu-id="8e78e-138">Použijte Model k predikci</span><span class="sxs-lookup"><span data-stu-id="8e78e-138">Use the Model to predict</span></span>**

### <a name="understand-the-problem"></a><span data-ttu-id="8e78e-139">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="8e78e-139">Understand the problem</span></span>

<span data-ttu-id="8e78e-140">Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="8e78e-141">Rozdělení problému můžete předpovídat a vyhodnoťte výsledky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-141">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="8e78e-142">Problém pro účely tohoto kurzu je pochopit příchozí subjektivního hodnocení webu komentář, proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="8e78e-142">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="8e78e-143">Problém můžete rozdělit mínění textu a mínění hodnotu pro data chcete trénování modelu s a předpokládané mínění hodnotu, kterou můžete vyhodnotit a pak použít provozně.</span><span class="sxs-lookup"><span data-stu-id="8e78e-143">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="8e78e-144">Potom budete potřebovat **určit** subjektivního hodnocení, které vám pomůžou s strojového učení výběr úkolů.</span><span class="sxs-lookup"><span data-stu-id="8e78e-144">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="8e78e-145">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="8e78e-145">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="8e78e-146">Tento problém víte, k následujícím skutečnostem:</span><span class="sxs-lookup"><span data-stu-id="8e78e-146">With this problem, you know the following facts:</span></span>

<span data-ttu-id="8e78e-147">Cvičná data: komentáře web může být kladná (1) nebo záporná (0) (**mínění**).</span><span class="sxs-lookup"><span data-stu-id="8e78e-147">Training data: website comments can be positive (1) or negative (0) (**sentiment**).</span></span>

<span data-ttu-id="8e78e-148">Předpověď **mínění** nový web komentáře, kladná nebo záporná, jako například v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="8e78e-148">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="8e78e-149">Mám rád číšníky tady.</span><span class="sxs-lookup"><span data-stu-id="8e78e-149">I love the wait staff here.</span></span> <span data-ttu-id="8e78e-150">Že jdeme na to.</span><span class="sxs-lookup"><span data-stu-id="8e78e-150">They rock.</span></span>
* <span data-ttu-id="8e78e-151">Toto umístění má nejhorší polévky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-151">This place has the worst soup.</span></span>

<span data-ttu-id="8e78e-152">Algoritmu strojového učení klasifikace je nejvhodnější pro tento scénář.</span><span class="sxs-lookup"><span data-stu-id="8e78e-152">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-algorithm"></a><span data-ttu-id="8e78e-153">O klasifikační algoritmus</span><span class="sxs-lookup"><span data-stu-id="8e78e-153">About the classification algorithm</span></span>

<span data-ttu-id="8e78e-154">Klasifikace je algoritmus strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-154">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="8e78e-155">Například můžete použít klasifikace:</span><span class="sxs-lookup"><span data-stu-id="8e78e-155">For example, you can use classification to:</span></span>

* <span data-ttu-id="8e78e-156">Zjistit mínění jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="8e78e-156">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="8e78e-157">E-mailu klasifikujte jako spam nevyžádané nebo funkční.</span><span class="sxs-lookup"><span data-stu-id="8e78e-157">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="8e78e-158">Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="8e78e-158">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="8e78e-159">Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.</span><span class="sxs-lookup"><span data-stu-id="8e78e-159">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="8e78e-160">Algoritmy klasifikace jsou často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="8e78e-160">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="8e78e-161">Binární soubor: buď A a B.</span><span class="sxs-lookup"><span data-stu-id="8e78e-161">Binary: either A or B.</span></span>
* <span data-ttu-id="8e78e-162">Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-162">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="8e78e-163">Protože webu komentáře zapotřebí klasifikováno jako kladné nebo záporné, použít binární klasifikační algoritmus.</span><span class="sxs-lookup"><span data-stu-id="8e78e-163">Because the website comments need to be classified as either positive or negative, you use the Binary Classification algorithm.</span></span> 

## <a name="create-a-console-application"></a><span data-ttu-id="8e78e-164">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="8e78e-164">Create a console application</span></span>

1. <span data-ttu-id="8e78e-165">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8e78e-165">Open Visual Studio 2017.</span></span> <span data-ttu-id="8e78e-166">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="8e78e-166">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="8e78e-167">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-167">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="8e78e-168">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-168">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="8e78e-169">V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8e78e-169">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="8e78e-170">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="8e78e-170">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="8e78e-171">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-171">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8e78e-172">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="8e78e-172">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="8e78e-173">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="8e78e-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="8e78e-174">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8e78e-175">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8e78e-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8e78e-176">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="8e78e-176">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="8e78e-177">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-177">Prepare your data</span></span>

1. <span data-ttu-id="8e78e-178">Stáhněte si [soubor zip The UCI subjektivního hodnocení s popiskem věty datové sady (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="8e78e-178">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="8e78e-179">Kopírovat `yelp_labelled.txt` soubor do *Data* adresáře, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="8e78e-179">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

> [!NOTE]
> <span data-ttu-id="8e78e-180">Tento kurz používá datové sady jsou z "From skupina na jednotlivé popisky pomocí podrobné funkce", Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="8e78e-180">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="8e78e-181">al,.</span><span class="sxs-lookup"><span data-stu-id="8e78e-181">al,.</span></span> <span data-ttu-id="8e78e-182">Konference KDD 2015 a hostované v UCI Machine Learning úložiště – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="8e78e-182">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="8e78e-183">UCI strojového učení úložiště [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="8e78e-183">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="8e78e-184">Irvine, certifikační Autorita: University of California, z informací o škole a počítačových věd.</span><span class="sxs-lookup"><span data-stu-id="8e78e-184">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="8e78e-185">V Průzkumníku řešení klikněte pravým tlačítkem myši `yelp_labeled.txt` a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-185">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="8e78e-186">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="8e78e-187">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="8e78e-187">Create classes and define paths</span></span>

<span data-ttu-id="8e78e-188">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="8e78e-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="8e78e-189">Je potřeba vytvořit dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-189">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* `_dataPath` <span data-ttu-id="8e78e-190">obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-190">has the path to the dataset used to train the model.</span></span>
* `_modelPath` <span data-ttu-id="8e78e-191">obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-191">has the path where the trained model is saved.</span></span>

<span data-ttu-id="8e78e-192">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="8e78e-192">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="8e78e-193">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="8e78e-193">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="8e78e-194">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-194">Add a new class to your project:</span></span>

1. <span data-ttu-id="8e78e-195">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-195">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="8e78e-196">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="8e78e-196">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="8e78e-197">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8e78e-197">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8e78e-198">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-198">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="8e78e-199">Přidejte následující `using` příkaz do horní části *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="8e78e-199">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="8e78e-200">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="8e78e-200">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="8e78e-201">Třída vstupní datová sada `SentimentData`, má `string` pro komentář (`SentimentText`) a `bool` (`Sentiment`), který má hodnotu pro pozitivní nebo negativní zabarvení.</span><span class="sxs-lookup"><span data-stu-id="8e78e-201">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive or negative.</span></span> <span data-ttu-id="8e78e-202">Obě pole mají <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> atributy připojené k nim.</span><span class="sxs-lookup"><span data-stu-id="8e78e-202">Both fields have <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> attributes attached to them.</span></span> <span data-ttu-id="8e78e-203">Tento atribut popisuje pořadí každé pole v datovém souboru služby.</span><span class="sxs-lookup"><span data-stu-id="8e78e-203">This attribute describes the order of each field in the data file.</span></span>  <span data-ttu-id="8e78e-204">Kromě toho `Sentiment` má vlastnost <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> nastavit jako `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="8e78e-204">In addition, the `Sentiment` property has a <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> to designate it as the `Label` field.</span></span> `SentimentPrediction` <span data-ttu-id="8e78e-205">Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="8e78e-205">is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="8e78e-206">Má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="8e78e-206">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="8e78e-207">`Label` Slouží k vytvoření a trénování modelu a jeho rozdělení na testovací datové použít také k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-207">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="8e78e-208">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="8e78e-208">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="8e78e-209">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="8e78e-209">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="8e78e-210">Při vytváření modelu s ML.NET začnete vytvořením <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="8e78e-210">When building a model with ML.NET you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> `MLContext` <span data-ttu-id="8e78e-211">je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="8e78e-211">is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="8e78e-212">Prostředí poskytuje kontext pro vaši úlohu ML, který lze použít pro sledování a protokolování výjimek.</span><span class="sxs-lookup"><span data-stu-id="8e78e-212">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="8e78e-213">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="8e78e-213">Initialize variables in Main</span></span>

<span data-ttu-id="8e78e-214">Vytvořte proměnnou s názvem `mlContext` a inicializujte novou instanci třídy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="8e78e-214">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="8e78e-215">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-215">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="8e78e-216">Přidejte následující položky jako další řádek kódu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-216">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="8e78e-217">`LoadData` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8e78e-217">The `LoadData` method executes the following tasks:</span></span>

* <span data-ttu-id="8e78e-218">Načte data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-218">Loads the data.</span></span>
* <span data-ttu-id="8e78e-219">Rozdělí načíst datovou sadu na trénování a testování datových sad.</span><span class="sxs-lookup"><span data-stu-id="8e78e-219">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="8e78e-220">Vrátí hodnotu rozdělení trénují a testují datové sady.</span><span class="sxs-lookup"><span data-stu-id="8e78e-220">Returns the split train and test datasets.</span></span>

<span data-ttu-id="8e78e-221">Vytvořte `LoadData` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-221">Create the `LoadData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static TrainCatalogBase.TrainTestData LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a><span data-ttu-id="8e78e-222">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-222">Load the data</span></span>

<span data-ttu-id="8e78e-223">Od dříve vytvořeného `SentimentData` typ modelu dat odpovídá schématu datové sady, můžete kombinovat inicializace, mapování a datovou sadu na jeden řádek kódu pomocí načítání `MLContext.Data.LoadFromTextFile` obálky pro [LoadFromTextFile metoda](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="8e78e-223">Since your previously created `SentimentData` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="8e78e-224">Vrátí <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="8e78e-224">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

 <span data-ttu-id="8e78e-225">Jako vstup a výstup `Transforms`, `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="8e78e-225">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="8e78e-226">Data jsou v ML.NET, podobně jako zobrazení SQL.</span><span class="sxs-lookup"><span data-stu-id="8e78e-226">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="8e78e-227">Je laxně Vyhodnocená schematizovanými a heterogenní.</span><span class="sxs-lookup"><span data-stu-id="8e78e-227">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="8e78e-228">Objekt představuje první část kanálu a načte data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-228">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="8e78e-229">Pro účely tohoto kurzu načte datovou sadu s komentáři a odpovídající toxické nebo jiných toxické mínění.</span><span class="sxs-lookup"><span data-stu-id="8e78e-229">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="8e78e-230">Slouží k vytvoření modelu a jeho trénování.</span><span class="sxs-lookup"><span data-stu-id="8e78e-230">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="8e78e-231">Přidejte následující kód jako první řádek `LoadData` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-231">Add the following code as the first line of the `LoadData` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="8e78e-232">Rozdělení datové sady pro trénování a testování modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-232">Split the dataset for model training and testing</span></span>

<span data-ttu-id="8e78e-233">Dále je třeba trénovací datové sady pro trénování modelu a datové sady testů k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-233">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span> <span data-ttu-id="8e78e-234">Použití `MLContext.BinaryClassification.TrainTestSplit` která zabalí <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> rozdělit načíst datovou sadu na trénování a testování datových sad a vrátit je uvnitř <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span><span class="sxs-lookup"><span data-stu-id="8e78e-234">Use the `MLContext.BinaryClassification.TrainTestSplit` which wraps <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> to split the loaded dataset into train and test datasets and return them inside of a <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span></span> <span data-ttu-id="8e78e-235">Část dat můžete zadat nastavení testu s `testFraction`parametru.</span><span class="sxs-lookup"><span data-stu-id="8e78e-235">You can specify the fraction of data for the test set with the `testFraction`parameter.</span></span> <span data-ttu-id="8e78e-236">Výchozí hodnota je 10 %, ale v tomto případě použijte 20 % používat další data pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="8e78e-236">The default is 10% but you use 20% in this case to use more data for the evaluation.</span></span>  

<span data-ttu-id="8e78e-237">Načtená data rozdělením potřebné datové sady, přidejte následující kód jako další řádek `LoadData` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-237">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData` method:</span></span>

[!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="8e78e-238">Vrátit `splitDataView` na konci `LoadData` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-238">Return the `splitDataView` at the end of the `LoadData` method:</span></span>

[!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="8e78e-239">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-239">Build and train the model</span></span>

<span data-ttu-id="8e78e-240">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-240">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="8e78e-241">`BuildAndTrainModel` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8e78e-241">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="8e78e-242">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-242">Extracts and transforms the data.</span></span>
* <span data-ttu-id="8e78e-243">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-243">Trains the model.</span></span>
* <span data-ttu-id="8e78e-244">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-244">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="8e78e-245">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-245">Returns the model.</span></span>

<span data-ttu-id="8e78e-246">Vytvořte `BuildAndTrainModel` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-246">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

<span data-ttu-id="8e78e-247">Všimněte si, že dva parametry jsou předány do metody trénování; `MLContext` kontextu (`mlContext`) a `IDataView`pro trénovací datové sady (`splitTrainSet`).</span><span class="sxs-lookup"><span data-stu-id="8e78e-247">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and an `IDataView`for the training dataset (`splitTrainSet`).</span></span> 

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="8e78e-248">Extrahovat a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-248">Extract and transform the data</span></span>

<span data-ttu-id="8e78e-249">Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="8e78e-249">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="8e78e-250">Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8e78e-250">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="8e78e-251">Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-251">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="8e78e-252">ML. Kanály transformace vaší sítě vytvořit vlastní sadu transformací, které se použijí pro vaše data před trénování a testování.</span><span class="sxs-lookup"><span data-stu-id="8e78e-252">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="8e78e-253">Hlavním účelem transformace jsou data [snadné](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="8e78e-253">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="8e78e-254">Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) data, abyste dalším krokem je získat z našich algoritmů ML rozpoznat formát naše textová data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-254">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="8e78e-255">Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="8e78e-255">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="8e78e-256">Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` které featurizes textového sloupce (`SentimentText`) sloupec jako číselný vektor nazývá `Features` používá algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="8e78e-256">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="8e78e-257">Toto je obálka volání, které se vrátí <xref:Microsoft.ML.Data.EstimatorChain%601> efektivně, který bude kanál.</span><span class="sxs-lookup"><span data-stu-id="8e78e-257">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="8e78e-258">Pojmenujte toto `pipeline` jako se pak připojí trainer k `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="8e78e-258">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="8e78e-259">Přidáte jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-259">Add this as the next line of code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> <span data-ttu-id="8e78e-260">ML.NET verze 0.10 změnit pořadí parametrů transformace.</span><span class="sxs-lookup"><span data-stu-id="8e78e-260">ML.NET Version 0.10 changed the order of the Transform parameters.</span></span> <span data-ttu-id="8e78e-261">Tímto krokem se nevygeneruje chybu, dokud při spuštění aplikace a vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-261">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="8e78e-262">Použijte názvy parametrů transformací, jak je znázorněno v předchozím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-262">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="8e78e-263">Jedná se o krok předběžného zpracování a snadné.</span><span class="sxs-lookup"><span data-stu-id="8e78e-263">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="8e78e-264">Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.</span><span class="sxs-lookup"><span data-stu-id="8e78e-264">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="8e78e-265">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="8e78e-265">Choose a learning algorithm</span></span>

<span data-ttu-id="8e78e-266">Přidáte školitele volání `mlContext.BinaryClassification.Trainers.FastTree` obalující metodu, která vrátí hodnotu <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> objektu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-266">To add the trainer, call the `mlContext.BinaryClassification.Trainers.FastTree` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="8e78e-267">Toto je learner stromu rozhodnutí, které budete používat v tomto kanálu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-267">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="8e78e-268">`FastTreeBinaryClassificationTrainer` Se připojí `pipeline` a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="8e78e-268">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="8e78e-269">Přidejte následující kód, který `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-269">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="8e78e-270">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-270">Train the model</span></span>

<span data-ttu-id="8e78e-271">Trénování modelu, <xref:Microsoft.ML.Data.TransformerChain%601>založená na datovou sadu, která má načíst a transformovat.</span><span class="sxs-lookup"><span data-stu-id="8e78e-271">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="8e78e-272">Po definování odhadu tréninku modelu pomocí <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> metoda současně už načtený trénovací data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-272">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> method while providing the already loaded training data.</span></span> <span data-ttu-id="8e78e-273">Vrátí model pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="8e78e-273">This returns a model to use for predictions.</span></span> `pipeline.Fit()` <span data-ttu-id="8e78e-274">trénovat kanálu a vrátí `Transformer` na základě `DataView` předán.</span><span class="sxs-lookup"><span data-stu-id="8e78e-274">trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="8e78e-275">Dokud není spuštěn experimentu `.Fit()` metoda spuštění.</span><span class="sxs-lookup"><span data-stu-id="8e78e-275">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="8e78e-276">Přidejte následující kód, který `BuildAndTrainModel` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-276">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="8e78e-277">Uložte a vraťte se model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="8e78e-277">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="8e78e-278">V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain%601> , který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="8e78e-278">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="8e78e-279">Model na konci vrátit `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="8e78e-279">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="8e78e-280">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-280">Evaluate the model</span></span>

<span data-ttu-id="8e78e-281">Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování.</span><span class="sxs-lookup"><span data-stu-id="8e78e-281">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="8e78e-282">V `Evaluate` metody, vytvořené v modelu `BuildAndTrainModel` předaný k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="8e78e-282">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="8e78e-283">Vytvořte `Evaluate` metoda, hned za `BuildAndTrainModel`, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-283">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="8e78e-284">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8e78e-284">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="8e78e-285">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="8e78e-285">Loads the test dataset.</span></span>
* <span data-ttu-id="8e78e-286">Chyba při vyhodnocování binaryclassification vytvoří.</span><span class="sxs-lookup"><span data-stu-id="8e78e-286">Creates the binaryclassification evaluator.</span></span>
* <span data-ttu-id="8e78e-287">Vyhodnotí modelu a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-287">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="8e78e-288">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-288">Displays the metrics.</span></span>

<span data-ttu-id="8e78e-289">Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-289">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="8e78e-290">V dalším kroku budete pomocí machine learning `model` parametr (transformace) a `splitTestSet` parametr pro vstup funkce a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="8e78e-290">Next, you'll use the machine learning `model` parameter (a transformer) and the `splitTestSet` parameter to input the features and return predictions.</span></span> <span data-ttu-id="8e78e-291">Přidejte následující kód, který `Evaluate` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="8e78e-291">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="8e78e-292">`mlContext.BinaryClassification.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="8e78e-292">The `mlContext.BinaryClassification.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="8e78e-293">Vrátí <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="8e78e-293">It returns a <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> object that contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="8e78e-294">Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první.</span><span class="sxs-lookup"><span data-stu-id="8e78e-294">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="8e78e-295">Přidejte následující kód jako další řádek `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-295">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="8e78e-296">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-296">Displaying the metrics for model validation</span></span>

<span data-ttu-id="8e78e-297">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="8e78e-297">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

<span data-ttu-id="8e78e-298">Pokud chcete uložit model do souboru ZIP a teprve potom se informuje, přidejte následující kód k volání `SaveModelAsFile` metody jako další řádek v `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="8e78e-298">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="8e78e-299">Uložit jako soubor a.zip model</span><span class="sxs-lookup"><span data-stu-id="8e78e-299">Save the model as a.zip file</span></span>

<span data-ttu-id="8e78e-300">Vytvořte `SaveModelAsFile` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-300">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="8e78e-301">`SaveModelAsFile` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8e78e-301">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="8e78e-302">Uloží modelu ve formě souboru .zip.</span><span class="sxs-lookup"><span data-stu-id="8e78e-302">Saves the model as a .zip file.</span></span>

<span data-ttu-id="8e78e-303">Dále vytvořte metodu k uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="8e78e-303">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="8e78e-304">`ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="8e78e-304">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="8e78e-305">Uložit jako soubor zip, vytvoříte `FileStream` bezprostředně před volání `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="8e78e-305">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="8e78e-306">Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="8e78e-306">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

<span data-ttu-id="8e78e-307">Může také zobrazit, kde soubor byl zapsán napsáním zprávu konzoly `_modelPath`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-307">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="8e78e-308">Předpověď data výsledek testu s modelem uložené</span><span class="sxs-lookup"><span data-stu-id="8e78e-308">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="8e78e-309">Vytvořte `UseModelWithSingleItem` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-309">Create the `UseModelWithSingleItem` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="8e78e-310">`UseModelWithSingleItem` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8e78e-310">The `UseModelWithSingleItem` method executes the following tasks:</span></span>

* <span data-ttu-id="8e78e-311">Vytvoří jeden komentář testovací data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-311">Creates a single comment of test data.</span></span>
* <span data-ttu-id="8e78e-312">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-312">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="8e78e-313">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="8e78e-313">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="8e78e-314">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-314">Displays the predicted results.</span></span>

<span data-ttu-id="8e78e-315">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-315">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="8e78e-316">Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, je potřeba k předpovědím na jednotlivé příklady o velmi běžný scénář produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="8e78e-316">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="8e78e-317"><xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="8e78e-317">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="8e78e-318">Přidejte následující kód k vytvoření `PredictionEngine` jako první řádek `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-318">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
<span data-ttu-id="8e78e-319">Přidejte komentář k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="8e78e-319">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 <span data-ttu-id="8e78e-320">Který můžete použít k predikci kladné nebo záporné mínění jednu instanci data komentáře.</span><span class="sxs-lookup"><span data-stu-id="8e78e-320">You can use that to predict the positive or negative sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="8e78e-321">Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-321">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="8e78e-322">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="8e78e-322">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="8e78e-323">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="8e78e-323">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="8e78e-324">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="8e78e-324">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a><span data-ttu-id="8e78e-325">Použití modelu: předpověď</span><span class="sxs-lookup"><span data-stu-id="8e78e-325">Use the model: prediction</span></span>

<span data-ttu-id="8e78e-326">Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="8e78e-326">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="8e78e-327">Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady.</span><span class="sxs-lookup"><span data-stu-id="8e78e-327">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="8e78e-328">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-328">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="8e78e-329">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="8e78e-329">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="8e78e-330">Vytvořte `UseLoadedModelWithBatchItems` metoda, těsně před `SaveModelAsFile` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-330">Create the `UseLoadedModelWithBatchItems` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="8e78e-331">`UseLoadedModelWithBatchItems` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8e78e-331">The `UseLoadedModelWithBatchItems` method executes the following tasks:</span></span>

* <span data-ttu-id="8e78e-332">Vytvoří služby batch testovací data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-332">Creates batch test data.</span></span>
* <span data-ttu-id="8e78e-333">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="8e78e-333">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="8e78e-334">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="8e78e-334">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="8e78e-335">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="8e78e-335">Displays the predicted results.</span></span>

<span data-ttu-id="8e78e-336">Přidejte volání do nové metody z `Main` metody, v rámci `UseModelWithSingleItem` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-336">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

<span data-ttu-id="8e78e-337">Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `UseLoadedModelWithBatchItems` metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-337">Add some comments to test the trained model's predictions in the `UseLoadedModelWithBatchItems` method:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

<span data-ttu-id="8e78e-338">Načíst model</span><span class="sxs-lookup"><span data-stu-id="8e78e-338">Load the model</span></span>

[!code-csharp[LoadTheModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

<span data-ttu-id="8e78e-339">Teď, když máte model, vám pomůže, která předvídat toxické nebo jiných toxické mínění komentář dat pomocí <xref:Microsoft.ML.ITransformer.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8e78e-339">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="8e78e-340">Chcete-li získat predikcí, použijte `Predict` na nová data.</span><span class="sxs-lookup"><span data-stu-id="8e78e-340">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="8e78e-341">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="8e78e-341">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="8e78e-342">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="8e78e-342">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="8e78e-343">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="8e78e-343">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="8e78e-344">Přidejte následující kód, který `UseLoadedModelWithBatchItems` metodu předpovědí:</span><span class="sxs-lookup"><span data-stu-id="8e78e-344">Add the following code to the `UseLoadedModelWithBatchItems` method for the predictions:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a><span data-ttu-id="8e78e-345">Použít načíst model pro předpověď</span><span class="sxs-lookup"><span data-stu-id="8e78e-345">Use the loaded model for prediction</span></span>

<span data-ttu-id="8e78e-346">Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="8e78e-346">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="8e78e-347">Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady.</span><span class="sxs-lookup"><span data-stu-id="8e78e-347">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="8e78e-348">Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="8e78e-348">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="8e78e-349">Před zobrazením předpokládané výsledky, kombinovat mínění a predikcí společně zobrazíte původním komentářem s jeho predikované mínění.</span><span class="sxs-lookup"><span data-stu-id="8e78e-349">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="8e78e-350">Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda docílit, vedle proto přidejte tento kód:</span><span class="sxs-lookup"><span data-stu-id="8e78e-350">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="8e78e-351">Teď, když jste kombinovat `SentimentText` a `Sentiment` do třídy, můžete zobrazit výsledky pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="8e78e-351">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

<span data-ttu-id="8e78e-352">Protože odvozené názvy elementů řazené kolekce členů se, že je nová funkce v jazyce C# 7.1 a výchozí jazyková verze projektu C# 7.0, potřebujete změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="8e78e-352">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="8e78e-353">To mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-353">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="8e78e-354">Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8e78e-354">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="8e78e-355">V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="8e78e-355">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="8e78e-356">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e78e-356">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="8e78e-357">Výsledky</span><span class="sxs-lookup"><span data-stu-id="8e78e-357">Results</span></span>

<span data-ttu-id="8e78e-358">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="8e78e-358">Your results should be similar to the following.</span></span> <span data-ttu-id="8e78e-359">Při zpracování kanálu zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="8e78e-359">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="8e78e-360">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="8e78e-360">You may see warnings, or processing messages.</span></span> <span data-ttu-id="8e78e-361">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="8e78e-361">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="8e78e-362">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="8e78e-362">Congratulations!</span></span> <span data-ttu-id="8e78e-363">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění.</span><span class="sxs-lookup"><span data-stu-id="8e78e-363">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> 

<span data-ttu-id="8e78e-364">Vytváření modelů po úspěšné je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="8e78e-364">Building successful models is an iterative process.</span></span> <span data-ttu-id="8e78e-365">Tento model má nižší počáteční kvalita jako kurz používá malé datové sady poskytují rychlý model školení.</span><span class="sxs-lookup"><span data-stu-id="8e78e-365">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="8e78e-366">Pokud si nejste spokojeni s kvalitou modelu, můžete ho vylepšit tím, že poskytuje větší cvičných datových sad nebo výběrem jiné školení algoritmy s jinou hyperparametry pro jednotlivé algoritmy.</span><span class="sxs-lookup"><span data-stu-id="8e78e-366">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span>

<span data-ttu-id="8e78e-367">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="8e78e-367">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8e78e-368">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8e78e-368">Next steps</span></span>

<span data-ttu-id="8e78e-369">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="8e78e-369">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8e78e-370">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="8e78e-370">Understand the problem</span></span>
> * <span data-ttu-id="8e78e-371">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="8e78e-371">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="8e78e-372">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-372">Prepare your data</span></span>
> * <span data-ttu-id="8e78e-373">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="8e78e-373">Transform the data</span></span>
> * <span data-ttu-id="8e78e-374">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-374">Train the model</span></span>
> * <span data-ttu-id="8e78e-375">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-375">Evaluate the model</span></span>
> * <span data-ttu-id="8e78e-376">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="8e78e-376">Predict with the trained model</span></span>
> * <span data-ttu-id="8e78e-377">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="8e78e-377">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="8e78e-378">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="8e78e-378">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8e78e-379">Klasifikace problému</span><span class="sxs-lookup"><span data-stu-id="8e78e-379">Issue Classification</span></span>](github-issue-classification.md)
