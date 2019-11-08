---
title: Nasazení modelu do ASP.NET Core webového rozhraní API
description: Obsluha modelu strojového učení ML.NET mínění přes Internet pomocí ASP.NET Core webového rozhraní API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733304"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Nasazení modelu do ASP.NET Core webového rozhraní API

Naučte se, jak na webu sloužit předem trained ML.NET model strojového učení, pomocí ASP.NET Core webového rozhraní API. Obsluha modelu přes webové rozhraní API umožňuje předpovědi prostřednictvím standardních metod HTTP.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.
- Prostředí.
- Předem vyškolený model. Pomocí [kurzu ML.NET analýza mínění](../tutorials/sentiment-analysis.md) sestavte svůj vlastní model nebo si stáhněte tento [model služby Machine Learning s představitelnou mínění analýzou](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) .

## <a name="create-aspnet-core-web-api-project"></a>Vytvoření projektu webového rozhraní API ASP.NET Core

1. Otevřete Visual Studio 2017. Z řádku nabídek vyberte **soubor > nový > projekt** . V dialogovém okně Nový projekt vyberte uzel  **C# vizuálu** následovaný **webovým** uzlem. Pak vyberte šablonu projektu **ASP.NET Core webové aplikace** . Do textového pole **název** zadejte "SentimentAnalysisWebAPI" a pak vyberte tlačítko **OK** .

1. V okně, které zobrazuje různé typy ASP.NET Core projektů, vyberte **rozhraní API** a klikněte na tlačítko **OK** .

1. Vytvořte ve svém projektu adresář s názvem *MLModels* a uložte předem sestavené soubory modelu Machine Learning:

    V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka. Zadejte "MLModels" a stiskněte klávesu ENTER.

1. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat. Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .

1. Nainstalujte **balíček Nuget Microsoft.Extensions.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.Extensions.ml**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat. Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro přijetí licence vyberte tlačítko **přijmout** .

### <a name="add-model-to-aspnet-core-web-api-project"></a>Přidání modelu do ASP.NET Core projektu webového rozhraní API

1. Zkopírování předem připraveného modelu do adresáře *MLModels*
1. V Průzkumník řešení klikněte pravým tlačítkem na soubor zip modelu a vyberte vlastnosti. V části Upřesnit změňte hodnotu kopírovat do výstupního adresáře na kopírovat, pokud je novější.

## <a name="create-data-models"></a>Vytváření datových modelů

Musíte vytvořit některé třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

1. Vytvořte v projektu adresář s názvem *Datamodels* pro uložení datových modelů:

    V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka. Zadejte "datamodels" a stiskněte **ENTER**.

2. V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte Přidat > nová položka.
3. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*. Pak vyberte tlačítko **Přidat** . V editoru kódu se otevře soubor *SentimentData.cs* . Do horní části *SentimentData.cs*přidejte následující příkaz using:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Odeberte existující definici třídy a přidejte následující kód do souboru **SentimentData.cs** :

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

4. V Průzkumník řešení klikněte pravým tlačítkem na adresář *Datamodels* a pak vyberte **Přidat > Nová položka**.
5. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentPrediction.cs*. Pak vyberte tlačítko Přidat. V editoru kódu se otevře soubor *SentimentPrediction.cs* . Do horní části *SentimentPrediction.cs*přidejte následující příkaz using:

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

    `SentimentPrediction` dědí z `SentimentData`. To usnadňuje zobrazení původních dat ve vlastnosti `SentimentText` spolu s výstupem generovaným modelem.

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Registrovat PredictionEnginePool pro použití v aplikaci

Chcete-li udělat jednu předpověď, je nutné vytvořit [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken. Kromě toho musíte vytvořit instanci, která je všude, kde je to potřeba v rámci vaší aplikace. Jak vaše aplikace roste, tento proces může být nespravovatelný. Pro zlepšení výkonu a zabezpečení vlákna použijte kombinaci injektáže a `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.

Následující odkaz poskytuje další informace, pokud se chcete dozvědět víc o [vkládání závislostí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otevřete třídu *Startup.cs* a na začátek souboru přidejte následující příkaz using:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Do metody *ConfigureServices* přidejte následující kód:

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

Na vysoké úrovni tento kód automaticky inicializuje objekty a služby pro pozdější použití v případě, že je aplikace požaduje místo ručního provedení.

Modely strojového učení nejsou statické. Jakmile budou k dispozici nová školicí data, model se přeškolí a znovu nasadí. Jedním ze způsobů, jak získat nejnovější verzi modelu do vaší aplikace, je znovu nasadit celou aplikaci. Tím se ale zavádí výpadek aplikace. Služba `PredictionEnginePool` poskytuje mechanismus pro opětovné načtení aktualizovaného modelu bez nutnosti pořizovat aplikaci.

Nastavte parametr `watchForChanges` na `true` a `PredictionEnginePool` spustí [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , které naslouchají oznámením o změnách systému souborů a vyvolává události, když dojde ke změně souboru. Tím se zobrazí výzva `PredictionEnginePool` pro automatické opětovné načtení modelu.

Model je identifikován parametrem `modelName`, aby bylo při změně možné znovu načíst více než jeden model na aplikaci.

> [!TIP]
> Alternativně můžete použít metodu `FromUri` při práci s místně uloženými modely. Místo sledování událostí změněných souborů `FromUri` se dotazuje na vzdálené umístění pro změny. Interval dotazování je ve výchozím nastavení nastaven na 5 minut. Interval dotazování můžete zvýšit nebo snížit na základě požadavků vaší aplikace. V níže uvedeném příkladu kódu `PredictionEnginePool` cyklické dotazování modelu uloženého v zadaném identifikátoru URI každou minutu.
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a>Vytvořit kontroler předpovědi

Pokud chcete zpracovat příchozí požadavky HTTP, vytvořte kontroler.

1. V Průzkumník řešení klikněte pravým tlačítkem na adresář *řadiče* a pak vyberte **Přidat > kontroler**.
1. V dialogovém okně **Přidat novou položku** vyberte možnost **kontroler rozhraní API prázdné** a vyberte **Přidat**.
1. V příkazovém řádku změňte pole **název kontroleru** na *PredictController.cs*. Pak vyberte tlačítko Přidat. V editoru kódu se otevře soubor *PredictController.cs* . Do horní části *PredictController.cs*přidejte následující příkaz using:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Odeberte existující definici třídy a přidejte následující kód do souboru *PredictController.cs* :

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

Tento kód přiřadí `PredictionEnginePool` předáním do konstruktoru kontroleru, který získáte prostřednictvím vkládání závislostí. Pak metoda `Post` řadiče `Predict` používá `PredictionEnginePool` k vytvoření předpovědi pomocí `SentimentAnalysisModel` registrovaného ve třídě `Startup` a vrátí výsledky zpátky uživateli, pokud je úspěšný.

## <a name="test-web-api-locally"></a>Místní testování webového rozhraní API

Jakmile je všechno nastavené, je čas otestovat aplikaci.

1. Spusťte aplikaci.
1. Otevřete PowerShell a zadejte následující kód, kde PORT je port, na kterém naslouchá vaše aplikace.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    V případě úspěchu by měl výstup vypadat podobně jako v následujícím textu:

    ```powershell
    Negative
    ```

Blahopřejeme! Úspěšně jste zasloužili vašemu modelu, aby se předpovědi přes Internet pomocí webového rozhraní API ASP.NET Core.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
