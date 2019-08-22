---
title: Nasazení modelu do Azure Functions
description: Obsluha modelu ML.NET mínění Analysis Machine Learning pro předpověď přes Internet pomocí Azure Functions
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 96b62017994da5b7b209c441b3e7fb760cad5201
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666672"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="14a5f-103">Nasazení modelu do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="14a5f-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="14a5f-104">Naučte se, jak nasadit předem vyškolený model ML.NET Machine Learning pro předpovědi přes protokol HTTP prostřednictvím prostředí bez serveru Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="14a5f-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="14a5f-105">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="14a5f-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14a5f-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14a5f-106">Prerequisites</span></span>

- <span data-ttu-id="14a5f-107">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "vývoj pro různé platformy pro .NET Core" a "vývoj pro Azure".</span><span class="sxs-lookup"><span data-stu-id="14a5f-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="14a5f-108">Microsoft. NET. SDK. Functions Package NuGet verze 1.0.28 +.</span><span class="sxs-lookup"><span data-stu-id="14a5f-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="14a5f-109">Nástroje Azure Functions</span><span class="sxs-lookup"><span data-stu-id="14a5f-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="14a5f-110">Prostředí</span><span class="sxs-lookup"><span data-stu-id="14a5f-110">Powershell</span></span>
- <span data-ttu-id="14a5f-111">Předem vyškolený model.</span><span class="sxs-lookup"><span data-stu-id="14a5f-111">Pre-trained model.</span></span> <span data-ttu-id="14a5f-112">Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) představitelnou mínění analýzou.</span><span class="sxs-lookup"><span data-stu-id="14a5f-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="14a5f-113">Vytvořit Azure Functions projekt</span><span class="sxs-lookup"><span data-stu-id="14a5f-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="14a5f-114">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="14a5f-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="14a5f-115">Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="14a5f-116">V dialogovém okně **Nový projekt** vyberte uzel **vizuálu C#**  následovaný uzlem cloudu .</span><span class="sxs-lookup"><span data-stu-id="14a5f-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="14a5f-117">Pak vyberte šablonu projektu **Azure Functions** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="14a5f-118">Do textového pole **název** zadejte "SentimentAnalysisFunctionsApp" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="14a5f-119">V dialogovém okně **Nový projekt** otevřete rozevírací seznam nad možnostmi projektu a vyberte **Azure Functions v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="14a5f-120">Pak vyberte projekt **triggeru http** a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="14a5f-121">Vytvořte v projektu adresář s názvem *MLModels* a uložte svůj model:</span><span class="sxs-lookup"><span data-stu-id="14a5f-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="14a5f-122">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="14a5f-123">Zadejte "MLModels" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="14a5f-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="14a5f-124">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="14a5f-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="14a5f-125">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="14a5f-126">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="14a5f-127">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="14a5f-128">Nainstalujte **balíček NuGet Microsoft. Azure. Functions. Extensions**:</span><span class="sxs-lookup"><span data-stu-id="14a5f-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="14a5f-129">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="14a5f-130">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft. Azure. Functions. Extensions**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="14a5f-131">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="14a5f-132">Nainstalujte **balíček NuGet Microsoft.Extensions.ml**:</span><span class="sxs-lookup"><span data-stu-id="14a5f-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="14a5f-133">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="14a5f-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="14a5f-135">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="14a5f-136">Aktualizujte **balíček NuGet Microsoft. NET. SDK. Functions** na verzi 1.0.28 +:</span><span class="sxs-lookup"><span data-stu-id="14a5f-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28+:</span></span>

    <span data-ttu-id="14a5f-137">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="14a5f-138">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu nainstalované, vyhledejte **Microsoft. NET. SDK. Functions**, vyberte tento balíček v seznamu, vyberte v rozevírací nabídce verze možnost 1.0.28 nebo novější a klikněte na tlačítko **aktualizovat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="14a5f-139">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="14a5f-140">Přidat předem vyškolený model do projektu</span><span class="sxs-lookup"><span data-stu-id="14a5f-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="14a5f-141">Do složky *MLModels* zkopírujte předem sestavený model.</span><span class="sxs-lookup"><span data-stu-id="14a5f-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="14a5f-142">V Průzkumník řešení klikněte pravým tlačítkem na předem sestavený soubor modelu a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="14a5f-143">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="14a5f-144">Vytvoření funkce Azure pro analýzu mínění</span><span class="sxs-lookup"><span data-stu-id="14a5f-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="14a5f-145">Vytvořte třídu pro předpověď mínění.</span><span class="sxs-lookup"><span data-stu-id="14a5f-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="14a5f-146">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="14a5f-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="14a5f-147">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="14a5f-148">V dialogovém okně **Přidat novou položku** vyberte možnost **Azure Functions** a změňte pole **název** na *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="14a5f-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="14a5f-149">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="14a5f-150">V dialogovém okně **Nová funkce Azure** vyberte **Trigger http**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="14a5f-151">Pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="14a5f-152">V editoru kódu se otevře soubor *AnalyzeSentiment.cs* .</span><span class="sxs-lookup"><span data-stu-id="14a5f-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="14a5f-153">Do horní části `using` *AnalyzeSentiment.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="14a5f-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using Microsoft.AspNetCore.Http;
    using Microsoft.Extensions.Logging;
    using Newtonsoft.Json;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="14a5f-154">Ve výchozím nastavení `AnalyzeSentiment` je `static`třída.</span><span class="sxs-lookup"><span data-stu-id="14a5f-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="14a5f-155">Nezapomeňte odebrat `static` klíčové slovo z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="14a5f-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="14a5f-156">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="14a5f-156">Create data models</span></span>

<span data-ttu-id="14a5f-157">Musíte vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="14a5f-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="14a5f-158">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="14a5f-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="14a5f-159">Vytvořte v projektu adresář s názvem datamodels pro uložení datových modelů: V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **přidat > nová složka**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="14a5f-160">Zadejte "datamodels" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="14a5f-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="14a5f-161">V Průzkumník řešení klikněte pravým tlačítkem na adresář datamodels a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="14a5f-162">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="14a5f-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="14a5f-163">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="14a5f-164">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="14a5f-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="14a5f-165">Do horní části *SentimentData.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="14a5f-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="14a5f-166">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="14a5f-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="14a5f-167">V Průzkumník řešení klikněte pravým tlačítkem na adresář datamodels a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="14a5f-168">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="14a5f-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="14a5f-169">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-169">Then, select the **Add** button.</span></span> <span data-ttu-id="14a5f-170">V editoru kódu se otevře soubor *SentimentPrediction.cs* .</span><span class="sxs-lookup"><span data-stu-id="14a5f-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="14a5f-171">Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="14a5f-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="14a5f-172">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="14a5f-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="14a5f-173">`SentimentPrediction`dědí z `SentimentData` , který poskytuje přístup k původním datům `SentimentText` ve vlastnosti a také výstup vygenerovaného modelem.</span><span class="sxs-lookup"><span data-stu-id="14a5f-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="14a5f-174">Zaregistrovat službu PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="14a5f-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="14a5f-175">K provedení jedné předpovědi použijte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="14a5f-175">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="14a5f-176">Aby bylo možné v [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) aplikaci používat, musíte ji vytvořit, až bude potřeba.</span><span class="sxs-lookup"><span data-stu-id="14a5f-176">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="14a5f-177">V takovém případě je osvědčeným postupem použití injektáže závislostí.</span><span class="sxs-lookup"><span data-stu-id="14a5f-177">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="14a5f-178">Následující odkaz poskytuje další informace, pokud chcete získat informace o [vkládání závislostí](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="14a5f-178">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="14a5f-179">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-179">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="14a5f-180">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="14a5f-180">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="14a5f-181">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-181">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="14a5f-182">V editoru kódu se otevře soubor *Startup.cs* .</span><span class="sxs-lookup"><span data-stu-id="14a5f-182">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="14a5f-183">Do horní části *Startup.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="14a5f-183">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="14a5f-184">Odeberte existující kód pod příkazy using a přidejte následující kód do souboru *Startup.cs* :</span><span class="sxs-lookup"><span data-stu-id="14a5f-184">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

<span data-ttu-id="14a5f-185">Na vysoké úrovni tento kód automaticky inicializuje objekty a služby, pokud je aplikace požaduje, místo toho, aby ji ručně provedete.</span><span class="sxs-lookup"><span data-stu-id="14a5f-185">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="14a5f-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="14a5f-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="14a5f-187">Pro zlepšení výkonu a bezpečnosti vláken použijte `PredictionEnginePool` službu, která [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) vytvoří `PredictionEngine` objekty pro použití aplikací.</span><span class="sxs-lookup"><span data-stu-id="14a5f-187">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="14a5f-188">Načtení modelu do funkce</span><span class="sxs-lookup"><span data-stu-id="14a5f-188">Load the model into the function</span></span>

<span data-ttu-id="14a5f-189">Do třídy *AnalyzeSentiment* vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="14a5f-189">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="14a5f-190">Tento kód přiřadí `PredictionEnginePool` rozhraní předáním do konstruktoru funkce, který obdržíte prostřednictvím injektáže závislosti.</span><span class="sxs-lookup"><span data-stu-id="14a5f-190">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="14a5f-191">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="14a5f-191">Use the model to make predictions</span></span>

<span data-ttu-id="14a5f-192">Nahraďte stávající implementaci metody *Run* ve třídě *AnalyzeSentiment* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="14a5f-192">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="14a5f-193">Když se `Run` Metoda spustí, příchozí data z požadavku HTTP se deserializovat a použijí se jako vstup `PredictionEnginePool`pro.</span><span class="sxs-lookup"><span data-stu-id="14a5f-193">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="14a5f-194">`Predict` Metoda je pak volána, aby vygenerovala předpověď a vrátila výsledek uživateli.</span><span class="sxs-lookup"><span data-stu-id="14a5f-194">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="14a5f-195">Test lokálně</span><span class="sxs-lookup"><span data-stu-id="14a5f-195">Test locally</span></span>

<span data-ttu-id="14a5f-196">Teď, když je všechno nastavené, je čas otestovat aplikaci:</span><span class="sxs-lookup"><span data-stu-id="14a5f-196">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="14a5f-197">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="14a5f-197">Run the application</span></span>
1. <span data-ttu-id="14a5f-198">Otevřete PowerShell a zadejte kód do příkazového řádku, kde PORT je port, na kterém je vaše aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="14a5f-198">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="14a5f-199">Obvykle je port 7071.</span><span class="sxs-lookup"><span data-stu-id="14a5f-199">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="14a5f-200">V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:</span><span class="sxs-lookup"><span data-stu-id="14a5f-200">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="14a5f-201">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="14a5f-201">Congratulations!</span></span> <span data-ttu-id="14a5f-202">Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí funkce Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="14a5f-202">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="14a5f-203">Další kroky</span><span class="sxs-lookup"><span data-stu-id="14a5f-203">Next Steps</span></span>

- [<span data-ttu-id="14a5f-204">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="14a5f-204">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
