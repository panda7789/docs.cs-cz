---
title: 'Kurz: Analýza mínění - binární klasifikace'
description: Tento kurz ukazuje, jak vytvořit aplikaci Razor Pages, která klasifikuje mínění z komentářů na webu a provede příslušnou akci. Binární třídění mínění používá Model Builder v sadě Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 7761240055c90ae9c713b1c460e9e83316d256f9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278948"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Kurz: Analýza mínění komentářů na webových stránkách ve webové aplikaci pomocí ML.NET Model Builder

Naučte se analyzovat mínění z komentářů v reálném čase uvnitř webové aplikace.

Tento kurz vám ukáže, jak vytvořit aplikaci ASP.NET Core Razor Pages, která klasifikuje mínění z komentářů na webu v reálném čase.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvoření aplikace ASP.NET Core Razor Pages
> - Příprava a pochopení dat
> - Výběr scénáře
> - Načtení dat
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

> [!NOTE]
> Tvůrce modelů je momentálně ve verzi Preview.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples)

## <a name="pre-requisites"></a>Požadavky

Seznam předpokladů a pokynů k instalaci naleznete v [instalační příručce výrobce modelů](../how-to-guides/install-model-builder.md).

## <a name="create-a-razor-pages-application"></a>Vytvoření aplikace Razor Pages

1. Vytvořte **aplikaci ASP.NET Core Razor Pages**.

    1. Otevřete Visual Studio a z panelu nabídek vyberte **Soubor > Nový > Project.**
    1. V dialogovém okně Nový projekt vyberte uzel **Visual C#** následovaný **webovým** uzlem.
    1. Pak vyberte šablonu projektu **ASP.NET core webová aplikace.**
    1. Do textového pole **Název** zadejte "SentimentRazor".
    1. Ujistěte se, že **umístit řešení a projekt ve stejném adresáři** je **nezaškrtnuté** (VS 2019) nebo **vytvořit adresář pro řešení** je **zaškrtnuto** (VS 2017).
    1. Vyberte tlačítko **OK**.
    1. V okně, které zobrazuje různé typy ASP.NET základní projekty, zvolte **Webová aplikace** a pak vyberte tlačítko **OK.**

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

Stáhnout [Wikipedia detox datový soubor](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv). Po otevření webové stránky klikněte pravým tlačítkem myši na stránku a vyberte **Uložit jako** a soubor uložte kdekoli v počítači.

Každý řádek v datové sadě *wikipedia-detox-250-line-data.tsv* představuje jinou recenzi, kterou uživatel zanechal na Wikipedii. První sloupec představuje mínění textu (0 je netoxický, 1 je toxický) a druhý sloupec představuje komentář, který uživatel zanechal. Sloupce jsou odděleny kartami. Data vypadají takto:

| Mínění | SentimentText |
| :---: | :---: |
1 | ==RUDE== Dude, ty jsou hrubý nahrát, že carl obrázek zpět, nebo jinak.
1 | == OK! == IM chystá vandalize wild ones WIKI pak!!!
0 | Doufám, že to pomůže.

## <a name="choose-a-scenario"></a>Výběr scénáře

![Průvodce tvůrcem modelů v sadě Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Chcete-li trénovat model, musíte vybrat ze seznamu dostupných scénářů strojového učení poskytovaných tvůrcem modelů.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt *SentimentRazor* a vyberte **přidat** > **strojové učení**.
1. Pro tuto ukázku je scénář analýza mínění. V kroku *scénáře* nástroje Tvůrce modelů vyberte scénář **Analýzy mínění.**

## <a name="load-the-data"></a>Načtení dat

Tvůrce modelů přijímá data ze dvou zdrojů, databáze serveru `csv` `tsv` SQL Server nebo místního souboru ve formátu nebo formátu.

1. V datovém kroku nástroje Tvůrce modelů vyberte **Soubor** z rozevíracího souboru zdroje dat.
1. Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů procházejte a vyberte soubor *wikipedia-detox-250-line-data.tsv.*
1. V rozevíracím **seznamu Sloupce zvolte Mínění, které chcete předpovědět (Popisek).** **Sentiment**
1. Ponechte výchozí hodnoty pro rozevírací seznam **Vstupní sloupce (Funkce).**
1. Vyberte spojení **Vlak,** chcete-li přejít k dalšímu kroku v nástroji Tvůrce modelů.

## <a name="train-the-model"></a>Trénování modelu

Úloha strojového učení použitá k trénování modelu analýzy mínění v tomto kurzu je binární klasifikace. Během procesu školení modelu Model Builder trénuje samostatné modely pomocí různých binárních klasifikačních algoritmů a nastavení, aby našel nejvýkonnější model pro vaši datovou sadu.

Doba potřebná pro vyškolení modelu je úměrná množství dat. Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas pro trénování (sekundy)** na základě velikosti zdroje dat.

1. Přestože Model Builder nastaví hodnotu **Čas trénovat (sekundy)** na 10 sekund, zvyšte ji na 30 sekund. Školení pro delší časové zpracování umožňuje Model Builder prozkoumat větší počet algoritmů a kombinace parametrů při hledání nejlepší model.
1. Vyberte **možnost Zahájit trénink**.

    V průběhu tréninkového procesu se `Progress` údaje o průběhu zobrazují v části kroku vlaku.

    - Stav zobrazuje stav dokončení procesu školení.
    - Nejlepší přesnost zobrazuje přesnost nejvýkonnějšího modelu, který dosud našel Model Builder. Vyšší přesnost znamená, že model byl na testovacích datech předpovězen správněji.
    - Nejlepší algoritmus zobrazí název nejvýkonnějšíalgoritmus u kterého našel Model Builder tak daleko.
    - Poslední algoritmus zobrazí název algoritmu, který byl naposledy použit tvůrcem modelů k trénování modelu.

1. Po dokončení tréninku vyberte odkaz **vyhodnocení** a přejděte k dalšímu kroku.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Výsledkem kroku školení bude jeden model, který má nejlepší výkon. V kroku vyhodnocení nástroje Tvůrce modelů bude výstupní část obsahovat algoritmus používaný nejvýkonnějším modelem v položce **Nejlepší model** spolu s metrikami v **kategorii Nejlepší přesnost modelu**. Dále se zobrazí souhrnná tabulka obsahující prvních pět modelů a jejich metriky.

Pokud nejste spokojeni s metrikami přesnosti, některé jednoduché způsoby, jak se pokusit zlepšit přesnost modelu, je prodloužit dobu pro trénování modelu nebo použití více dat. V opačném případě vyberte odkaz **kódu,** který chcete přesunout do posledního kroku v nástroji Tvůrce modelů.

## <a name="add-the-code-to-make-predictions"></a>Přidání kódu pro předpověď

V důsledku procesu školení budou vytvořeny dva projekty.

### <a name="reference-the-trained-model"></a>Odkaz na trénovaný model

1. V kroku *kódu* nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.

    V **Průzkumníku řešení**by se měly objevit následující projekty :

    - *SentimentRazorML.ConsoleApp*: Aplikace .NET Core Console, která obsahuje model školení a předpověď kódu.
    - *SentimentRazorML.Model*: Knihovna tříd .NET Standard obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, stejně jako uloženou verzi nejvýkonnějšího modelu během trénování.

    Pro účely tohoto kurzu pouze *SentimentRazorML.Model* projektu se používá, protože předpovědi budou provedeny ve webové aplikaci *SentimentRazor* spíše než v konzoli. Přestože *SentimentRazorML.ConsoleApp* nebude použit pro vyhodnocování, lze jej použít k přeškolit model pomocí nových dat později. Rekvalifikace je mimo rozsah tohoto kurzu ačkoli.

### <a name="configure-the-predictionengine-pool"></a>Konfigurace fondu PredictionEngine

Chcete-li provést jednu předpověď, <xref:Microsoft.ML.PredictionEngine%602>musíte vytvořit . <xref:Microsoft.ML.PredictionEngine%602>není bezpečný pro přístup z více vláken. Kromě toho budete muset vytvořit instanci všude, kde je potřeba v rámci aplikace. Jak vaše aplikace roste, tento proces může být nezvladatelný. Pro zvýšení výkonu a bezpečnosti podprocesů použijte `PredictionEnginePool` kombinaci vkládání <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601> závislostí a služby, která vytvoří objekty <xref:Microsoft.ML.PredictionEngine%602> pro použití v celé aplikaci.

1. Nainstalujte *balíček Microsoft.Extensions.ML* NuGet:

    1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**.
    1. Jako zdroj balíčku zvolte "nuget.org".
    1. Vyberte kartu **Procházet** a vyhledejte **Microsoft.Extensions.ML**.
    1. Vyberte balíček v seznamu a vyberte tlačítko **Instalovat.**
    1. Výběr tlačítka **OK** v dialogovém okně **Náhled změn**
    1. Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, vyberte v dialogovém okně **Přijetí licence** tlačítko **Souhlasím.**

1. Otevřete soubor *Startup.cs* v projektu *SentimentRazor.*
1. Přidejte následující příkazy pomocí odkazování na *Microsoft.Extensions.ML* NuGet balíček a *SentimentRazorML.Model* projektu:

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Vytvořte globální proměnnou pro uložení umístění trénovaného souboru modelu.

    ```csharp
    private readonly string _modelPath;
    ```

1. Soubor modelu je uložen v adresáři sestavení vedle souborů sestavení aplikace. Chcete-li usnadnit přístup, vytvořte `GetAbsolutePath` pomocnou `Configure` metodu volanou po metodě

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. Pomocí `GetAbsolutePath` metody v `Startup` konstruktoru třídy nastavte `_modelPath`.

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. Nakonfigurujte `PredictionEnginePool` pro `ConfigureServices` vaši aplikaci v metodě:

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Vytvoření obslužné rutiny analýzy mínění

Předpovědi budou provedeny uvnitř hlavní stránky aplikace. Proto je třeba přidat metodu, `PredictionEnginePool` která přebírá vstup uživatele a používá k vrácení předpověď.

1. Otevřete *soubor Index.cshtml.cs* umístěný v adresáři *Stránky* a přidejte následující příkazy:

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    Chcete-li použít `PredictionEnginePool` nakonfigurované ve `Startup` třídě, musíte jej vložit do konstruktoru modelu, kde jej chcete použít.

1. Přidejte proměnnou, `PredictionEnginePool` která `IndexModel` odkazuje na vnitřní třídu.

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. Vytvořte konstruktor `IndexModel` ve třídě `PredictionEnginePool` a vložte do něj službu.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. Vytvořte obslužnou rutinu `PredictionEnginePool` metody, která používá k vytváření předpovědí z uživatelského vstupu přijatého z webové stránky.

    1. Pod `OnGet` metodou vytvořte novou metodu nazvanou`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. Uvnitř `OnGetAnalyzeSentiment` metody vrátí *neutrální* mínění, pokud je vstup od uživatele prázdný nebo null.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. Daný platný vstup, vytvořit novou `ModelInput`instanci .

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Použijte `PredictionEnginePool` k předvídání mínění.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Převeďte `bool` předpokládanou hodnotu na toxickou nebo netoxickou pomocí následujícího kódu.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Nakonec vraťte sentiment zpět na webovou stránku.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Konfigurace webové stránky

Výsledky vrácené `OnGetAnalyzeSentiment` bude dynamicky zobrazí na `Index` webové stránce.

1. Otevřete soubor *Index.cshtml* v adresáři *Stránky* a nahraďte jeho obsah následujícím kódem:

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Dále přidejte kód stylů css na konec stránky *site.css* v adresáři *wwwroot\css:*

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Poté přidejte kód pro odeslání vstupů z `OnGetAnalyzeSentiment` webové stránky do obslužné rutiny.

    1. V souboru *site.js* umístěném v adresáři *wwwroot\js* vytvořte funkci volanou `getSentiment` `OnGetAnalyzeSentiment` pro vytvoření požadavku GET HTTP se vstupem uživatele do obslužné rutiny.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Pod tím přidejte `updateMarker` další funkci volanou k dynamické aktualizaci pozice značky na webové stránce podle předpovědi mínění.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Vytvořte volanou `updateSentiment` funkci obslužné rutiny `OnGetAnalyzeSentiment` události, `getSentiment` abyste získali vstup `updateMarker` od uživatele, odešlete ji do funkce pomocí funkce a aktualizujte značku pomocí funkce.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Nakonec zaregistrujte obslužnou `textarea` rutinu `id=Message` události a spojte ji s elementem s atributem.

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Spuštění aplikace

Nyní, když je aplikace nastavena, spusťte aplikaci, která by se měla spustit ve vašem prohlížeči.

Když se aplikace spustí, zadejte *Model Builder je v pohodě!* do textové oblasti. Zobrazený předpokládaný názor by neměl být *toxický*.

![Spuštěné okno s předpovídaným oknem mínění](./media/sentiment-analysis-model-builder/web-app.png)

Pokud potřebujete odkazovat na projekty generované tvůrcem modelů později uvnitř jiného `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` řešení, můžete je najít uvnitř adresáře.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvoření aplikace ASP.NET Core Razor Pages
> - Příprava a pochopení dat
> - Výběr scénáře
> - Načtení dat
> - Trénování modelu
> - Vyhodnocení modelu
> - Použití modelu pro předpovědi

### <a name="additional-resources"></a>Další zdroje

Další informace o tématech uvedených v tomto kurzu naleznete v následujících zdrojích:

- [Scénáře tvůrce modelů](../automate-training-with-model-builder.md#scenario)
- [Binární klasifikace](../resources/glossary.md#binary-classification)
- [Binární klasifikace model metriky](../resources/metrics.md#evaluation-metrics-for-binary-classification)
