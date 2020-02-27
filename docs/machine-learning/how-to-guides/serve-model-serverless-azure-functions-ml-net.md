---
title: Nasazení modelu do Azure Functions
description: Obsluha modelu ML.NET mínění Analysis Machine Learning pro předpověď přes Internet pomocí Azure Functions
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33afd568bb12b855a3888bec31f2e9bbc3c720da
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628667"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="80000-103">Nasazení modelu do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="80000-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="80000-104">Naučte se, jak nasadit předem vyškolený model ML.NET Machine Learning pro předpovědi přes protokol HTTP prostřednictvím prostředí bez serveru Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="80000-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="80000-105">Tato ukázka spustí verzi Preview služby `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="80000-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80000-106">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="80000-106">Prerequisites</span></span>

- <span data-ttu-id="80000-107">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "vývoj pro různé platformy .NET Core" a "vývoj pro Azure".</span><span class="sxs-lookup"><span data-stu-id="80000-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="80000-108">Nástroje Azure Functions</span><span class="sxs-lookup"><span data-stu-id="80000-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="80000-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="80000-109">Powershell</span></span>
- <span data-ttu-id="80000-110">Předem vyškolený model.</span><span class="sxs-lookup"><span data-stu-id="80000-110">Pre-trained model.</span></span> <span data-ttu-id="80000-111">Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s představitelnou mínění analýzou](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) .</span><span class="sxs-lookup"><span data-stu-id="80000-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="80000-112">Přehled ukázek Azure Functions</span><span class="sxs-lookup"><span data-stu-id="80000-112">Azure Functions sample overview</span></span>

<span data-ttu-id="80000-113">Tato ukázka je  **C# triggerem http Azure Functions aplikaci** , která používá předmínění binární klasifikační model pro kategorizaci textu jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="80000-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="80000-114">Azure Functions poskytuje snadný způsob, jak na spravovaném prostředí bez serveru v cloudu spouštět malé části kódu se škálováním.</span><span class="sxs-lookup"><span data-stu-id="80000-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="80000-115">Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="80000-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="80000-116">Vytvořit Azure Functions projekt</span><span class="sxs-lookup"><span data-stu-id="80000-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="80000-117">Otevřete sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="80000-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="80000-118">Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="80000-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="80000-119">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **cloudu** .</span><span class="sxs-lookup"><span data-stu-id="80000-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="80000-120">Pak vyberte šablonu projektu **Azure Functions** .</span><span class="sxs-lookup"><span data-stu-id="80000-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="80000-121">Do textového pole **název** zadejte "SentimentAnalysisFunctionsApp" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="80000-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="80000-122">V dialogovém okně **Nový projekt** otevřete rozevírací seznam nad možnostmi projektu a vyberte **Azure Functions v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="80000-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="80000-123">Pak vyberte projekt **triggeru http** a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="80000-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="80000-124">Vytvořte v projektu adresář s názvem *MLModels* a uložte svůj model:</span><span class="sxs-lookup"><span data-stu-id="80000-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="80000-125">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="80000-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="80000-126">Zadejte "MLModels" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="80000-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="80000-127">Nainstalujte **balíček NuGet Microsoft.ml** verze **1.3.1**:</span><span class="sxs-lookup"><span data-stu-id="80000-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="80000-128">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="80000-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="80000-129">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="80000-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="80000-130">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="80000-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="80000-131">Nainstalujte **balíček NuGet Microsoft. Azure. Functions. Extensions**:</span><span class="sxs-lookup"><span data-stu-id="80000-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="80000-132">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="80000-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="80000-133">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft. Azure. Functions. Extensions**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="80000-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="80000-134">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="80000-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="80000-135">Nainstalujte **balíček NuGet Microsoft.Extensions.ml** verze **0.15.1**:</span><span class="sxs-lookup"><span data-stu-id="80000-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="80000-136">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="80000-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="80000-137">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="80000-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="80000-138">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="80000-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="80000-139">Nainstalujte **balíček NuGet Microsoft. NET. SDK. Functions** verze **1.0.31**:</span><span class="sxs-lookup"><span data-stu-id="80000-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="80000-140">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="80000-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="80000-141">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu nainstalované, vyhledejte **Microsoft. NET. SDK. Functions**, vyberte tento balíček v seznamu, vyberte v rozevírací nabídce verze možnost **1.0.31** a klikněte na tlačítko **aktualizovat** .</span><span class="sxs-lookup"><span data-stu-id="80000-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="80000-142">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="80000-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="80000-143">Přidat předem vyškolený model do projektu</span><span class="sxs-lookup"><span data-stu-id="80000-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="80000-144">Do složky *MLModels* zkopírujte předem sestavený model.</span><span class="sxs-lookup"><span data-stu-id="80000-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="80000-145">V Průzkumník řešení klikněte pravým tlačítkem na předem sestavený soubor modelu a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="80000-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="80000-146">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="80000-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="80000-147">Vytvoření funkce Azure pro analýzu mínění</span><span class="sxs-lookup"><span data-stu-id="80000-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="80000-148">Vytvořte třídu pro předpověď mínění.</span><span class="sxs-lookup"><span data-stu-id="80000-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="80000-149">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="80000-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="80000-150">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="80000-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="80000-151">V dialogovém okně **Přidat novou položku** vyberte možnost **Azure Functions** a změňte pole **název** na *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="80000-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="80000-152">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="80000-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="80000-153">V dialogovém okně **Nová funkce Azure** vyberte **Trigger http**.</span><span class="sxs-lookup"><span data-stu-id="80000-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="80000-154">Pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="80000-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="80000-155">V editoru kódu se otevře soubor *AnalyzeSentiment.cs* .</span><span class="sxs-lookup"><span data-stu-id="80000-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="80000-156">Do horní části *AnalyzeSentiment.cs*přidejte následující příkaz `using`:</span><span class="sxs-lookup"><span data-stu-id="80000-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="80000-157">Ve výchozím nastavení je třída `AnalyzeSentiment` `static`.</span><span class="sxs-lookup"><span data-stu-id="80000-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="80000-158">Nezapomeňte odebrat klíčové slovo `static` z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="80000-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="80000-159">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="80000-159">Create data models</span></span>

<span data-ttu-id="80000-160">Musíte vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="80000-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="80000-161">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="80000-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="80000-162">Vytvořte v projektu adresář s názvem *Datamodels* pro uložení datových modelů: v Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="80000-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="80000-163">Zadejte "datamodels" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="80000-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="80000-164">V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="80000-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="80000-165">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="80000-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="80000-166">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="80000-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="80000-167">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="80000-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="80000-168">Do horní části *SentimentData.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="80000-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="80000-169">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="80000-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="80000-170">V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="80000-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="80000-171">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="80000-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="80000-172">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="80000-172">Then, select the **Add** button.</span></span> <span data-ttu-id="80000-173">V editoru kódu se otevře soubor *SentimentPrediction.cs* .</span><span class="sxs-lookup"><span data-stu-id="80000-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="80000-174">Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="80000-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="80000-175">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="80000-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="80000-176">`SentimentPrediction` dědí z `SentimentData`, která poskytuje přístup k původním datům ve vlastnosti `SentimentText`, a také výstup generovaný modelem.</span><span class="sxs-lookup"><span data-stu-id="80000-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="80000-177">Zaregistrovat službu PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="80000-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="80000-178">Chcete-li udělat jednu předpověď, je nutné vytvořit [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="80000-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="80000-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="80000-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="80000-180">Kromě toho musíte vytvořit instanci, která je všude, kde je to potřeba v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="80000-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="80000-181">Jak vaše aplikace roste, tento proces může být nespravovatelný.</span><span class="sxs-lookup"><span data-stu-id="80000-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="80000-182">Pro zlepšení výkonu a bezpečnosti vláken použijte kombinaci injektáže a `PredictionEnginePool` služby, která vytváří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="80000-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="80000-183">Následující odkaz poskytuje další informace, pokud se chcete dozvědět víc o [vkládání závislostí](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="80000-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="80000-184">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="80000-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="80000-185">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="80000-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="80000-186">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="80000-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="80000-187">Do horní části *Startup.cs*přidejte následující příkazy using:</span><span class="sxs-lookup"><span data-stu-id="80000-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="80000-188">Odeberte existující kód pod příkazy using a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="80000-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="80000-189">Definujte proměnné pro ukládání prostředí, ve kterém je aplikace spuštěná, a cesta k souboru, kde je model umístěný uvnitř `Startup` třídy.</span><span class="sxs-lookup"><span data-stu-id="80000-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="80000-190">Níže Vytvořte konstruktor pro nastavení hodnot `_environment` a `_modelPath` proměnných.</span><span class="sxs-lookup"><span data-stu-id="80000-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="80000-191">Když je aplikace spuštěná místně, je výchozím prostředím *vývoj*.</span><span class="sxs-lookup"><span data-stu-id="80000-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="80000-192">Pak přidejte novou metodu nazvanou `Configure` k registraci služby `PredictionEnginePool` pod konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="80000-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="80000-193">Na vysoké úrovni tento kód automaticky inicializuje objekty a služby pro pozdější použití v případě, že je aplikace požaduje místo ručního provedení.</span><span class="sxs-lookup"><span data-stu-id="80000-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="80000-194">Modely strojového učení nejsou statické.</span><span class="sxs-lookup"><span data-stu-id="80000-194">Machine learning models are not static.</span></span> <span data-ttu-id="80000-195">Jakmile budou k dispozici nová školicí data, model se přeškolí a znovu nasadí.</span><span class="sxs-lookup"><span data-stu-id="80000-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="80000-196">Jedním ze způsobů, jak získat nejnovější verzi modelu do vaší aplikace, je znovu nasadit celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="80000-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="80000-197">Tím se ale zavádí výpadek aplikace.</span><span class="sxs-lookup"><span data-stu-id="80000-197">However, this introduces application downtime.</span></span> <span data-ttu-id="80000-198">Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti pořizovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="80000-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="80000-199">Nastavte parametr `watchForChanges` na `true`a `PredictionEnginePool` spustí [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , který čeká na oznámení o změnách systému souborů a vyvolává události, když dojde ke změně souboru.</span><span class="sxs-lookup"><span data-stu-id="80000-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="80000-200">Tím se zobrazí výzva `PredictionEnginePool`, aby se model automaticky znovu načítat.</span><span class="sxs-lookup"><span data-stu-id="80000-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="80000-201">Model je identifikován parametrem `modelName`, aby bylo po změně možné znovu načíst více než jeden model na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="80000-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="80000-202">Alternativně můžete při práci s modely uloženými vzdáleně použít metodu `FromUri`.</span><span class="sxs-lookup"><span data-stu-id="80000-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="80000-203">Místo sledování událostí změněných souborů `FromUri` dotazuje vzdálené umístění pro změny.</span><span class="sxs-lookup"><span data-stu-id="80000-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="80000-204">Interval dotazování je ve výchozím nastavení nastaven na 5 minut.</span><span class="sxs-lookup"><span data-stu-id="80000-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="80000-205">Interval dotazování můžete zvýšit nebo snížit na základě požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="80000-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="80000-206">V níže uvedeném příkladu kódu `PredictionEnginePool` dotazuje model uložený v zadaném identifikátoru URI každou minutu.</span><span class="sxs-lookup"><span data-stu-id="80000-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="80000-207">Načtení modelu do funkce</span><span class="sxs-lookup"><span data-stu-id="80000-207">Load the model into the function</span></span>

<span data-ttu-id="80000-208">Do třídy *AnalyzeSentiment* vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="80000-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="80000-209">Tento kód přiřadí `PredictionEnginePool` předáním do konstruktoru funkce, který získáte prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="80000-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="80000-210">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="80000-210">Use the model to make predictions</span></span>

<span data-ttu-id="80000-211">Nahraďte stávající implementaci metody *Run* ve třídě *AnalyzeSentiment* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="80000-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="80000-212">Když se metoda `Run` spustí, příchozí data z požadavku HTTP se deserializovat a použijí se jako vstup pro `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="80000-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="80000-213">Metoda `Predict` je pak volána k provedení předpovědi pomocí `SentimentAnalysisModel` zaregistrovaného ve třídě `Startup` a vrátí výsledky zpět uživateli v případě úspěchu.</span><span class="sxs-lookup"><span data-stu-id="80000-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="80000-214">Test lokálně</span><span class="sxs-lookup"><span data-stu-id="80000-214">Test locally</span></span>

<span data-ttu-id="80000-215">Teď, když je všechno nastavené, je čas otestovat aplikaci:</span><span class="sxs-lookup"><span data-stu-id="80000-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="80000-216">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="80000-216">Run the application</span></span>
1. <span data-ttu-id="80000-217">Otevřete PowerShell a zadejte kód do příkazového řádku, kde PORT je port, na kterém je vaše aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="80000-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="80000-218">Obvykle je port 7071.</span><span class="sxs-lookup"><span data-stu-id="80000-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="80000-219">V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:</span><span class="sxs-lookup"><span data-stu-id="80000-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="80000-220">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="80000-220">Congratulations!</span></span> <span data-ttu-id="80000-221">Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí funkce Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="80000-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="80000-222">Další kroky</span><span class="sxs-lookup"><span data-stu-id="80000-222">Next Steps</span></span>

- [<span data-ttu-id="80000-223">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="80000-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
