---
title: Nasazení modelu do Azure Functions
description: Poskytování ML.NET mínění analýzy modelu strojového učení pro predikci přes internet pomocí služby Azure Functions
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 7df7a6f9fcc5a4702171e1aac4b6b67e0c343748
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025976"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="dbf06-103">Nasazení modelu do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="dbf06-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="dbf06-104">Zjistěte, jak nasadit předem vytrénovaných ML.NET model strojového učení k předpovědi přes protokol HTTP pomocí prostředí Azure Functions bez serveru.</span><span class="sxs-lookup"><span data-stu-id="dbf06-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="dbf06-105">`PredictionEnginePool` rozšíření služby je aktuálně ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="dbf06-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbf06-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbf06-106">Prerequisites</span></span>

- <span data-ttu-id="dbf06-107">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) úlohy "Vývoj pro různé platformy .NET Core" a "Vývoj pro Azure" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="dbf06-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="dbf06-108">Microsoft.NET.Sdk.Functions 1.0.28+ verze balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="dbf06-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="dbf06-109">Nástroje Azure Functions</span><span class="sxs-lookup"><span data-stu-id="dbf06-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="dbf06-110">Powershell</span><span class="sxs-lookup"><span data-stu-id="dbf06-110">Powershell</span></span>
- <span data-ttu-id="dbf06-111">Předem natrénovaných modelů.</span><span class="sxs-lookup"><span data-stu-id="dbf06-111">Pre-trained model.</span></span> <span data-ttu-id="dbf06-112">Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestavovat vlastní model nebo stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="dbf06-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="dbf06-113">Vytvoření projektu Azure Functions</span><span class="sxs-lookup"><span data-stu-id="dbf06-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="dbf06-114">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="dbf06-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="dbf06-115">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="dbf06-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="dbf06-116">V **nový projekt** dialogového okna, vyberte **Visual C#**  uzel, za nímž následuje **cloudu** uzlu.</span><span class="sxs-lookup"><span data-stu-id="dbf06-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="dbf06-117">Vyberte **Azure Functions** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="dbf06-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="dbf06-118">V **název** textového pole zadejte "SentimentAnalysisFunctionsApp" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="dbf06-119">V **nový projekt** dialogového okna, otevřete rozevírací seznam nahoře možnosti projektu a vyberte **Azure Functions v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="dbf06-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="dbf06-120">Vyberte **triggeru Http** projektu a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="dbf06-121">Vytvořte adresář *MLModels* ve vašem projektu a uložit model:</span><span class="sxs-lookup"><span data-stu-id="dbf06-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="dbf06-122">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="dbf06-123">Zadejte "MLModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="dbf06-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="dbf06-124">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="dbf06-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="dbf06-125">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dbf06-126">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="dbf06-127">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="dbf06-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="dbf06-128">Nainstalujte **balíček NuGet Microsoft.Azure.Functions.Extensions**:</span><span class="sxs-lookup"><span data-stu-id="dbf06-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="dbf06-129">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dbf06-130">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.Azure.Functions.Extensions**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="dbf06-131">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="dbf06-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="dbf06-132">Nainstalujte **balíček NuGet Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="dbf06-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="dbf06-133">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dbf06-134">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="dbf06-135">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="dbf06-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="dbf06-136">Aktualizace **balíček NuGet Microsoft.NET.Sdk.Functions** verzi 1.0.28:</span><span class="sxs-lookup"><span data-stu-id="dbf06-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28:</span></span>

    <span data-ttu-id="dbf06-137">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dbf06-138">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu nainstalováno, vyhledejte **Microsoft.NET.Sdk.Functions**, vyberte v seznamu vyberte 1.0.28 nebo později z rozevíracího seznamu verze tento balíček a vyberte **aktualizace**  tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="dbf06-139">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="dbf06-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="dbf06-140">Přidání předem vytrénovaných modelu do projektu</span><span class="sxs-lookup"><span data-stu-id="dbf06-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="dbf06-141">Zkopírujte předem sestavených model *MLModels* složky.</span><span class="sxs-lookup"><span data-stu-id="dbf06-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="dbf06-142">V Průzkumníku řešení klikněte pravým tlačítkem na soubor předem sestavených modelů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="dbf06-143">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="dbf06-144">Vytvoření funkce Azure analyzovat mínění</span><span class="sxs-lookup"><span data-stu-id="dbf06-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="dbf06-145">Vytvoření třídy k předpovědi mínění.</span><span class="sxs-lookup"><span data-stu-id="dbf06-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="dbf06-146">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="dbf06-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="dbf06-147">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="dbf06-148">V **přidat novou položku** dialogu **funkce Azure Functions** a změnit **název** pole *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="dbf06-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="dbf06-149">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="dbf06-150">V **novou funkci Azure Functions** dialogu **triggeru Http**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="dbf06-151">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="dbf06-152">*AnalyzeSentiment.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dbf06-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="dbf06-153">Přidejte následující `using` příkaz do horní části *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="dbf06-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

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

    <span data-ttu-id="dbf06-154">Ve výchozím nastavení `AnalyzeSentiment` třída je `static`.</span><span class="sxs-lookup"><span data-stu-id="dbf06-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="dbf06-155">Ujistěte se, že chcete odebrat `static` – klíčové slovo z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="dbf06-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="dbf06-156">Vytvoření datových modelů</span><span class="sxs-lookup"><span data-stu-id="dbf06-156">Create data models</span></span>

<span data-ttu-id="dbf06-157">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="dbf06-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="dbf06-158">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="dbf06-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="dbf06-159">Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů: V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="dbf06-160">Zadejte "DataModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="dbf06-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="dbf06-161">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="dbf06-162">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="dbf06-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="dbf06-163">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="dbf06-164">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dbf06-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="dbf06-165">Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="dbf06-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="dbf06-166">Odeberte stávající definice třídy a přidejte následující kód, který *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="dbf06-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
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

4. <span data-ttu-id="dbf06-167">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="dbf06-168">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="dbf06-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="dbf06-169">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-169">Then, select the **Add** button.</span></span> <span data-ttu-id="dbf06-170">*SentimentPrediction.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dbf06-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="dbf06-171">Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="dbf06-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="dbf06-172">Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="dbf06-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="dbf06-173">`SentimentPrediction` dědí z `SentimentData` poskytující přístup k původní data v `SentimentText` vlastnosti a také výstup generovaný model.</span><span class="sxs-lookup"><span data-stu-id="dbf06-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="dbf06-174">Zaregistrovat službu PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="dbf06-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="dbf06-175">Chcete-li jeden predikcí, použijte [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="dbf06-175">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="dbf06-176">Chcete-li použít [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) ve vaší aplikaci je třeba jej vytvořit když ho nepotřebují.</span><span class="sxs-lookup"><span data-stu-id="dbf06-176">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="dbf06-177">V takovém případě je vhodné zvážit je vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="dbf06-177">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="dbf06-178">Pod následujícím odkazem najdete další informace, pokud chcete další informace o [injektáž závislostí](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="dbf06-178">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="dbf06-179">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="dbf06-179">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="dbf06-180">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="dbf06-180">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="dbf06-181">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dbf06-181">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="dbf06-182">*Startup.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dbf06-182">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="dbf06-183">Přidejte následující příkaz k hornímu okraji *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="dbf06-183">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="dbf06-184">Odeberte existující kód podle následujících příkazů a přidejte následující kód, který *Startup.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="dbf06-184">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

<span data-ttu-id="dbf06-185">Na vysoké úrovni tento kód inicializuje objekty a služby automaticky, pokud je požadovaná aplikací místo nutnosti ručně provést.</span><span class="sxs-lookup"><span data-stu-id="dbf06-185">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="dbf06-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečné pro vlákna.</span><span class="sxs-lookup"><span data-stu-id="dbf06-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="dbf06-187">Pro lepší výkon a bezpečný přístup z více vláken, použijte `PredictionEnginePool` službu, která vytvoří [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` objekty při použití aplikace.</span><span class="sxs-lookup"><span data-stu-id="dbf06-187">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="dbf06-188">Načíst model do funkce</span><span class="sxs-lookup"><span data-stu-id="dbf06-188">Load the model into the function</span></span>

<span data-ttu-id="dbf06-189">Vložte následující kód *AnalyzeSentiment* třídy:</span><span class="sxs-lookup"><span data-stu-id="dbf06-189">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="dbf06-190">Tento kód přiřadí `PredictionEnginePool` předáním funkce konstruktoru, který můžete získat pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="dbf06-190">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="dbf06-191">Použít model k predikci</span><span class="sxs-lookup"><span data-stu-id="dbf06-191">Use the model to make predictions</span></span>

<span data-ttu-id="dbf06-192">Nahraďte stávající implementaci *spustit* metoda *AnalyzeSentiment* třídy následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="dbf06-192">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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

<span data-ttu-id="dbf06-193">Když `Run` metody, je deserializovat a použít jako vstup pro příchozí data z požadavku HTTP `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="dbf06-193">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="dbf06-194">`Predict` Metoda je volána poté generovat predikcí a vrátí výsledek pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="dbf06-194">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="dbf06-195">Místní test</span><span class="sxs-lookup"><span data-stu-id="dbf06-195">Test locally</span></span>

<span data-ttu-id="dbf06-196">Teď, když je všechno nastavené, je čas k otestování aplikace:</span><span class="sxs-lookup"><span data-stu-id="dbf06-196">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="dbf06-197">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="dbf06-197">Run the application</span></span>
1. <span data-ttu-id="dbf06-198">Otevřete PowerShell a zobrazený kód zadejte do řádku, kde je port vaše aplikace běží na.</span><span class="sxs-lookup"><span data-stu-id="dbf06-198">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="dbf06-199">Port, který je obvykle 7071.</span><span class="sxs-lookup"><span data-stu-id="dbf06-199">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="dbf06-200">V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="dbf06-200">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="dbf06-201">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="dbf06-201">Congratulations!</span></span> <span data-ttu-id="dbf06-202">Jste úspěšně obsluhovat model k predikci přes internet pomocí funkce Azure functions.</span><span class="sxs-lookup"><span data-stu-id="dbf06-202">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dbf06-203">Další kroky</span><span class="sxs-lookup"><span data-stu-id="dbf06-203">Next Steps</span></span>

- [<span data-ttu-id="dbf06-204">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="dbf06-204">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
