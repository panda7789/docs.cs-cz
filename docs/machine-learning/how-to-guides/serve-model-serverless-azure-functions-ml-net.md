---
title: Nasazení modelu do Azure Functions
description: Obsluha modelu ML.NET mínění Analysis Machine Learning pro předpověď přes Internet pomocí Azure Functions
ms.date: 09/12/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2abd8588aa314b630c995e0c78b5869ec00a89df
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179365"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="d2192-103">Nasazení modelu do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="d2192-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="d2192-104">Naučte se, jak nasadit předem vyškolený model ML.NET Machine Learning pro předpovědi přes protokol HTTP prostřednictvím prostředí bez serveru Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="d2192-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="d2192-105">rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="d2192-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2192-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2192-106">Prerequisites</span></span>

- <span data-ttu-id="d2192-107">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "vývoj pro různé platformy pro .NET Core" a "vývoj pro Azure".</span><span class="sxs-lookup"><span data-stu-id="d2192-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="d2192-108">Microsoft. NET. SDK. Functions Package NuGet verze 1.0.28 +.</span><span class="sxs-lookup"><span data-stu-id="d2192-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="d2192-109">Nástroje Azure Functions</span><span class="sxs-lookup"><span data-stu-id="d2192-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="d2192-110">Prostředí</span><span class="sxs-lookup"><span data-stu-id="d2192-110">Powershell</span></span>
- <span data-ttu-id="d2192-111">Předem vyškolený model.</span><span class="sxs-lookup"><span data-stu-id="d2192-111">Pre-trained model.</span></span> <span data-ttu-id="d2192-112">Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s představitelnou mínění analýzou](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) .</span><span class="sxs-lookup"><span data-stu-id="d2192-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="d2192-113">Vytvořit Azure Functions projekt</span><span class="sxs-lookup"><span data-stu-id="d2192-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="d2192-114">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d2192-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="d2192-115">Z řádku nabídek vyberte **soubor** > **Nový** **projekt**  > .</span><span class="sxs-lookup"><span data-stu-id="d2192-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="d2192-116">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **cloudu** .</span><span class="sxs-lookup"><span data-stu-id="d2192-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="d2192-117">Pak vyberte šablonu projektu **Azure Functions** .</span><span class="sxs-lookup"><span data-stu-id="d2192-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="d2192-118">Do textového pole **název** zadejte "SentimentAnalysisFunctionsApp" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="d2192-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="d2192-119">V dialogovém okně **Nový projekt** otevřete rozevírací seznam nad možnostmi projektu a vyberte **Azure Functions v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="d2192-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="d2192-120">Pak vyberte projekt **triggeru http** a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="d2192-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="d2192-121">Vytvořte v projektu adresář s názvem *MLModels* a uložte svůj model:</span><span class="sxs-lookup"><span data-stu-id="d2192-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="d2192-122">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **přidat** **novou složku** > .</span><span class="sxs-lookup"><span data-stu-id="d2192-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="d2192-123">Zadejte "MLModels" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d2192-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="d2192-124">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="d2192-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="d2192-125">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d2192-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d2192-126">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d2192-127">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="d2192-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="d2192-128">Nainstalujte **balíček NuGet Microsoft. Azure. Functions. Extensions**:</span><span class="sxs-lookup"><span data-stu-id="d2192-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="d2192-129">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d2192-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d2192-130">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft. Azure. Functions. Extensions**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d2192-131">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="d2192-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="d2192-132">Nainstalujte **balíček NuGet Microsoft.Extensions.ml**:</span><span class="sxs-lookup"><span data-stu-id="d2192-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="d2192-133">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d2192-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d2192-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d2192-135">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="d2192-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="d2192-136">Aktualizujte **balíček NuGet Microsoft. NET. SDK. Functions** na verzi 1.0.28 +:</span><span class="sxs-lookup"><span data-stu-id="d2192-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28+:</span></span>

    <span data-ttu-id="d2192-137">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d2192-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d2192-138">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu nainstalované, vyhledejte **Microsoft. NET. SDK. Functions**, vyberte tento balíček v seznamu, vyberte v rozevírací nabídce verze možnost 1.0.28 nebo novější a klikněte na tlačítko **aktualizovat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="d2192-139">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="d2192-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="d2192-140">Přidat předem vyškolený model do projektu</span><span class="sxs-lookup"><span data-stu-id="d2192-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="d2192-141">Do složky *MLModels* zkopírujte předem sestavený model.</span><span class="sxs-lookup"><span data-stu-id="d2192-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="d2192-142">V Průzkumník řešení klikněte pravým tlačítkem na předem sestavený soubor modelu a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d2192-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="d2192-143">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="d2192-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="d2192-144">Vytvoření funkce Azure pro analýzu mínění</span><span class="sxs-lookup"><span data-stu-id="d2192-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="d2192-145">Vytvořte třídu pro předpověď mínění.</span><span class="sxs-lookup"><span data-stu-id="d2192-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="d2192-146">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="d2192-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="d2192-147">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .</span><span class="sxs-lookup"><span data-stu-id="d2192-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d2192-148">V dialogovém okně **Přidat novou položku** vyberte možnost **Azure Functions** a změňte pole **název** na *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="d2192-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="d2192-149">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="d2192-150">V dialogovém okně **Nová funkce Azure** vyberte **Trigger http**.</span><span class="sxs-lookup"><span data-stu-id="d2192-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="d2192-151">Pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="d2192-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="d2192-152">V editoru kódu se otevře soubor *AnalyzeSentiment.cs* .</span><span class="sxs-lookup"><span data-stu-id="d2192-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="d2192-153">Přidejte následující příkaz `using` do horní části *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="d2192-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="d2192-154">Ve výchozím nastavení je třída `AnalyzeSentiment` `static`.</span><span class="sxs-lookup"><span data-stu-id="d2192-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="d2192-155">Nezapomeňte z definice třídy odebrat klíčové slovo `static`.</span><span class="sxs-lookup"><span data-stu-id="d2192-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="d2192-156">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="d2192-156">Create data models</span></span>

<span data-ttu-id="d2192-157">Musíte vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="d2192-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="d2192-158">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="d2192-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="d2192-159">Vytvořte v projektu adresář s názvem *Datamodels* pro uložení datových modelů: v Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="d2192-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="d2192-160">Zadejte "datamodels" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="d2192-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="d2192-161">V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="d2192-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="d2192-162">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d2192-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="d2192-163">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="d2192-164">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="d2192-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d2192-165">Do horní části *SentimentData.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="d2192-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="d2192-166">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="d2192-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="d2192-167">V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="d2192-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="d2192-168">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="d2192-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="d2192-169">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-169">Then, select the **Add** button.</span></span> <span data-ttu-id="d2192-170">V editoru kódu se otevře soubor *SentimentPrediction.cs* .</span><span class="sxs-lookup"><span data-stu-id="d2192-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="d2192-171">Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="d2192-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="d2192-172">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="d2192-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="d2192-173">`SentimentPrediction` dědí z `SentimentData`, který poskytuje přístup k původním datům ve vlastnosti `SentimentText` a také výstup generovaný modelem.</span><span class="sxs-lookup"><span data-stu-id="d2192-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="d2192-174">Zaregistrovat službu PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="d2192-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="d2192-175">Chcete-li udělat jednu předpověď, je nutné vytvořit [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="d2192-175">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="d2192-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="d2192-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="d2192-177">Kromě toho musíte vytvořit instanci, která je všude, kde je to potřeba v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2192-177">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="d2192-178">Jak vaše aplikace roste, tento proces může být nespravovatelný.</span><span class="sxs-lookup"><span data-stu-id="d2192-178">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="d2192-179">Pro zlepšení výkonu a zabezpečení vlákna použijte kombinaci injektáže a `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2192-179">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="d2192-180">Následující odkaz poskytuje další informace, pokud se chcete dozvědět víc o [vkládání závislostí](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="d2192-180">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="d2192-181">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .</span><span class="sxs-lookup"><span data-stu-id="d2192-181">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d2192-182">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="d2192-182">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="d2192-183">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="d2192-183">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="d2192-184">V editoru kódu se otevře soubor *Startup.cs* .</span><span class="sxs-lookup"><span data-stu-id="d2192-184">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="d2192-185">Do horní části *Startup.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="d2192-185">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="d2192-186">Odeberte existující kód pod příkazy using a přidejte následující kód do souboru *Startup.cs* :</span><span class="sxs-lookup"><span data-stu-id="d2192-186">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
            }
        }
    }
    ```

<span data-ttu-id="d2192-187">Na vysoké úrovni tento kód automaticky inicializuje objekty a služby pro pozdější použití v případě, že je aplikace požaduje místo ručního provedení.</span><span class="sxs-lookup"><span data-stu-id="d2192-187">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span> 

<span data-ttu-id="d2192-188">Modely strojového učení nejsou statické.</span><span class="sxs-lookup"><span data-stu-id="d2192-188">Machine learning models are not static.</span></span> <span data-ttu-id="d2192-189">Jakmile budou k dispozici nová školicí data, model se přeškolí a znovu nasadí.</span><span class="sxs-lookup"><span data-stu-id="d2192-189">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="d2192-190">Jedním ze způsobů, jak získat nejnovější verzi modelu do vaší aplikace, je znovu nasadit celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2192-190">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="d2192-191">Tím se ale zavádí výpadek aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2192-191">However, this introduces application downtime.</span></span> <span data-ttu-id="d2192-192">Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti pořizovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2192-192">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span> 

<span data-ttu-id="d2192-193">Nastavte parametr `watchForChanges` na `true` a `PredictionEnginePool` spustí [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , které naslouchají oznámením o změnách systému souborů a vyvolává události, když dojde ke změně souboru.</span><span class="sxs-lookup"><span data-stu-id="d2192-193">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="d2192-194">Tím se zobrazí výzva `PredictionEnginePool` pro automatické opětovné načtení modelu.</span><span class="sxs-lookup"><span data-stu-id="d2192-194">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="d2192-195">Model je identifikován parametrem `modelName`, aby bylo při změně možné znovu načíst více než jeden model na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2192-195">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span> 

> [!TIP]
> <span data-ttu-id="d2192-196">Alternativně můžete použít metodu `FromUri` při práci s místně uloženými modely.</span><span class="sxs-lookup"><span data-stu-id="d2192-196">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="d2192-197">Místo sledování událostí změněných souborů `FromUri` se dotazuje na vzdálené umístění pro změny.</span><span class="sxs-lookup"><span data-stu-id="d2192-197">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="d2192-198">Interval dotazování je ve výchozím nastavení nastaven na 5 minut.</span><span class="sxs-lookup"><span data-stu-id="d2192-198">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="d2192-199">Interval dotazování můžete zvýšit nebo snížit na základě požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2192-199">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="d2192-200">V níže uvedeném příkladu kódu `PredictionEnginePool` cyklické dotazování modelu uloženého v zadaném identifikátoru URI každou minutu.</span><span class="sxs-lookup"><span data-stu-id="d2192-200">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>    
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel", 
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip", 
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="d2192-201">Načtení modelu do funkce</span><span class="sxs-lookup"><span data-stu-id="d2192-201">Load the model into the function</span></span>

<span data-ttu-id="d2192-202">Do třídy *AnalyzeSentiment* vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="d2192-202">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="d2192-203">Tento kód přiřadí `PredictionEnginePool` předáním do konstruktoru funkce, který získáte prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="d2192-203">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="d2192-204">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="d2192-204">Use the model to make predictions</span></span>

<span data-ttu-id="d2192-205">Nahraďte stávající implementaci metody *Run* ve třídě *AnalyzeSentiment* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d2192-205">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="d2192-206">Když se spustí metoda `Run`, jsou příchozí data z požadavku HTTP deserializovaná a slouží jako vstup pro `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="d2192-206">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="d2192-207">Metoda `Predict` je pak volána k provedení předpovědi pomocí `SentimentAnalysisModel` zaregistrovaného ve třídě `Startup` a vrátí výsledky zpět uživateli, pokud bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d2192-207">The `Predict` method is then called to to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="d2192-208">Test lokálně</span><span class="sxs-lookup"><span data-stu-id="d2192-208">Test locally</span></span>

<span data-ttu-id="d2192-209">Teď, když je všechno nastavené, je čas otestovat aplikaci:</span><span class="sxs-lookup"><span data-stu-id="d2192-209">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="d2192-210">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="d2192-210">Run the application</span></span>
1. <span data-ttu-id="d2192-211">Otevřete PowerShell a zadejte kód do příkazového řádku, kde PORT je port, na kterém je vaše aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="d2192-211">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="d2192-212">Obvykle je port 7071.</span><span class="sxs-lookup"><span data-stu-id="d2192-212">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="d2192-213">V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:</span><span class="sxs-lookup"><span data-stu-id="d2192-213">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="d2192-214">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="d2192-214">Congratulations!</span></span> <span data-ttu-id="d2192-215">Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí funkce Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="d2192-215">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d2192-216">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d2192-216">Next Steps</span></span>

- [<span data-ttu-id="d2192-217">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="d2192-217">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
