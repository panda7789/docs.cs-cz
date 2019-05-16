---
title: Nasazení modelu do Azure Functions
description: Poskytování ML.NET mínění analýzy modelu strojového učení pro predikci přes internet pomocí služby Azure Functions
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 9e62d8826227aed07451387cc733d27094327f99
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645094"
---
# <a name="deploy-a-model-to-azure-functions"></a>Nasazení modelu do Azure Functions

Zjistěte, jak nasadit předem vytrénovaných ML.NET model strojového učení k předpovědi přes protokol HTTP pomocí prostředí Azure Functions bez serveru.

> [!NOTE]
> `PredictionEnginePool` rozšíření služby je aktuálně ve verzi preview.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) úlohy "Vývoj pro různé platformy .NET Core" a "Vývoj pro Azure" nainstalované.
- [Nástroje Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Powershell
- Předem natrénovaných modelů. Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestavovat vlastní model nebo stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Vytvoření projektu Azure Functions

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#**  uzel, za nímž následuje **cloudu** uzlu. Vyberte **Azure Functions** šablony projektu. V **název** textového pole zadejte "SentimentAnalysisFunctionsApp" a pak vyberte **OK** tlačítko.
1. V **nový projekt** dialogového okna, otevřete rozevírací seznam nahoře možnosti projektu a vyberte **Azure Functions v2 (.NET Core)**. Vyberte **triggeru Http** projektu a pak vyberte **OK** tlačítko.
1. Vytvořte adresář *MLModels* ve vašem projektu a uložit model:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "MLModels" a stiskněte Enter.

1. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

1. Nainstalujte **balíček NuGet Microsoft.Extensions.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.Extensions.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

## <a name="add-pre-trained-model-to-project"></a>Přidání předem vytrénovaných modelu do projektu

1. Zkopírujte předem sestavených model *MLModels* složky.
1. V Průzkumníku řešení klikněte pravým tlačítkem na soubor předem sestavených modelů a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Vytvoření funkce Azure analyzovat mínění

Vytvoření třídy k předpovědi mínění. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **funkce Azure Functions** a změnit **název** pole *AnalyzeSentiment.cs*. Vyberte **přidat** tlačítko.

1. V **novou funkci Azure Functions** dialogu **triggeru Http**. Vyberte **OK** tlačítko.

    *AnalyzeSentiment.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *AnalyzeSentiment.cs*:

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

    Ve výchozím nastavení `AnalyzeSentiment` třída je `static`. Ujistěte se, že chcete odebrat `static` – klíčové slovo z definice třídy.

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>Vytvoření datových modelů

Je potřeba vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů: V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**. Zadejte "DataModels" a stiskněte Enter.
2. V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.
3. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko. 

    *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Odeberte stávající definice třídy a přidejte následující kód, který *SentimentData.cs* souboru:
    
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

4. V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.
5. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*. Vyberte **přidat** tlačítko. *SentimentPrediction.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` dědí z `SentimentData` poskytující přístup k původní data v `SentimentText` vlastnosti a také výstup generovaný model.

## <a name="register-predictionenginepool-service"></a>Zaregistrovat službu PredictionEnginePool

Chcete-li jeden predikcí, použijte [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602). Chcete-li použít [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) ve vaší aplikaci je třeba jej vytvořit když ho nepotřebují. V takovém případě je vhodné zvážit je vkládání závislostí.

Pod následujícím odkazem najdete další informace, pokud chcete další informace o [injektáž závislostí](https://en.wikipedia.org/wiki/Dependency_injection).

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *Startup.cs*. Vyberte **přidat** tlačítko. 

    *Startup.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *Startup.cs*:

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Odeberte existující kód podle následujících příkazů a přidejte následující kód, který *Startup.cs* souboru:

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

Na vysoké úrovni tento kód inicializuje objekty a služby automaticky, pokud je požadovaná aplikací místo nutnosti ručně provést.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečné pro vlákna. Pro lepší výkon a bezpečný přístup z více vláken, použijte `PredictionEnginePool` službu, která vytvoří [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` objekty při použití aplikace. 

## <a name="register-startup-as-an-azure-functions-extension"></a>Zaregistrujte se při spuštění jako rozšíření Azure Functions

Chcete-li použít `Startup` ve vaší aplikaci, budete muset zaregistrovat jako rozšíření Azure Functions. Vytvořte nový soubor s názvem *extensions.json* ve vašem projektu, pokud ještě neexistuje.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **nová položka** dialogového okna, vyberte **Visual C#**  uzel, za nímž následuje **webové** uzlu. Vyberte **soubor Json** možnost. V **název** textového pole zadejte "extensions.json" a pak vyberte **OK** tlačítko.

    *Extensions.json* soubor se otevře v editoru kódu. Přidejte následující obsah, který se *extensions.json*:
    
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

1. V Průzkumníku řešení klikněte pravým tlačítkem na váš *extensions.json* a vyberte možnost **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

## <a name="load-the-model-into-the-function"></a>Načíst model do funkce

Vložte následující kód *AnalyzeSentiment* třídy:

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

Tento kód přiřadí `PredictionEnginePool` předáním funkce konstruktoru, který můžete získat pomocí vkládání závislostí.

## <a name="use-the-model-to-make-predictions"></a>Použít model k predikci

Nahraďte stávající implementaci *spustit* metoda *AnalyzeSentiment* třídy následujícím kódem:

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

Když `Run` metody, je deserializovat a použít jako vstup pro příchozí data z požadavku HTTP `PredictionEnginePool`. `Predict` Metoda je volána poté generovat predikcí a vrátí výsledek pro uživatele. 

## <a name="test-locally"></a>Místní test

Teď, když je všechno nastavené, je čas k otestování aplikace:

1. Spuštění aplikace
1. Otevřete PowerShell a zobrazený kód zadejte do řádku, kde je port vaše aplikace běží na. Port, který je obvykle 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:
    
    ```powershell
    Negative
    ```

Blahopřejeme! Jste úspěšně obsluhovat model k predikci přes internet pomocí funkce Azure functions.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
