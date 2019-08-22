---
title: Nasazení modelu do ASP.NET Core webového rozhraní API
description: Obsluha modelu strojového učení ML.NET mínění přes Internet pomocí ASP.NET Core webového rozhraní API
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: e1dcc719738a2beb3e63463245d4721c5298cf85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666664"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="43ec8-103">Nasazení modelu do ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="43ec8-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="43ec8-104">Naučte se, jak na webu sloužit předem trained ML.NET model strojového učení, pomocí ASP.NET Core webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="43ec8-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="43ec8-105">Obsluha modelu přes webové rozhraní API umožňuje předpovědi prostřednictvím standardních metod HTTP.</span><span class="sxs-lookup"><span data-stu-id="43ec8-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="43ec8-106">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="43ec8-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43ec8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43ec8-107">Prerequisites</span></span>

- <span data-ttu-id="43ec8-108">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="43ec8-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="43ec8-109">Prostředí.</span><span class="sxs-lookup"><span data-stu-id="43ec8-109">Powershell.</span></span>
- <span data-ttu-id="43ec8-110">Předem vyškolený model.</span><span class="sxs-lookup"><span data-stu-id="43ec8-110">Pre-trained model.</span></span> <span data-ttu-id="43ec8-111">Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) představitelnou mínění analýzou.</span><span class="sxs-lookup"><span data-stu-id="43ec8-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="43ec8-112">Vytvoření projektu webového rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43ec8-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="43ec8-113">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="43ec8-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="43ec8-114">Z řádku nabídek vyberte **soubor > nový > projekt** .</span><span class="sxs-lookup"><span data-stu-id="43ec8-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="43ec8-115">V dialogovém okně Nový projekt vyberte uzel **vizuálu C#**  následovaný webovým uzlem .</span><span class="sxs-lookup"><span data-stu-id="43ec8-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="43ec8-116">Pak vyberte šablonu projektu **ASP.NET Core webové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="43ec8-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="43ec8-117">Do textového pole **název** zadejte "SentimentAnalysisWebAPI" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="43ec8-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="43ec8-118">V okně, které zobrazuje různé typy ASP.NET Core projektů, vyberte **rozhraní API** a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="43ec8-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="43ec8-119">Vytvořte ve svém projektu adresář s názvem *MLModels* a uložte předem sestavené soubory modelu Machine Learning:</span><span class="sxs-lookup"><span data-stu-id="43ec8-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="43ec8-120">V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="43ec8-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="43ec8-121">Zadejte "MLModels" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="43ec8-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="43ec8-122">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="43ec8-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="43ec8-123">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="43ec8-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="43ec8-124">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="43ec8-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="43ec8-125">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="43ec8-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="43ec8-126">Nainstalujte **balíček Nuget Microsoft.Extensions.ml**:</span><span class="sxs-lookup"><span data-stu-id="43ec8-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="43ec8-127">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="43ec8-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="43ec8-128">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="43ec8-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="43ec8-129">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="43ec8-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="43ec8-130">Přidání modelu do ASP.NET Core projektu webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="43ec8-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="43ec8-131">Zkopírování předem připraveného modelu do adresáře *MLModels*</span><span class="sxs-lookup"><span data-stu-id="43ec8-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="43ec8-132">V Průzkumník řešení klikněte pravým tlačítkem na soubor zip modelu a vyberte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="43ec8-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="43ec8-133">V části Upřesnit změňte hodnotu kopírovat do výstupního adresáře na kopírovat, pokud je novější.</span><span class="sxs-lookup"><span data-stu-id="43ec8-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="43ec8-134">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="43ec8-134">Create data models</span></span>

<span data-ttu-id="43ec8-135">Musíte vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="43ec8-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="43ec8-136">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="43ec8-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="43ec8-137">Vytvořte v projektu adresář s názvem datamodels pro uložení datových modelů:</span><span class="sxs-lookup"><span data-stu-id="43ec8-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="43ec8-138">V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="43ec8-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="43ec8-139">Zadejte "datamodels" a stiskněte **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="43ec8-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="43ec8-140">V Průzkumník řešení klikněte pravým tlačítkem na adresář datamodels a pak vyberte Přidat > nová položka.</span><span class="sxs-lookup"><span data-stu-id="43ec8-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="43ec8-141">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="43ec8-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="43ec8-142">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="43ec8-142">Then, select the **Add** button.</span></span> <span data-ttu-id="43ec8-143">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="43ec8-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="43ec8-144">Do horní části *SentimentData.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="43ec8-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="43ec8-145">Odeberte existující definici třídy a přidejte následující kód do souboru **SentimentData.cs** :</span><span class="sxs-lookup"><span data-stu-id="43ec8-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="43ec8-146">V Průzkumník řešení klikněte pravým tlačítkem na adresář datamodels a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="43ec8-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="43ec8-147">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="43ec8-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="43ec8-148">Pak vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="43ec8-148">Then, select the Add button.</span></span> <span data-ttu-id="43ec8-149">V editoru kódu se otevře soubor *SentimentPrediction.cs* .</span><span class="sxs-lookup"><span data-stu-id="43ec8-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="43ec8-150">Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="43ec8-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="43ec8-151">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="43ec8-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="43ec8-152">`SentimentPrediction`dědí z `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="43ec8-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="43ec8-153">To usnadňuje zobrazení původních dat ve `SentimentText` vlastnosti spolu s výstupem generovaným modelem.</span><span class="sxs-lookup"><span data-stu-id="43ec8-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="43ec8-154">Registrovat PredictionEnginePool pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="43ec8-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="43ec8-155">K provedení jedné předpovědi použijte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="43ec8-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="43ec8-156">Aby bylo možné v [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) aplikaci používat, musíte ji vytvořit, až bude potřeba.</span><span class="sxs-lookup"><span data-stu-id="43ec8-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="43ec8-157">V takovém případě je osvědčeným postupem použití injektáže závislostí.</span><span class="sxs-lookup"><span data-stu-id="43ec8-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="43ec8-158">Následující odkaz poskytuje další informace, pokud se chcete dozvědět o [vkládání závislostí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="43ec8-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="43ec8-159">Otevřete třídu *Startup.cs* a na začátek souboru přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="43ec8-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="43ec8-160">Do metody *ConfigureServices* přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="43ec8-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="43ec8-161">Na vysoké úrovni tento kód automaticky inicializuje objekty a služby, pokud je aplikace požaduje, místo toho, aby ji ručně provedete.</span><span class="sxs-lookup"><span data-stu-id="43ec8-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="43ec8-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="43ec8-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="43ec8-163">Pro zlepšení výkonu a bezpečnosti vláken použijte `PredictionEnginePool` službu, která [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) vytvoří `PredictionEngine` objekty pro použití aplikací.</span><span class="sxs-lookup"><span data-stu-id="43ec8-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="43ec8-164">Další informace o [vytváření a používání `PredictionEngine` fondů objektů v ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)najdete v tomto blogovém příspěvku.</span><span class="sxs-lookup"><span data-stu-id="43ec8-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="43ec8-165">Vytvořit kontroler předpovědi</span><span class="sxs-lookup"><span data-stu-id="43ec8-165">Create Predict controller</span></span>

<span data-ttu-id="43ec8-166">Pokud chcete zpracovat příchozí požadavky HTTP, vytvořte kontroler.</span><span class="sxs-lookup"><span data-stu-id="43ec8-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="43ec8-167">V Průzkumník řešení klikněte pravým tlačítkem na adresář *řadiče* a pak vyberte **Přidat > kontroler**.</span><span class="sxs-lookup"><span data-stu-id="43ec8-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="43ec8-168">V dialogovém okně **Přidat novou položku** vyberte možnost **kontroler rozhraní API prázdné** a vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="43ec8-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="43ec8-169">V příkazovém řádku změňte pole **název kontroleru** na *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="43ec8-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="43ec8-170">Pak vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="43ec8-170">Then, select the Add button.</span></span> <span data-ttu-id="43ec8-171">V editoru kódu se otevře soubor *PredictController.cs* .</span><span class="sxs-lookup"><span data-stu-id="43ec8-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="43ec8-172">Do horní části *PredictController.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="43ec8-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="43ec8-173">Odeberte existující definici třídy a přidejte následující kód do souboru *PredictController.cs* :</span><span class="sxs-lookup"><span data-stu-id="43ec8-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="43ec8-174">Tento kód přiřadí `PredictionEnginePool` rozhraní předáním do konstruktoru kontroleru, který získáte prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="43ec8-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="43ec8-175">`Predict` Pak Metoda`Post` řadiče používá `PredictionEnginePool` k vytvoření předpovědi a vrátí výsledky zpátky uživateli, pokud je to úspěšné.</span><span class="sxs-lookup"><span data-stu-id="43ec8-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="43ec8-176">Místní testování webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="43ec8-176">Test web API locally</span></span>

<span data-ttu-id="43ec8-177">Jakmile je všechno nastavené, je čas otestovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="43ec8-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="43ec8-178">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="43ec8-178">Run the application.</span></span>
1. <span data-ttu-id="43ec8-179">Otevřete PowerShell a zadejte následující kód, kde PORT je port, na kterém naslouchá vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="43ec8-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="43ec8-180">V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:</span><span class="sxs-lookup"><span data-stu-id="43ec8-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="43ec8-181">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="43ec8-181">Congratulations!</span></span> <span data-ttu-id="43ec8-182">Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí webového rozhraní API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="43ec8-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="43ec8-183">Další kroky</span><span class="sxs-lookup"><span data-stu-id="43ec8-183">Next Steps</span></span>

- [<span data-ttu-id="43ec8-184">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="43ec8-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
