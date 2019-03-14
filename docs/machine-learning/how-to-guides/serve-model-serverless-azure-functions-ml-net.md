---
title: Nasazení modelu ML.NET na službu Azure Functions
description: Poskytování ML.NET mínění analýzy modelu strojového učení pro predikci přes internet pomocí služby Azure Functions
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: db29e37660665b02ab93a07b37418f0c4c20a608
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788653"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a>Postupy: Použití ML.NET modelu ve službě Azure Functions

Tento návod ukazuje, jak jednotlivé předpovědi je možné provádět pomocí předem sestavených ML.NET model strojového učení prostřednictvím Internetu v prostředí bez serveru, třeba Azure Functions.

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložišti dotnet/machinelearning githubu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) úlohy "Vývoj pro různé platformy .NET Core" a "Vývoj pro Azure" nainstalované. 
- [Nástroje Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Powershell
- Předem natrénovaných modelů. 
    - Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestaví vlastní model.
    - Stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Vytvoření projektu Azure Functions

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#**  uzel, za nímž následuje **cloudu** uzlu. Vyberte **Azure Functions** šablony projektu. V **název** textového pole zadejte "SentimentAnalysisFunctionsApp" a pak vyberte **OK** tlačítko.
1. V **nový projekt** dialogového okna, otevřete rozevírací seznam nahoře možnosti projektu a vyberte **Azure Functions v2 (.NET Core)**. Vyberte **triggeru Http** projektu a pak vyberte **OK** tlačítko.
1. Vytvořte adresář *MLModels* ve vašem projektu a uložit model:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "MLModels" a stiskněte Enter.

1. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

## <a name="add-pre-built-model-to-project"></a>Přidat do projektu předem sestavených modelů

1. Zkopírujte předem sestavených model *MLModels* složky.
1. V Průzkumníku řešení klikněte pravým tlačítkem na soubor předem sestavených modelů a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

## <a name="create-function-to-analyze-sentiment"></a>Vytvoření funkce pro analýzu mínění

Vytvoření třídy k předpovědi mínění. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **funkce Azure Functions** a změnit **název** pole *AnalyzeSentiment.cs*. Vyberte **přidat** tlačítko.

1. V **novou funkci Azure Functions** dialogu **triggeru Http**. Vyberte **OK** tlačítko.

    *AnalyzeSentiment.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *GitHubIssueData.cs*:

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
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a>Vytvoření datových modelů

Je potřeba vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů: V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová složka**. Zadejte "DataModels" a stiskněte Enter.
2. V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.
3. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko. *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:

```csharp
using Microsoft.ML.Data;
```

Odeberte stávající definice třídy a přidejte následující kód do souboru SentimentData.cs:

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost **Přidat > Nová položka**.
5. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*. Vyberte **přidat** tlačítko. *SentimentPrediction.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:

```csharp
using Microsoft.ML.Data;
```

Odeberte stávající definice třídy a přidejte následující kód, který *SentimentPrediction.cs* souboru:

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a>Přidání logiky Predikcí

Nahraďte stávající implementaci *spustit* metoda *AnalyzeSentiment* třídy následujícím kódem:

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a>Místní test

Teď, když je všechno nastavené, je čas k otestování aplikace:

1. Spuštění aplikace
1. Otevřete PowerShell a zobrazený kód zadejte do řádku, kde je port vaše aplikace běží na. Port, který je obvykle 7071. 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:

```powershell
Toxic
```

Blahopřejeme! Jste úspěšně obsluhovat model k predikci přes internet pomocí funkce Azure functions.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)