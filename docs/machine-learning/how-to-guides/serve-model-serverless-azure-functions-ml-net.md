---
title: Nasazení modelu do Azure Functions
description: Obsluhujte ML.NET modelu strojového učení analýzy mínění pro předpověď přes internet pomocí Azure Functions
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f340805200a14e0e145ffe1bf20f8059df63555
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608046"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="2af45-103">Nasazení modelu do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="2af45-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="2af45-104">Zjistěte, jak nasadit předem trénovaný model ML.NET strojového učení pro předpovědi přes HTTP prostřednictvím prostředí Bez serveru Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="2af45-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="2af45-105">Tato ukázka spustí verzi `PredictionEnginePool` náhledu služby.</span><span class="sxs-lookup"><span data-stu-id="2af45-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2af45-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2af45-106">Prerequisites</span></span>

- <span data-ttu-id="2af45-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanými úlohami "Vývoj napříč platformami.NET Core" a "Azure Development".</span><span class="sxs-lookup"><span data-stu-id="2af45-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" and "Azure development" workloads installed.</span></span>
- [<span data-ttu-id="2af45-108">Nástroje pro funkce Azure</span><span class="sxs-lookup"><span data-stu-id="2af45-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="2af45-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="2af45-109">Powershell</span></span>
- <span data-ttu-id="2af45-110">Předem vycvičený model.</span><span class="sxs-lookup"><span data-stu-id="2af45-110">Pre-trained model.</span></span> <span data-ttu-id="2af45-111">Použijte [kurz ML.NET analýzy mínění](../tutorials/sentiment-analysis.md) k vytvoření vlastního modelu nebo ke stažení tohoto [předem vytrénovaného modelu strojového učení analýzy mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="2af45-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="2af45-112">Přehled ukázkových funkcí Azure</span><span class="sxs-lookup"><span data-stu-id="2af45-112">Azure Functions sample overview</span></span>

<span data-ttu-id="2af45-113">Tato ukázka je **aplikace C# HTTP Trigger Azure Functions,** která používá předem trénovaný binární klasifikační model ke kategorizaci mínění textu jako kladné nebo negativní.</span><span class="sxs-lookup"><span data-stu-id="2af45-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="2af45-114">Funkce Azure poskytuje snadný způsob, jak spustit malé části kódu ve velkém měřítku ve spravovaném prostředí bez serveru v cloudu.</span><span class="sxs-lookup"><span data-stu-id="2af45-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="2af45-115">Kód pro tuto ukázku najdete v úložišti [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="2af45-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="2af45-116">Vytvoření projektu Azure Functions</span><span class="sxs-lookup"><span data-stu-id="2af45-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="2af45-117">Otevřete sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="2af45-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="2af45-118">Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.**</span><span class="sxs-lookup"><span data-stu-id="2af45-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="2af45-119">V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **Cloud.**</span><span class="sxs-lookup"><span data-stu-id="2af45-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="2af45-120">Pak vyberte šablonu projektu **Azure Functions.**</span><span class="sxs-lookup"><span data-stu-id="2af45-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="2af45-121">Do textového pole **Název** zadejte "SentimentAnalysisFunctionsApp" a vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="2af45-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="2af45-122">V dialogovém okně **Nový projekt** otevřete rozbalovací okno nad možnostmi projektu a vyberte Azure **Functions v2 (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="2af45-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="2af45-123">Potom vyberte spouštěcí projekt **Http** a pak vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="2af45-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="2af45-124">Vytvořte adresář s názvem *MLModels* v projektu pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="2af45-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="2af45-125">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="2af45-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="2af45-126">Zadejte "MLModels" a stiskněte enter.</span><span class="sxs-lookup"><span data-stu-id="2af45-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="2af45-127">Nainstalujte **Microsoft.ML balíček NuGet** verze **1.3.1**:</span><span class="sxs-lookup"><span data-stu-id="2af45-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="2af45-128">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2af45-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2af45-129">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2af45-130">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="2af45-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="2af45-131">Nainstalujte **balíček Microsoft.Azure.Functions.Extensions NuGet**:</span><span class="sxs-lookup"><span data-stu-id="2af45-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="2af45-132">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2af45-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2af45-133">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **microsoft.azure.functions.extensions**, vyberte tento balíček v seznamu a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2af45-134">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="2af45-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="2af45-135">Nainstalujte **Microsoft.Extensions.ML balíček NuGet** verze **0.15.1**:</span><span class="sxs-lookup"><span data-stu-id="2af45-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="2af45-136">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2af45-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2af45-137">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2af45-138">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="2af45-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="2af45-139">Nainstalujte **balíček Microsoft.NET.Sdk.Functions NuGet verze** **1.0.31**:</span><span class="sxs-lookup"><span data-stu-id="2af45-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="2af45-140">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2af45-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2af45-141">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Nainstalováno, vyhledejte **sadu Microsoft.NET.Sdk.Functions**, vyberte tento balíček v seznamu, vyberte **1.0.31** v rozevíracím seznamu Verze a vyberte tlačítko **Aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="2af45-142">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="2af45-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="2af45-143">Přidání předem trénovaného modelu k projektu</span><span class="sxs-lookup"><span data-stu-id="2af45-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="2af45-144">Zkopírujte předem sestavený model do složky *MLModels.*</span><span class="sxs-lookup"><span data-stu-id="2af45-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="2af45-145">V Průzkumníku řešení klepněte pravým tlačítkem myši na předem sestavený soubor modelu a vyberte **příkaz Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2af45-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="2af45-146">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="2af45-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="2af45-147">Vytvoření funkce Azure pro analýzu mínění</span><span class="sxs-lookup"><span data-stu-id="2af45-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="2af45-148">Vytvořte třídu pro předpověď mínění.</span><span class="sxs-lookup"><span data-stu-id="2af45-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="2af45-149">Přidání nové třídy do projektu:</span><span class="sxs-lookup"><span data-stu-id="2af45-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="2af45-150">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="2af45-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="2af45-151">V dialogovém okně **Přidat novou položku** vyberte **Funkci Azure** a změňte pole **Název** na *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="2af45-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="2af45-152">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="2af45-153">V dialogovém okně **Nová funkce Azure** vyberte Http **Trigger**.</span><span class="sxs-lookup"><span data-stu-id="2af45-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="2af45-154">Potom vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="2af45-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="2af45-155">V editoru kódu se otevře *soubor AnalyzeSentiment.cs.*</span><span class="sxs-lookup"><span data-stu-id="2af45-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="2af45-156">Na začátek `using` *AnalyzeSentiment.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="2af45-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="2af45-157">Ve výchozím `AnalyzeSentiment` nastavení `static`je třída .</span><span class="sxs-lookup"><span data-stu-id="2af45-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="2af45-158">Nezapomeňte odebrat `static` klíčové slovo z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="2af45-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="2af45-159">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="2af45-159">Create data models</span></span>

<span data-ttu-id="2af45-160">Je třeba vytvořit některé třídy pro vaše vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2af45-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="2af45-161">Přidání nové třídy do projektu:</span><span class="sxs-lookup"><span data-stu-id="2af45-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="2af45-162">Vytvořte adresář s názvem *DataModels* v projektu pro uložení datových modelů: V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > novou složku**.</span><span class="sxs-lookup"><span data-stu-id="2af45-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="2af45-163">Zadejte "DataModels" a stiskněte klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="2af45-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="2af45-164">V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *DataModels* a pak vyberte **příkaz Přidat > novou položku**.</span><span class="sxs-lookup"><span data-stu-id="2af45-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="2af45-165">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="2af45-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="2af45-166">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="2af45-167">Soubor *SentimentData.cs* se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="2af45-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="2af45-168">Přidejte následující příkaz using na začátek *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="2af45-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="2af45-169">Odeberte existující definici třídy a do *souboru SentimentData.cs* přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="2af45-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="2af45-170">V Průzkumníku řešení klepněte pravým tlačítkem myši na adresář *DataModels* a pak vyberte **příkaz Přidat > novou položku**.</span><span class="sxs-lookup"><span data-stu-id="2af45-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="2af45-171">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="2af45-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="2af45-172">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-172">Then, select the **Add** button.</span></span> <span data-ttu-id="2af45-173">Soubor *SentimentPrediction.cs* se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="2af45-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="2af45-174">Přidejte následující příkaz using na začátek *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="2af45-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="2af45-175">Odeberte existující definici třídy a přidejte do *SentimentPrediction.cs* souboru následující kód:</span><span class="sxs-lookup"><span data-stu-id="2af45-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="2af45-176">`SentimentPrediction`dědí, `SentimentData` z nichž poskytuje přístup `SentimentText` k původní data ve vlastnosti, stejně jako výstup generovaný modelem.</span><span class="sxs-lookup"><span data-stu-id="2af45-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="2af45-177">Zaregistrovat službu PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="2af45-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="2af45-178">Chcete-li provést jednu předpověď, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musíte vytvořit .</span><span class="sxs-lookup"><span data-stu-id="2af45-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="2af45-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2af45-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2af45-180">Navíc je nutné vytvořit instanci všude, kde je potřeba v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="2af45-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="2af45-181">Jak vaše aplikace roste, tento proces může být nezvladatelný.</span><span class="sxs-lookup"><span data-stu-id="2af45-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="2af45-182">Pro zvýšení výkonu a bezpečnosti podprocesů použijte `PredictionEnginePool` kombinaci vkládání [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) závislostí a služby, která vytvoří objekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2af45-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="2af45-183">Následující odkaz obsahuje další informace, pokud chcete získat další informace o [vkládání závislostí](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="2af45-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="2af45-184">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="2af45-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2af45-185">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="2af45-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="2af45-186">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="2af45-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2af45-187">Přidejte následující příkazy using na začátek *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="2af45-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="2af45-188">Odeberte existující kód pod příkazy using a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="2af45-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="2af45-189">Definujte proměnné pro uložení prostředí, ve kterém aplikace běží, a `Startup` cestu k souboru, kde je model umístěn uvnitř třídy</span><span class="sxs-lookup"><span data-stu-id="2af45-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="2af45-190">Pod tím vytvořte konstruktor pro nastavení `_environment` `_modelPath` hodnot a proměnných.</span><span class="sxs-lookup"><span data-stu-id="2af45-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="2af45-191">Pokud je aplikace spuštěna místně, výchozí prostředí je *Vývoj*.</span><span class="sxs-lookup"><span data-stu-id="2af45-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="2af45-192">Potom přidejte novou `Configure` metodu `PredictionEnginePool` volanou k registraci služby pod konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="2af45-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="2af45-193">Na vysoké úrovni tento kód inicializuje objekty a služby automaticky pro pozdější použití na požádání aplikace namísto nutnosti ručně provést.</span><span class="sxs-lookup"><span data-stu-id="2af45-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="2af45-194">Modely strojového učení nejsou statické.</span><span class="sxs-lookup"><span data-stu-id="2af45-194">Machine learning models are not static.</span></span> <span data-ttu-id="2af45-195">Jako nová trénovací data k dispozici, model je retrained a znovu nasadit.</span><span class="sxs-lookup"><span data-stu-id="2af45-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="2af45-196">Jedním ze způsobů, jak získat nejnovější verzi modelu do aplikace, je znovu nasadit celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2af45-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="2af45-197">To však zavádí prostoje aplikace.</span><span class="sxs-lookup"><span data-stu-id="2af45-197">However, this introduces application downtime.</span></span> <span data-ttu-id="2af45-198">Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti snížit počet aplikací.</span><span class="sxs-lookup"><span data-stu-id="2af45-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="2af45-199">Nastavte `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) spustí, který naslouchá systému souborů změnit oznámení a vyvolá události, když dojde ke změně souboru.</span><span class="sxs-lookup"><span data-stu-id="2af45-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="2af45-200">To vyzve `PredictionEnginePool` k automatickému opětovnému načtení modelu.</span><span class="sxs-lookup"><span data-stu-id="2af45-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="2af45-201">Model je identifikován `modelName` parametrem tak, aby více než jeden model na aplikaci lze znovu načíst při změně.</span><span class="sxs-lookup"><span data-stu-id="2af45-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="2af45-202">Alternativně můžete použít `FromUri` metodu při práci s modely uloženými vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="2af45-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="2af45-203">Místo sledování změn souborů `FromUri` se vyhodnoťuje změny ve vzdáleném umístění.</span><span class="sxs-lookup"><span data-stu-id="2af45-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="2af45-204">Interval dotazování je výchozí na 5 minut.</span><span class="sxs-lookup"><span data-stu-id="2af45-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="2af45-205">Můžete zvýšit nebo snížit interval dotazování na základě požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="2af45-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="2af45-206">V ukázce `PredictionEnginePool` kódu níže uskutečuje model uložený na zadaném identifikátoru URI každou minutu.</span><span class="sxs-lookup"><span data-stu-id="2af45-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="2af45-207">Načtení modelu do funkce</span><span class="sxs-lookup"><span data-stu-id="2af45-207">Load the model into the function</span></span>

<span data-ttu-id="2af45-208">Do třídy *AnalyzeSentiment* vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="2af45-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="2af45-209">Tento kód přiřadí `PredictionEnginePool` předáním konstruktoru funkce, který získáte prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="2af45-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="2af45-210">Použití modelu k předpovědi</span><span class="sxs-lookup"><span data-stu-id="2af45-210">Use the model to make predictions</span></span>

<span data-ttu-id="2af45-211">Nahraďte existující implementaci metody *Run* ve třídě *AnalyzeSentiment* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2af45-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="2af45-212">Při `Run` spuštění metody jsou příchozí data z požadavku HTTP deknokrenována a použita `PredictionEnginePool`jako vstup pro soubor .</span><span class="sxs-lookup"><span data-stu-id="2af45-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="2af45-213">Metoda `Predict` je pak volána k `SentimentAnalysisModel` předpovědi `Startup` pomocí registrované ve třídě a vrátí výsledky zpět uživateli v případě úspěchu.</span><span class="sxs-lookup"><span data-stu-id="2af45-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="2af45-214">Testování místně</span><span class="sxs-lookup"><span data-stu-id="2af45-214">Test locally</span></span>

<span data-ttu-id="2af45-215">Nyní, když je vše nastaveno, je čas otestovat aplikaci:</span><span class="sxs-lookup"><span data-stu-id="2af45-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="2af45-216">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="2af45-216">Run the application</span></span>
1. <span data-ttu-id="2af45-217">Otevřete PowerShell a zadejte kód do výzvy, kde PORT je port, na kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="2af45-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="2af45-218">Port je obvykle 7071.</span><span class="sxs-lookup"><span data-stu-id="2af45-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="2af45-219">V případě úspěchu by výstup měl vypadat podobně jako v níže uvedeném textu:</span><span class="sxs-lookup"><span data-stu-id="2af45-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="2af45-220">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="2af45-220">Congratulations!</span></span> <span data-ttu-id="2af45-221">Úspěšně obsluhoval model, aby předpovědi přes internet pomocí funkce Azure.</span><span class="sxs-lookup"><span data-stu-id="2af45-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2af45-222">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2af45-222">Next Steps</span></span>

- [<span data-ttu-id="2af45-223">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="2af45-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
