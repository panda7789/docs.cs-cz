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
# <a name="deploy-a-model-to-azure-functions"></a>Nasazení modelu do Azure Functions

Naučte se, jak nasadit předem vyškolený model ML.NET Machine Learning pro předpovědi přes protokol HTTP prostřednictvím prostředí bez serveru Azure Functions.

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "vývoj pro různé platformy pro .NET Core" a "vývoj pro Azure".
- Microsoft. NET. SDK. Functions Package NuGet verze 1.0.28 +.
- [Nástroje Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Prostředí
- Předem vyškolený model. Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) představitelnou mínění analýzou.

## <a name="create-azure-functions-project"></a>Vytvořit Azure Functions projekt

1. Otevřete Visual Studio 2017. Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** . V dialogovém okně **Nový projekt** vyberte uzel **vizuálu C#**  následovaný uzlem cloudu . Pak vyberte šablonu projektu **Azure Functions** . Do textového pole **název** zadejte "SentimentAnalysisFunctionsApp" a pak vyberte tlačítko **OK** .
1. V dialogovém okně **Nový projekt** otevřete rozevírací seznam nad možnostmi projektu a vyberte **Azure Functions v2 (.NET Core)** . Pak vyberte projekt **triggeru http** a pak klikněte na tlačítko **OK** .
1. Vytvořte v projektu adresář s názvem *MLModels* a uložte svůj model:

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat** > **novou složku**. Zadejte "MLModels" a stiskněte klávesu ENTER.

1. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

1. Nainstalujte **balíček NuGet Microsoft. Azure. Functions. Extensions**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft. Azure. Functions. Extensions**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

1. Nainstalujte **balíček NuGet Microsoft.Extensions.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

1. Aktualizujte **balíček NuGet Microsoft. NET. SDK. Functions** na verzi 1.0.28 +:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu nainstalované, vyhledejte **Microsoft. NET. SDK. Functions**, vyberte tento balíček v seznamu, vyberte v rozevírací nabídce verze možnost 1.0.28 nebo novější a klikněte na tlačítko **aktualizovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

## <a name="add-pre-trained-model-to-project"></a>Přidat předem vyškolený model do projektu

1. Do složky *MLModels* zkopírujte předem sestavený model.
1. V Průzkumník řešení klikněte pravým tlačítkem na předem sestavený soubor modelu a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Vytvoření funkce Azure pro analýzu mínění

Vytvořte třídu pro předpověď mínění. Přidejte do projektu novou třídu:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte možnost **Azure Functions** a změňte pole **název** na *AnalyzeSentiment.cs*. Pak vyberte tlačítko **Přidat** .

1. V dialogovém okně **Nová funkce Azure** vyberte **Trigger http**. Pak vyberte tlačítko **OK** .

    V editoru kódu se otevře soubor *AnalyzeSentiment.cs* . Do horní části `using` *AnalyzeSentiment.cs*přidejte následující příkaz:

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

    Ve výchozím nastavení `AnalyzeSentiment` je `static`třída. Nezapomeňte odebrat `static` klíčové slovo z definice třídy.

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>Vytváření datových modelů

Musíte vytvořit některé třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

1. Vytvořte v projektu adresář s názvem datamodels pro uložení datových modelů: V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **přidat > nová složka**. Zadejte "datamodels" a stiskněte ENTER.
2. V Průzkumník řešení klikněte pravým tlačítkem na adresář datamodels a pak vyberte **Přidat > Nová položka**.
3. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*. Pak vyberte tlačítko **Přidat** . 

    V editoru kódu se otevře soubor *SentimentData.cs* . Do horní části *SentimentData.cs*přidejte následující příkaz using:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentData.cs* :
    
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

4. V Průzkumník řešení klikněte pravým tlačítkem na adresář datamodels a pak vyberte **Přidat > Nová položka**.
5. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*. Pak vyberte tlačítko **Přidat** . V editoru kódu se otevře soubor *SentimentPrediction.cs* . Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Odeberte existující definici třídy a přidejte následující kód do souboru *SentimentPrediction.cs* :

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction`dědí z `SentimentData` , který poskytuje přístup k původním datům `SentimentText` ve vlastnosti a také výstup vygenerovaného modelem.

## <a name="register-predictionenginepool-service"></a>Zaregistrovat službu PredictionEnginePool

K provedení jedné předpovědi použijte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). Aby bylo možné v [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) aplikaci používat, musíte ji vytvořit, až bude potřeba. V takovém případě je osvědčeným postupem použití injektáže závislostí.

Následující odkaz poskytuje další informace, pokud chcete získat informace o [vkládání závislostí](https://en.wikipedia.org/wiki/Dependency_injection).

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *Startup.cs*. Pak vyberte tlačítko **Přidat** . 

    V editoru kódu se otevře soubor *Startup.cs* . Do horní části *Startup.cs*přidejte následující příkaz using:

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Odeberte existující kód pod příkazy using a přidejte následující kód do souboru *Startup.cs* :

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

Na vysoké úrovni tento kód automaticky inicializuje objekty a služby, pokud je aplikace požaduje, místo toho, aby ji ručně provedete.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken. Pro zlepšení výkonu a bezpečnosti vláken použijte `PredictionEnginePool` službu, která [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) vytvoří `PredictionEngine` objekty pro použití aplikací. 

## <a name="load-the-model-into-the-function"></a>Načtení modelu do funkce

Do třídy *AnalyzeSentiment* vložte následující kód:

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

Tento kód přiřadí `PredictionEnginePool` rozhraní předáním do konstruktoru funkce, který obdržíte prostřednictvím injektáže závislosti.

## <a name="use-the-model-to-make-predictions"></a>Použití modelu k vytvoření předpovědi

Nahraďte stávající implementaci metody *Run* ve třídě *AnalyzeSentiment* následujícím kódem:

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

Když se `Run` Metoda spustí, příchozí data z požadavku HTTP se deserializovat a použijí se jako vstup `PredictionEnginePool`pro. `Predict` Metoda je pak volána, aby vygenerovala předpověď a vrátila výsledek uživateli. 

## <a name="test-locally"></a>Test lokálně

Teď, když je všechno nastavené, je čas otestovat aplikaci:

1. Spuštění aplikace
1. Otevřete PowerShell a zadejte kód do příkazového řádku, kde PORT je port, na kterém je vaše aplikace spuštěná. Obvykle je port 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:
    
    ```powershell
    Negative
    ```

Blahopřejeme! Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí funkce Azure Functions.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
