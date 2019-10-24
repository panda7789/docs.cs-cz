---
title: Nasazení modelu do ASP.NET Core webového rozhraní API
description: Obsluha modelu strojového učení ML.NET mínění přes Internet pomocí ASP.NET Core webového rozhraní API
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b85d77900c5d9227ecc6fe81b8a8d68171dd9ef5
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774511"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="469cb-103">Nasazení modelu do ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="469cb-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="469cb-104">Naučte se, jak na webu sloužit předem trained ML.NET model strojového učení, pomocí ASP.NET Core webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="469cb-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="469cb-105">Obsluha modelu přes webové rozhraní API umožňuje předpovědi prostřednictvím standardních metod HTTP.</span><span class="sxs-lookup"><span data-stu-id="469cb-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="469cb-106">rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="469cb-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="469cb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="469cb-107">Prerequisites</span></span>

- <span data-ttu-id="469cb-108">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="469cb-108">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="469cb-109">Prostředí.</span><span class="sxs-lookup"><span data-stu-id="469cb-109">Powershell.</span></span>
- <span data-ttu-id="469cb-110">Předem vyškolený model.</span><span class="sxs-lookup"><span data-stu-id="469cb-110">Pre-trained model.</span></span> <span data-ttu-id="469cb-111">Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s představitelnou mínění analýzou](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) .</span><span class="sxs-lookup"><span data-stu-id="469cb-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="469cb-112">Vytvoření projektu webového rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="469cb-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="469cb-113">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="469cb-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="469cb-114">Z řádku nabídek vyberte **soubor > nový > projekt** .</span><span class="sxs-lookup"><span data-stu-id="469cb-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="469cb-115">V dialogovém okně Nový projekt vyberte uzel  **C# vizuálu** následovaný **webovým** uzlem.</span><span class="sxs-lookup"><span data-stu-id="469cb-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="469cb-116">Pak vyberte šablonu projektu **ASP.NET Core webové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="469cb-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="469cb-117">Do textového pole **název** zadejte "SentimentAnalysisWebAPI" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="469cb-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="469cb-118">V okně, které zobrazuje různé typy ASP.NET Core projektů, vyberte **rozhraní API** a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="469cb-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="469cb-119">Vytvořte ve svém projektu adresář s názvem *MLModels* a uložte předem sestavené soubory modelu Machine Learning:</span><span class="sxs-lookup"><span data-stu-id="469cb-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="469cb-120">V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="469cb-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="469cb-121">Zadejte "MLModels" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="469cb-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="469cb-122">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="469cb-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="469cb-123">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="469cb-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="469cb-124">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="469cb-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="469cb-125">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="469cb-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="469cb-126">Nainstalujte **balíček Nuget Microsoft.Extensions.ml**:</span><span class="sxs-lookup"><span data-stu-id="469cb-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="469cb-127">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="469cb-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="469cb-128">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="469cb-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="469cb-129">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="469cb-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="469cb-130">Přidání modelu do ASP.NET Core projektu webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="469cb-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="469cb-131">Zkopírování předem připraveného modelu do adresáře *MLModels*</span><span class="sxs-lookup"><span data-stu-id="469cb-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="469cb-132">V Průzkumník řešení klikněte pravým tlačítkem na soubor zip modelu a vyberte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="469cb-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="469cb-133">V části Upřesnit změňte hodnotu kopírovat do výstupního adresáře na kopírovat, pokud je novější.</span><span class="sxs-lookup"><span data-stu-id="469cb-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="469cb-134">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="469cb-134">Create data models</span></span>

<span data-ttu-id="469cb-135">Musíte vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="469cb-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="469cb-136">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="469cb-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="469cb-137">Vytvořte v projektu adresář s názvem *Datamodels* pro uložení datových modelů:</span><span class="sxs-lookup"><span data-stu-id="469cb-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="469cb-138">V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka.</span><span class="sxs-lookup"><span data-stu-id="469cb-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="469cb-139">Zadejte "datamodels" a stiskněte **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="469cb-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="469cb-140">V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte Přidat > nová položka.</span><span class="sxs-lookup"><span data-stu-id="469cb-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="469cb-141">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="469cb-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="469cb-142">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="469cb-142">Then, select the **Add** button.</span></span> <span data-ttu-id="469cb-143">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="469cb-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="469cb-144">Do horní části *SentimentData.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="469cb-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="469cb-145">Odeberte existující definici třídy a přidejte následující kód do souboru **SentimentData.cs** :</span><span class="sxs-lookup"><span data-stu-id="469cb-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

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

4. <span data-ttu-id="469cb-146">V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="469cb-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="469cb-147">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="469cb-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="469cb-148">Pak vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="469cb-148">Then, select the Add button.</span></span> <span data-ttu-id="469cb-149">V editoru kódu se otevře soubor *SentimentPrediction.cs* .</span><span class="sxs-lookup"><span data-stu-id="469cb-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="469cb-150">Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="469cb-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="469cb-151">Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="469cb-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="469cb-152">`SentimentPrediction` dědí z `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="469cb-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="469cb-153">To usnadňuje zobrazení původních dat ve vlastnosti `SentimentText` spolu s výstupem generovaným modelem.</span><span class="sxs-lookup"><span data-stu-id="469cb-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="469cb-154">Registrovat PredictionEnginePool pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="469cb-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="469cb-155">Chcete-li udělat jednu předpověď, je nutné vytvořit [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="469cb-155">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="469cb-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="469cb-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="469cb-157">Kromě toho musíte vytvořit instanci, která je všude, kde je to potřeba v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="469cb-157">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="469cb-158">Jak vaše aplikace roste, tento proces může být nespravovatelný.</span><span class="sxs-lookup"><span data-stu-id="469cb-158">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="469cb-159">Pro zlepšení výkonu a zabezpečení vlákna použijte kombinaci injektáže a `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="469cb-159">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="469cb-160">Následující odkaz poskytuje další informace, pokud se chcete dozvědět víc o [vkládání závislostí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="469cb-160">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="469cb-161">Otevřete třídu *Startup.cs* a na začátek souboru přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="469cb-161">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="469cb-162">Do metody *ConfigureServices* přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="469cb-162">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    }
    ```

<span data-ttu-id="469cb-163">Na vysoké úrovni tento kód automaticky inicializuje objekty a služby pro pozdější použití v případě, že je aplikace požaduje místo ručního provedení.</span><span class="sxs-lookup"><span data-stu-id="469cb-163">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="469cb-164">Modely strojového učení nejsou statické.</span><span class="sxs-lookup"><span data-stu-id="469cb-164">Machine learning models are not static.</span></span> <span data-ttu-id="469cb-165">Jakmile budou k dispozici nová školicí data, model se přeškolí a znovu nasadí.</span><span class="sxs-lookup"><span data-stu-id="469cb-165">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="469cb-166">Jedním ze způsobů, jak získat nejnovější verzi modelu do vaší aplikace, je znovu nasadit celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="469cb-166">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="469cb-167">Tím se ale zavádí výpadek aplikace.</span><span class="sxs-lookup"><span data-stu-id="469cb-167">However, this introduces application downtime.</span></span> <span data-ttu-id="469cb-168">Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti pořizovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="469cb-168">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="469cb-169">Nastavte parametr `watchForChanges` na `true` a `PredictionEnginePool` spustí [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , které naslouchají oznámením o změnách systému souborů a vyvolává události, když dojde ke změně souboru.</span><span class="sxs-lookup"><span data-stu-id="469cb-169">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="469cb-170">Tím se zobrazí výzva `PredictionEnginePool` pro automatické opětovné načtení modelu.</span><span class="sxs-lookup"><span data-stu-id="469cb-170">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="469cb-171">Model je identifikován parametrem `modelName`, aby bylo při změně možné znovu načíst více než jeden model na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="469cb-171">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="469cb-172">Alternativně můžete použít metodu `FromUri` při práci s místně uloženými modely.</span><span class="sxs-lookup"><span data-stu-id="469cb-172">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="469cb-173">Místo sledování událostí změněných souborů `FromUri` se dotazuje na vzdálené umístění pro změny.</span><span class="sxs-lookup"><span data-stu-id="469cb-173">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="469cb-174">Interval dotazování je ve výchozím nastavení nastaven na 5 minut.</span><span class="sxs-lookup"><span data-stu-id="469cb-174">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="469cb-175">Interval dotazování můžete zvýšit nebo snížit na základě požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="469cb-175">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="469cb-176">V níže uvedeném příkladu kódu `PredictionEnginePool` cyklické dotazování modelu uloženého v zadaném identifikátoru URI každou minutu.</span><span class="sxs-lookup"><span data-stu-id="469cb-176">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="469cb-177">Vytvořit kontroler předpovědi</span><span class="sxs-lookup"><span data-stu-id="469cb-177">Create Predict controller</span></span>

<span data-ttu-id="469cb-178">Pokud chcete zpracovat příchozí požadavky HTTP, vytvořte kontroler.</span><span class="sxs-lookup"><span data-stu-id="469cb-178">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="469cb-179">V Průzkumník řešení klikněte pravým tlačítkem na adresář *řadiče* a pak vyberte **Přidat > kontroler**.</span><span class="sxs-lookup"><span data-stu-id="469cb-179">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="469cb-180">V dialogovém okně **Přidat novou položku** vyberte možnost **kontroler rozhraní API prázdné** a vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="469cb-180">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="469cb-181">V příkazovém řádku změňte pole **název kontroleru** na *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="469cb-181">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="469cb-182">Pak vyberte tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="469cb-182">Then, select the Add button.</span></span> <span data-ttu-id="469cb-183">V editoru kódu se otevře soubor *PredictController.cs* .</span><span class="sxs-lookup"><span data-stu-id="469cb-183">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="469cb-184">Do horní části *PredictController.cs*přidejte následující příkaz using:</span><span class="sxs-lookup"><span data-stu-id="469cb-184">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="469cb-185">Odeberte existující definici třídy a přidejte následující kód do souboru *PredictController.cs* :</span><span class="sxs-lookup"><span data-stu-id="469cb-185">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

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

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="469cb-186">Tento kód přiřadí `PredictionEnginePool` předáním do konstruktoru kontroleru, který získáte prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="469cb-186">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="469cb-187">Pak metoda `Post` řadiče `Predict` používá `PredictionEnginePool` k vytvoření předpovědi pomocí `SentimentAnalysisModel` registrovaného ve třídě `Startup` a vrátí výsledky zpátky uživateli, pokud je úspěšný.</span><span class="sxs-lookup"><span data-stu-id="469cb-187">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="469cb-188">Místní testování webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="469cb-188">Test web API locally</span></span>

<span data-ttu-id="469cb-189">Jakmile je všechno nastavené, je čas otestovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="469cb-189">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="469cb-190">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="469cb-190">Run the application.</span></span>
1. <span data-ttu-id="469cb-191">Otevřete PowerShell a zadejte následující kód, kde PORT je port, na kterém naslouchá vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="469cb-191">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="469cb-192">V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:</span><span class="sxs-lookup"><span data-stu-id="469cb-192">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="469cb-193">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="469cb-193">Congratulations!</span></span> <span data-ttu-id="469cb-194">Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí webového rozhraní API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="469cb-194">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="469cb-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="469cb-195">Next Steps</span></span>

- [<span data-ttu-id="469cb-196">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="469cb-196">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
