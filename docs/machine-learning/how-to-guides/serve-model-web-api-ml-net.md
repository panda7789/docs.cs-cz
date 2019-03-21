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
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a>Postupy: Slouží k Machine Learning Model prostřednictvím webové rozhraní API ASP.NET Core

Tento návod ukazuje, jak poskytovat předem sestavených ML.NET model strojového učení na web pomocí ASP.NET Core Web API. Tímto způsobem umožňuje uživatelům přístup k rozhraní API pro účely předpovědi přes standardní HTTP metody.

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložišti dotnet/machinelearning githubu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.
- Prostředí PowerShell.
- Předem natrénovaných modelů.
    - Použití [kurz analýza mínění ML.NET](../tutorials/sentiment-analysis.md) sestaví vlastní model.
    - Stáhněte si tuto aplikaci [model machine learning analýzy předem vytrénovaných mínění](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Vytvořte projekt webového rozhraní API ASP.NET Core

1. Otevřete Visual Studio 2017. Vyberte **soubor > Nový > projekt** z řádku nabídek. V dialogovém okně Nový projekt, vyberte **Visual C#**  uzel, za nímž následuje **webové** uzlu. Vyberte **webové aplikace ASP.NET Core** šablony projektu. V **název** textového pole zadejte "SentimentAnalysisWebAPI" a pak vyberte **OK** tlačítko.
1. V okně, které zobrazuje různé typy projektů ASP.NET Core, vyberte **API** a vyberte položku **OK** tlačítko.
1. Vytvořte adresář *MLModels* ve vašem projektu a uložit předem sestavených strojového učení soubory modelu:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka. Zadejte "MLModels" a stiskněte Enter.

1. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a klikněte na tlačítko nainstalovat. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko v dialogovém okně přijetí licence, pokud souhlasíte s licenčními podmínkami pro balíčky uvedené.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Přidání modelu s projektem webového rozhraní API ASP.NET Core

1. Zkopírujte předem sestavených model *MLModels* adresáře
1. V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor zip modelu a vyberte vlastnosti. V části Upřesnit změňte hodnotu kopírovat do výstupního adresáře ke zkopírování, pokud je novější.

## <a name="build-data-models"></a>Vytvářet datové modely

Je potřeba vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. Vytvořte adresář *DataModels* ve vašem projektu a uložit datových modelů:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte Přidat > Nová složka. Zadejte "DataModels" a stiskněte **Enter**.

2. V Průzkumníku řešení klikněte pravým tlačítkem myši *DataModels* adresář a potom vyberte možnost Přidat > Nová položka.
3. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko. *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentData.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

Odeberte stávající definice třídy a přidejte následující kód, který **SentimentData.cs** souboru:

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
5. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentPrediction.cs*. Vyberte tlačítko Přidat. *SentimentPrediction.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *SentimentPrediction.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
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

## <a name="register-predictionengine-for-use-in-application"></a>Zaregistrujte PredictionEngine pro použití v aplikaci

Chcete-li jeden predikcí, můžete použít `PredictionEngine`. Chcete-li použít `PredictionEngine` ve vaší aplikaci, budete muset pokaždé, když je potřeba ho vytvořit. V takovém případě je vhodné zvážit je injektáž závislostí ASP.NET Core.

Pod následujícím odkazem najdete další informace, pokud chcete další informace o [injektáž závislostí](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otevřít *Startup.cs* třídu a přidejte následující příkaz do horní části souboru:

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

2. Přidejte následující řádky kódu, který *ConfigureServices* metody:

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
> `PredictionEngine` není bezpečné pro vlákna. Způsob, jak můžete omezit náklady na vytvoření objektu je tím, že jeho doba platnosti služby *obor*. Objekty s vymezenou *životností* jsou stejné v rámci jednoho požadavku, ale jiné napříč různými požadavky. Navštivte následující odkaz na další informace o [služby životnosti](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).

Na vysoké úrovni tento kód inicializuje objekty a služby automaticky, pokud je požadovaná aplikací místo nutnosti ručně provést.

## <a name="create-predict-controller"></a>Vytvořte předpověď Kontroleru

Ke zpracování příchozích žádostí HTTP, budete muset vytvořit řadič.

1. V Průzkumníku řešení klikněte pravým tlačítkem myši *řadiče* adresář a potom vyberte možnost **Přidat > kontroler**.
1. V **přidat novou položku** dialogu **prázdný kontroler API** a vyberte **přidat**.
1. Příkazový řádek změnu **názvu Kontroleru** pole *PredictController.cs*. Vyberte tlačítko Přidat. *PredictController.cs* soubor se otevře v editoru kódu. Přidejte následující příkaz k hornímu okraji *PredictController.cs*:

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

Odeberte stávající definice třídy a přidejte následující kód, který *PredictController.cs* souboru:

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

Toto přiřazení `PredictionEngine` předáním konstruktoru kontroleru, který můžete získat pomocí vkládání závislostí. Pak na metodu POST tento kontroler `PredictionEngine` se používá k vytváření předpovědí a výsledek se vrátí zpět na uživatele v případě úspěšného ověření.

## <a name="test-web-api-locally"></a>Místní test webové rozhraní API

Jakmile je všechno nastavené, je čas k otestování aplikace.

1. Spusťte aplikaci.
1. Otevřete Powershell a zadejte následující kód, kde je port naslouchá vaše aplikace.

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

V případě úspěchu se výstup by měl vypadat podobně jako na následujícím textem:

```powershell
Toxic
```

Blahopřejeme! Jste úspěšně obsluhovat model k predikci přes internet pomocí rozhraní API pro ASP.NET Core.

## <a name="next-steps"></a>Další kroky

- [Nasazení do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)