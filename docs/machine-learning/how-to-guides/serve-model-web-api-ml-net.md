---
title: Nasazení modelu v ASP.NET Core Web API
description: Poskytování modelu strojového učení ML.NET mínění analýzy prostřednictvím Internetu pomocí webového rozhraní API ASP.NET Core
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c78e58dbec6b2ba3065fc46c4d4fd65abdcd37cd
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063483"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="36e0d-103">Nasazení modelu v ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="36e0d-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="36e0d-104">Zjistěte, jak poskytovat předem vytrénovaných ML.NET model strojového učení na web pomocí ASP.NET Core Web API.</span><span class="sxs-lookup"><span data-stu-id="36e0d-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="36e0d-105">Obsluhuje modelu přes webové rozhraní API umožňuje predikcí přes standardní HTTP metody.</span><span class="sxs-lookup"><span data-stu-id="36e0d-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="36e0d-106">`PredictionEnginePool` rozšíření služby je aktuálně ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="36e0d-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36e0d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36e0d-107">Prerequisites</span></span>

- <span data-ttu-id="36e0d-108">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="36e0d-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="36e0d-109">Prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36e0d-109">Powershell.</span></span>
- <span data-ttu-id="36e0d-110">Předem natrénovaných modelů.</span><span class="sxs-lookup"><span data-stu-id="36e0d-110">Pre-trained model.</span></span> <span data-ttu-id="36e0d-111">Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestavovat vlastní model nebo stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="36e0d-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="36e0d-112">Vytvořte projekt webového rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36e0d-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="36e0d-113">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="36e0d-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="36e0d-114">Vyberte **soubor > Nový > projekt** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="36e0d-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="36e0d-115">V dialogovém okně Nový projekt, vyberte **Visual C#**  uzel, za nímž následuje **webové** uzlu.</span><span class="sxs-lookup"><span data-stu-id="36e0d-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="36e0d-116">Vyberte **webové aplikace ASP.NET Core** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="36e0d-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="36e0d-117">V **název** textového pole zadejte "SentimentAnalysisWebAPI" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="36e0d-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="36e0d-118">V okně, které zobrazuje různé typy projektů ASP.NET Core, vyberte **API** a vyberte položku **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="36e0d-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="36e0d-119">Vytvořte adresář *MLModels* ve vašem projektu a uložit předem sestavených strojového učení soubory modelu:</span><span class="sxs-lookup"><span data-stu-id="36e0d-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="36e0d-120">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="36e0d-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="36e0d-121">Zadejte "MLModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="36e0d-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="36e0d-122">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="36e0d-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="36e0d-123">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="36e0d-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="36e0d-124">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="36e0d-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="36e0d-125">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko v dialogovém okně přijetí licence, pokud souhlasíte s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="36e0d-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="36e0d-126">Nainstalujte **balíček Nuget Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="36e0d-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="36e0d-127">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="36e0d-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="36e0d-128">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="36e0d-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="36e0d-129">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko v dialogovém okně přijetí licence, pokud souhlasíte s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="36e0d-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="36e0d-130">Přidání modelu do projektu webového rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36e0d-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="36e0d-131">Zkopírujte předem sestavených model *MLModels* adresáře</span><span class="sxs-lookup"><span data-stu-id="36e0d-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="36e0d-132">V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor zip modelu a vyberte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="36e0d-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="36e0d-133">V části Upřesnit změňte hodnotu kopírovat do výstupního adresáře ke zkopírování, pokud je novější.</span><span class="sxs-lookup"><span data-stu-id="36e0d-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="36e0d-134">Vytvoření datových modelů</span><span class="sxs-lookup"><span data-stu-id="36e0d-134">Create data models</span></span>

<span data-ttu-id="36e0d-135">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="36e0d-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="36e0d-136">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="36e0d-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="36e0d-137">Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů:</span><span class="sxs-lookup"><span data-stu-id="36e0d-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="36e0d-138">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="36e0d-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="36e0d-139">Zadejte "DataModels" a stiskněte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="36e0d-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="36e0d-140">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost Přidat > Nová položka.</span><span class="sxs-lookup"><span data-stu-id="36e0d-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="36e0d-141">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="36e0d-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="36e0d-142">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="36e0d-142">Then, select the **Add** button.</span></span> <span data-ttu-id="36e0d-143">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="36e0d-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="36e0d-144">Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="36e0d-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="36e0d-145">Odeberte stávající definice třídy a přidejte následující kód, který **SentimentData.cs** souboru:</span><span class="sxs-lookup"><span data-stu-id="36e0d-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="36e0d-146">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="36e0d-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="36e0d-147">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="36e0d-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="36e0d-148">Vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="36e0d-148">Then, select the Add button.</span></span> <span data-ttu-id="36e0d-149">*SentimentPrediction.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="36e0d-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="36e0d-150">Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="36e0d-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="36e0d-151">Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="36e0d-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="36e0d-152">`SentimentPrediction` dědí z `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="36e0d-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="36e0d-153">To usnadňuje v původní data `SentimentText` vlastnost společně s výstupem generovaných modelu.</span><span class="sxs-lookup"><span data-stu-id="36e0d-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="36e0d-154">Zaregistrujte PredictionEnginePool pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="36e0d-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="36e0d-155">Chcete-li jeden predikcí, použijte [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="36e0d-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="36e0d-156">Chcete-li použít [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) ve vaší aplikaci je třeba jej vytvořit když ho nepotřebují.</span><span class="sxs-lookup"><span data-stu-id="36e0d-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="36e0d-157">V takovém případě je vhodné zvážit je vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="36e0d-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="36e0d-158">Pod následujícím odkazem najdete další informace, pokud chcete další informace o [injektáž závislostí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="36e0d-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="36e0d-159">Otevřít *Startup.cs* třídu a přidejte následující příkaz do horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="36e0d-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="36e0d-160">Přidejte následující kód, který *ConfigureServices* metody:</span><span class="sxs-lookup"><span data-stu-id="36e0d-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="36e0d-161">Na vysoké úrovni tento kód inicializuje objekty a služby automaticky, pokud je požadovaná aplikací místo nutnosti ručně provést.</span><span class="sxs-lookup"><span data-stu-id="36e0d-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="36e0d-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečné pro vlákna.</span><span class="sxs-lookup"><span data-stu-id="36e0d-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="36e0d-163">Pro lepší výkon a bezpečný přístup z více vláken, použijte `PredictionEnginePool` službu, která vytvoří [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` objekty při použití aplikace.</span><span class="sxs-lookup"><span data-stu-id="36e0d-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="36e0d-164">Přečtěte si další informace o následujícím příspěvku blogu [vytváření a používání `PredictionEngine` objektu fondů v ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="36e0d-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="36e0d-165">Vytvoření kontroleru Predict</span><span class="sxs-lookup"><span data-stu-id="36e0d-165">Create Predict controller</span></span>

<span data-ttu-id="36e0d-166">Ke zpracování příchozích žádostí HTTP, vytvořte kontroleru.</span><span class="sxs-lookup"><span data-stu-id="36e0d-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="36e0d-167">V Průzkumníku řešení klikněte pravým tlačítkem myši *řadiče* adresář a potom vyberte možnost **Přidat > kontroler**.</span><span class="sxs-lookup"><span data-stu-id="36e0d-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="36e0d-168">V **přidat novou položku** dialogu **prázdný kontroler API** a vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="36e0d-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="36e0d-169">Příkazový řádek změnu **názvu Kontroleru** pole *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="36e0d-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="36e0d-170">Vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="36e0d-170">Then, select the Add button.</span></span> <span data-ttu-id="36e0d-171">*PredictController.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="36e0d-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="36e0d-172">Přidejte následující příkaz k hornímu okraji *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="36e0d-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="36e0d-173">Odeberte stávající definice třídy a přidejte následující kód, který *PredictController.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="36e0d-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
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

<span data-ttu-id="36e0d-174">Tento kód přiřadí `PredictionEnginePool` předáním konstruktoru kontroleru, který můžete získat pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="36e0d-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="36e0d-175">Pak, bude `Predict` kontroleru `Post` metoda používá `PredictionEnginePool` k predikci a výsledek se vrátí zpět na uživatele v případě úspěšného ověření.</span><span class="sxs-lookup"><span data-stu-id="36e0d-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="36e0d-176">Místní test webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="36e0d-176">Test web API locally</span></span>

<span data-ttu-id="36e0d-177">Jakmile je všechno nastavené, je čas k otestování aplikace.</span><span class="sxs-lookup"><span data-stu-id="36e0d-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="36e0d-178">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="36e0d-178">Run the application.</span></span>
1. <span data-ttu-id="36e0d-179">Otevřete Powershell a zadejte následující kód, kde je port naslouchá vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="36e0d-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="36e0d-180">V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="36e0d-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="36e0d-181">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="36e0d-181">Congratulations!</span></span> <span data-ttu-id="36e0d-182">Jste úspěšně obsluhovat model k predikci přes internet pomocí rozhraní API pro ASP.NET Core Web.</span><span class="sxs-lookup"><span data-stu-id="36e0d-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="36e0d-183">Další kroky</span><span class="sxs-lookup"><span data-stu-id="36e0d-183">Next Steps</span></span>

- [<span data-ttu-id="36e0d-184">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="36e0d-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)