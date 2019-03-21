---
title: Poskytování strojového učení modelu ve webovém rozhraní API ASP.NET Core
description: Poskytování modelu strojového učení ML.NET mínění analýzy prostřednictvím Internetu pomocí webového rozhraní API ASP.NET Core
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 0cc13ec22b3a8805ec4aa17bf10560b2564ccd63
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307912"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a><span data-ttu-id="6bb4e-103">Postupy: Slouží k Machine Learning Model prostřednictvím webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6bb4e-103">How-To: Serve Machine Learning Model Through ASP.NET Core Web API</span></span>

<span data-ttu-id="6bb4e-104">Tento návod ukazuje, jak poskytovat předem sestavených ML.NET model strojového učení na web pomocí ASP.NET Core Web API.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-104">This how-to shows how to serve a pre-built ML.NET machine learning model to the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="6bb4e-105">Tímto způsobem umožňuje uživatelům přístup k rozhraní API pro účely předpovědi přes standardní HTTP metody.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-105">By doing so it allows for users to access the API for prediction purposes via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="6bb4e-106">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="6bb4e-107">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6bb4e-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="6bb4e-108">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-108">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="6bb4e-109">Další informace najdete v tématu poznámky k verzi v [úložišti dotnet/machinelearning githubu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="6bb4e-109">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6bb4e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bb4e-110">Prerequisites</span></span>

- <span data-ttu-id="6bb4e-111">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-111">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="6bb4e-112">Prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-112">Powershell.</span></span>
- <span data-ttu-id="6bb4e-113">Předem natrénovaných modelů.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-113">Pre-trained model.</span></span>
    - <span data-ttu-id="6bb4e-114">Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestaví vlastní model.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="6bb4e-115">Stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="6bb4e-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="6bb4e-116">Vytvořte projekt webového rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6bb4e-116">Create ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="6bb4e-117">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="6bb4e-118">Vyberte **soubor > Nový > projekt** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-118">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="6bb4e-119">V dialogovém okně Nový projekt, vyberte **Visual C#**  uzel, za nímž následuje **webové** uzlu.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-119">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="6bb4e-120">Vyberte **webové aplikace ASP.NET Core** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-120">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="6bb4e-121">V **název** textového pole zadejte "SentimentAnalysisWebAPI" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-121">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>
1. <span data-ttu-id="6bb4e-122">V okně, které zobrazuje různé typy projektů ASP.NET Core, vyberte **API** a vyberte položku **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-122">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>
1. <span data-ttu-id="6bb4e-123">Vytvořte adresář *MLModels* ve vašem projektu a uložit předem sestavených strojového učení soubory modelu:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-123">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="6bb4e-124">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-124">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="6bb4e-125">Zadejte "MLModels" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-125">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="6bb4e-126">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="6bb4e-127">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="6bb4e-128">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="6bb4e-129">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko v dialogovém okně přijetí licence, pokud souhlasíte s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="6bb4e-130">Přidání modelu s projektem webového rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6bb4e-130">Add Model to ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="6bb4e-131">Zkopírujte předem sestavených model *MLModels* adresáře</span><span class="sxs-lookup"><span data-stu-id="6bb4e-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="6bb4e-132">V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor zip modelu a vyberte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="6bb4e-133">V části Upřesnit změňte hodnotu kopírovat do výstupního adresáře ke zkopírování, pokud je novější.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="build-data-models"></a><span data-ttu-id="6bb4e-134">Vytvářet datové modely</span><span class="sxs-lookup"><span data-stu-id="6bb4e-134">Build Data Models</span></span>

<span data-ttu-id="6bb4e-135">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="6bb4e-136">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="6bb4e-137">Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="6bb4e-138">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="6bb4e-139">Zadejte "DataModels" a stiskněte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="6bb4e-140">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost Přidat > Nová položka.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="6bb4e-141">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="6bb4e-142">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-142">Then, select the **Add** button.</span></span> <span data-ttu-id="6bb4e-143">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="6bb4e-144">Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="6bb4e-145">Odeberte stávající definice třídy a přidejte následující kód, který **SentimentData.cs** souboru:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }   
}
```

4. <span data-ttu-id="6bb4e-146">V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="6bb4e-147">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="6bb4e-148">Vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-148">Then, select the Add button.</span></span> <span data-ttu-id="6bb4e-149">*SentimentPrediction.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="6bb4e-150">Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="6bb4e-151">Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

## <a name="register-predictionengine-for-use-in-application"></a><span data-ttu-id="6bb4e-152">Zaregistrujte PredictionEngine pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="6bb4e-152">Register PredictionEngine for Use in Application</span></span>

<span data-ttu-id="6bb4e-153">Chcete-li jeden predikcí, můžete použít `PredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-153">To make a single prediction, you can use `PredictionEngine`.</span></span> <span data-ttu-id="6bb4e-154">Chcete-li použít `PredictionEngine` ve vaší aplikaci, budete muset pokaždé, když je potřeba ho vytvořit.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-154">In order to use `PredictionEngine` in your application you will have to create it every time it is needed.</span></span> <span data-ttu-id="6bb4e-155">V takovém případě je vhodné zvážit je injektáž závislostí ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-155">In that case, a best practice to consider is ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="6bb4e-156">Pod následujícím odkazem najdete další informace, pokud chcete další informace o [injektáž závislostí](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="6bb4e-156">The following link provides more information if you want to learn about [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="6bb4e-157">Otevřít *Startup.cs* třídu a přidejte následující příkaz do horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-157">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

2. <span data-ttu-id="6bb4e-158">Přidejte následující řádky kódu, který *ConfigureServices* metody:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-158">Add the following lines of code to the *ConfigureServices* method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddScoped<MLContext>();
    services.AddScoped<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
}
```

> [!WARNING]
> <span data-ttu-id="6bb4e-159">`PredictionEngine` není bezpečné pro vlákna.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-159">`PredictionEngine` is not thread-safe.</span></span> <span data-ttu-id="6bb4e-160">Způsob, jak můžete omezit náklady na vytvoření objektu je tím, že jeho doba platnosti služby *obor*.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-160">A way that you can limit the cost of creating the object is by making its service lifetime *Scoped*.</span></span> <span data-ttu-id="6bb4e-161">Objekty s vymezenou *životností* jsou stejné v rámci jednoho požadavku, ale jiné napříč různými požadavky.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-161">*Scoped* objects are the same within a request but different across requests.</span></span> <span data-ttu-id="6bb4e-162">Navštivte následující odkaz na další informace o [služby životnosti](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="6bb4e-162">Visit the following link to learn more about [service lifetimes](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).</span></span>

<span data-ttu-id="6bb4e-163">Na vysoké úrovni tento kód inicializuje objekty a služby automaticky, pokud je požadovaná aplikací místo nutnosti ručně provést.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-163">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

## <a name="create-predict-controller"></a><span data-ttu-id="6bb4e-164">Vytvořte předpověď Kontroleru</span><span class="sxs-lookup"><span data-stu-id="6bb4e-164">Create Predict Controller</span></span>

<span data-ttu-id="6bb4e-165">Ke zpracování příchozích žádostí HTTP, budete muset vytvořit řadič.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-165">To process your incoming HTTP requests, you need to create a controller.</span></span>

1. <span data-ttu-id="6bb4e-166">V Průzkumníku řešení klikněte pravým tlačítkem myši *řadiče* adresář a potom vyberte možnost **Přidat > kontroler**.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-166">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="6bb4e-167">V **přidat novou položku** dialogu **prázdný kontroler API** a vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-167">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="6bb4e-168">Příkazový řádek změnu **názvu Kontroleru** pole *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-168">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="6bb4e-169">Vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-169">Then, select the Add button.</span></span> <span data-ttu-id="6bb4e-170">*PredictController.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-170">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="6bb4e-171">Přidejte následující příkaz k hornímu okraji *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-171">Add the following using statement to the top of *PredictController.cs*:</span></span>

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

<span data-ttu-id="6bb4e-172">Odeberte stávající definice třídy a přidejte následující kód, který *PredictController.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-172">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

```csharp
public class PredictController : ControllerBase
{
    
    private readonly PredictionEngine<SentimentData,SentimentPrediction> _predictionEngine;

    public PredictController(PredictionEngine<SentimentData, SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine; //Define prediction engine
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }

        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return Ok(isToxic);
    }
    
}
```

<span data-ttu-id="6bb4e-173">Toto přiřazení `PredictionEngine` předáním konstruktoru kontroleru, který můžete získat pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-173">This is assigning the `PredictionEngine` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="6bb4e-174">Pak na metodu POST tento kontroler `PredictionEngine` se používá k vytváření předpovědí a výsledek se vrátí zpět na uživatele v případě úspěšného ověření.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-174">Then, in the POST method of this controller the `PredictionEngine` is being used to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="6bb4e-175">Místní test webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6bb4e-175">Test Web API Locally</span></span>

<span data-ttu-id="6bb4e-176">Jakmile je všechno nastavené, je čas k otestování aplikace.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-176">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="6bb4e-177">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-177">Run the application.</span></span>
1. <span data-ttu-id="6bb4e-178">Otevřete Powershell a zadejte následující kód, kde je port naslouchá vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-178">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="6bb4e-179">V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="6bb4e-179">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="6bb4e-180">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="6bb4e-180">Congratulations!</span></span> <span data-ttu-id="6bb4e-181">Jste úspěšně obsluhovat model k predikci přes internet pomocí rozhraní API pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6bb4e-181">You have successfully served your model to make predictions over the internet using an ASP.NET Core API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6bb4e-182">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6bb4e-182">Next Steps</span></span>

- [<span data-ttu-id="6bb4e-183">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="6bb4e-183">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)