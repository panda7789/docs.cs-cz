---
title: Nasazení modelu do služby Azure Functions
description: Poskytování ML.NET mínění analýzy modelu strojového učení pro predikci přes internet pomocí služby Azure Functions
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: c30c1c2e6f00020d22fe32fb3f53cefe88d8bb09
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063504"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="62332-103">Nasazení modelu do služby Azure Functions</span><span class="sxs-lookup"><span data-stu-id="62332-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="62332-104">Zjistěte, jak nasadit předem vytrénovaných ML.NET model strojového učení k předpovědi přes protokol HTTP pomocí prostředí Azure Functions bez serveru.</span><span class="sxs-lookup"><span data-stu-id="62332-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="62332-105">`PredictionEnginePool` rozšíření služby je aktuálně ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="62332-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="62332-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62332-106">Prerequisites</span></span>

- <span data-ttu-id="62332-107">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) úlohy "Vývoj pro různé platformy .NET Core" a "Vývoj pro Azure" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="62332-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="62332-108">Nástroje Azure Functions</span><span class="sxs-lookup"><span data-stu-id="62332-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="62332-109">Powershell</span><span class="sxs-lookup"><span data-stu-id="62332-109">Powershell</span></span>
- <span data-ttu-id="62332-110">Předem natrénovaných modelů.</span><span class="sxs-lookup"><span data-stu-id="62332-110">Pre-trained model.</span></span> <span data-ttu-id="62332-111">Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestavovat vlastní model nebo stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="62332-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="62332-112">Vytvoření projektu Azure Functions</span><span class="sxs-lookup"><span data-stu-id="62332-112">Create Azure Functions project</span></span>

1. <span data-ttu-id="62332-113">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="62332-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="62332-114">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="62332-114">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="62332-115">V **nový projekt** dialogového okna, vyberte **Visual C#**  uzel, za nímž následuje **cloudu** uzlu.</span><span class="sxs-lookup"><span data-stu-id="62332-115">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="62332-116">Vyberte **Azure Functions** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="62332-116">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="62332-117">V **název** textového pole zadejte "SentimentAnalysisFunctionsApp" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-117">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="62332-118">V **nový projekt** dialogového okna, otevřete rozevírací seznam nahoře možnosti projektu a vyberte **Azure Functions v2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="62332-118">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="62332-119">Vyberte **triggeru Http** projektu a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-119">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="62332-120">Vytvořte adresář *MLModels* ve vašem projektu a uložit model:</span><span class="sxs-lookup"><span data-stu-id="62332-120">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="62332-121">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="62332-121">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="62332-122">Zadejte "MLModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="62332-122">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="62332-123">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="62332-123">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="62332-124">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="62332-124">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="62332-125">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-125">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="62332-126">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="62332-126">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="62332-127">Nainstalujte **balíček NuGet Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="62332-127">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="62332-128">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="62332-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="62332-129">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="62332-130">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="62332-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="62332-131">Přidání předem vytrénovaných modelu do projektu</span><span class="sxs-lookup"><span data-stu-id="62332-131">Add pre-trained model to project</span></span>

1. <span data-ttu-id="62332-132">Zkopírujte předem sestavených model *MLModels* složky.</span><span class="sxs-lookup"><span data-stu-id="62332-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="62332-133">V Průzkumníku řešení klikněte pravým tlačítkem na soubor předem sestavených modelů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="62332-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="62332-134">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="62332-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="62332-135">Vytvoření funkce Azure analyzovat mínění</span><span class="sxs-lookup"><span data-stu-id="62332-135">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="62332-136">Vytvoření třídy k předpovědi mínění.</span><span class="sxs-lookup"><span data-stu-id="62332-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="62332-137">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="62332-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="62332-138">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="62332-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="62332-139">V **přidat novou položku** dialogu **funkce Azure Functions** a změnit **název** pole *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="62332-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="62332-140">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="62332-141">V **novou funkci Azure Functions** dialogu **triggeru Http**.</span><span class="sxs-lookup"><span data-stu-id="62332-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="62332-142">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="62332-143">*AnalyzeSentiment.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="62332-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="62332-144">Přidejte následující `using` příkaz do horní části *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="62332-144">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

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

    <span data-ttu-id="62332-145">Ve výchozím nastavení `AnalyzeSentiment` třída je `static`.</span><span class="sxs-lookup"><span data-stu-id="62332-145">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="62332-146">Ujistěte se, že chcete odebrat `static` – klíčové slovo z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="62332-146">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="62332-147">Vytvoření datových modelů</span><span class="sxs-lookup"><span data-stu-id="62332-147">Create data models</span></span>

<span data-ttu-id="62332-148">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="62332-148">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="62332-149">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="62332-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="62332-150">Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů: V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="62332-150">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="62332-151">Zadejte "DataModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="62332-151">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="62332-152">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="62332-152">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="62332-153">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="62332-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="62332-154">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-154">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="62332-155">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="62332-155">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="62332-156">Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="62332-156">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="62332-157">Odeberte stávající definice třídy a přidejte následující kód, který *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="62332-157">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
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

4. <span data-ttu-id="62332-158">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="62332-158">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="62332-159">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="62332-159">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="62332-160">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-160">Then, select the **Add** button.</span></span> <span data-ttu-id="62332-161">*SentimentPrediction.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="62332-161">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="62332-162">Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="62332-162">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="62332-163">Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="62332-163">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="62332-164">`SentimentPrediction` dědí z `SentimentData` poskytující přístup k původní data v `SentimentText` vlastnosti a také výstup generovaný model.</span><span class="sxs-lookup"><span data-stu-id="62332-164">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="62332-165">Zaregistrovat službu PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="62332-165">Register PredictionEnginePool service</span></span>

<span data-ttu-id="62332-166">Chcete-li jeden predikcí, použijte [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="62332-166">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="62332-167">Chcete-li použít [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) ve vaší aplikaci je třeba jej vytvořit když ho nepotřebují.</span><span class="sxs-lookup"><span data-stu-id="62332-167">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="62332-168">V takovém případě je vhodné zvážit je vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="62332-168">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="62332-169">Pod následujícím odkazem najdete další informace, pokud chcete další informace o [injektáž závislostí](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="62332-169">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="62332-170">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="62332-170">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="62332-171">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="62332-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="62332-172">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-172">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="62332-173">*Startup.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="62332-173">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="62332-174">Přidejte následující příkaz k hornímu okraji *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="62332-174">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="62332-175">Odeberte existující kód podle následujících příkazů a přidejte následující kód, který *Startup.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="62332-175">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

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

<span data-ttu-id="62332-176">Na vysoké úrovni tento kód inicializuje objekty a služby automaticky, pokud je požadovaná aplikací místo nutnosti ručně provést.</span><span class="sxs-lookup"><span data-stu-id="62332-176">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="62332-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečné pro vlákna.</span><span class="sxs-lookup"><span data-stu-id="62332-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="62332-178">Pro lepší výkon a bezpečný přístup z více vláken, použijte `PredictionEnginePool` službu, která vytvoří [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` objekty při použití aplikace.</span><span class="sxs-lookup"><span data-stu-id="62332-178">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="register-startup-as-an-azure-functions-extension"></a><span data-ttu-id="62332-179">Zaregistrujte se při spuštění jako rozšíření Azure Functions</span><span class="sxs-lookup"><span data-stu-id="62332-179">Register Startup as an Azure Functions extension</span></span>

<span data-ttu-id="62332-180">Chcete-li použít `Startup` ve vaší aplikaci, budete muset zaregistrovat jako rozšíření Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="62332-180">In order to use `Startup` in your application, you need to register it as an Azure Functions extension.</span></span> <span data-ttu-id="62332-181">Vytvořte nový soubor s názvem *extensions.json* ve vašem projektu, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="62332-181">Create a new file called *extensions.json* in your project if one does not already exist.</span></span>

1. <span data-ttu-id="62332-182">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="62332-182">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="62332-183">V **nová položka** dialogového okna, vyberte **Visual C#**  uzel, za nímž následuje **webové** uzlu.</span><span class="sxs-lookup"><span data-stu-id="62332-183">In the **New Item** dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="62332-184">Vyberte **soubor Json** možnost.</span><span class="sxs-lookup"><span data-stu-id="62332-184">Then select the **Json File** option.</span></span> <span data-ttu-id="62332-185">V **název** textového pole zadejte "extensions.json" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="62332-185">In the **Name** text box, type "extensions.json" and then select the **OK** button.</span></span>

    <span data-ttu-id="62332-186">*Extensions.json* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="62332-186">The *extensions.json* file opens in the code editor.</span></span> <span data-ttu-id="62332-187">Přidejte následující obsah, který se *extensions.json*:</span><span class="sxs-lookup"><span data-stu-id="62332-187">Add the following content to *extensions.json*:</span></span>
    
    ```json
    {
      "extensions": [
        {
          "name": "Startup",
          "typename": "SentimentAnalysisFunctionsApp.Startup, SentimentAnalysisFunctionsApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"
        }
      ]
    }
    ```

1. <span data-ttu-id="62332-188">V Průzkumníku řešení klikněte pravým tlačítkem na váš *extensions.json* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="62332-188">In Solution Explorer, right-click your *extensions.json* file and select **Properties**.</span></span> <span data-ttu-id="62332-189">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="62332-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="62332-190">Načíst model do funkce</span><span class="sxs-lookup"><span data-stu-id="62332-190">Load the model into the function</span></span>

<span data-ttu-id="62332-191">Vložte následující kód *AnalyzeSentiment* třídy:</span><span class="sxs-lookup"><span data-stu-id="62332-191">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="62332-192">Tento kód přiřadí `PredictionEnginePool` předáním funkce konstruktoru, který můžete získat pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="62332-192">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="62332-193">Použít model k predikci</span><span class="sxs-lookup"><span data-stu-id="62332-193">Use the model to make predictions</span></span>

<span data-ttu-id="62332-194">Nahraďte stávající implementaci *spustit* metoda *AnalyzeSentiment* třídy následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="62332-194">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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

<span data-ttu-id="62332-195">Když `Run` metody, je deserializovat a použít jako vstup pro příchozí data z požadavku HTTP `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="62332-195">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="62332-196">`Predict` Metoda je volána poté generovat predikcí a vrátí výsledek pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="62332-196">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="62332-197">Místní test</span><span class="sxs-lookup"><span data-stu-id="62332-197">Test locally</span></span>

<span data-ttu-id="62332-198">Teď, když je všechno nastavené, je čas k otestování aplikace:</span><span class="sxs-lookup"><span data-stu-id="62332-198">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="62332-199">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="62332-199">Run the application</span></span>
1. <span data-ttu-id="62332-200">Otevřete PowerShell a zobrazený kód zadejte do řádku, kde je port vaše aplikace běží na.</span><span class="sxs-lookup"><span data-stu-id="62332-200">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="62332-201">Port, který je obvykle 7071.</span><span class="sxs-lookup"><span data-stu-id="62332-201">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="62332-202">V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="62332-202">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="62332-203">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="62332-203">Congratulations!</span></span> <span data-ttu-id="62332-204">Jste úspěšně obsluhovat model k predikci přes internet pomocí funkce Azure functions.</span><span class="sxs-lookup"><span data-stu-id="62332-204">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="62332-205">Další kroky</span><span class="sxs-lookup"><span data-stu-id="62332-205">Next Steps</span></span>

- [<span data-ttu-id="62332-206">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="62332-206">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)