---
title: Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku ML.NET
description: Automaticky generovat modelu ML a související C# kódu z ukázkové datové sadě
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 2679df0317fede9fa5f3885831c65bd87a14981a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960390"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a>Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku

Další informace o použití rozhraní příkazového řádku ML.NET k automatickému generování modelu ML.NET a příslušná C# kódu. Zadejte vaše datová sada a strojového učení úkol, který chcete implementovat a rozhraní příkazového řádku používá modul AutoML pro vytvoření generování modelu a nasazení zdrojového kódu, jakož i binárnímu modelu.

V tomto kurzu provedete následující kroky:
> [!div class="checklist"]
> * Příprava dat pro úlohu učení vybraný počítač
> * Z rozhraní příkazového řádku spusťte příkaz "mlnet automaticky – train"
> * Kontrola výsledků metrik kvality
> * Vysvětlení generované C# kódu k použití modelu v aplikaci
> * Prozkoumejte generované C# kód, který byl použit pro trénování modelu

> [!NOTE]
> Toto téma odkazuje na nástroj ML.NET rozhraní příkazového řádku, který je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Rozhraní příkazového řádku ML.NET je součástí ML.NET a jeho hlavním cílem je "demokratizaci" ML.NET pro vývojáře na platformě .NET při učení ML.NET, takže není nutné do kódu od začátku začít.

Rozhraní příkazového řádku ML.NET můžete spustit na libovolné příkazového řádku (Windows, Mac nebo Linux) ke generování kvalitních ML.NET modely a zdrojový kód podle cvičných datových sad, které zadáte.

## <a name="pre-requisites"></a>Požadavky

- [Sada .NET core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo novější
- (Volitelné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)
- [ML.NET CLI](../how-to-guides/install-ml-net-cli.md)

Můžete spustit buď generované C# projekty ze sady Visual Studio nebo pomocí kódu `dotnet run` (.NET Core CLI).

## <a name="prepare-your-data"></a>Příprava dat

Budeme používat existující datovou sadu používají pro scénáře "Analýza mínění", což je úloha binární klasifikace strojového učení. Vlastní datové sady můžete použít podobným způsobem, a modelu a kódu vygeneruje se pro vás.

1. Stáhněte si [soubor zip The UCI subjektivního hodnocení s popiskem věty datové sady (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho v jakékoli složce zvolíte.

    > [!NOTE]
    > Datové sady v tomto kurzu používá datovou sadu ze "From skupiny na jednotlivé popisky pomocí podrobné funkce" Kotzias a další. Konference KDD 2015 a hostované v UCI Machine Learning úložiště – Dua, D. a Karra Taniskidou, E. (2017). UCI strojového učení úložiště [http://archive.ics.uci.edu/ml]. Irvine, certifikační Autorita: University of California, z informací o škole a počítačových věd.

2. Kopírovat `yelp_labelled.txt` souboru do libovolné složky, kterou jste vytvořili dřív (například `/cli-test`).

3. Otevřete upřednostňované příkazový řádek a přejděte do složky, kam jste zkopírovali soubor datové sady. Příklad:

    ```console
    > cd /cli-test
    ```

    Pomocí libovolného textového editoru, jako je Visual Studio Code, můžete otevřít a prozkoumejte `yelp_labelled.txt` soubor datové sady. Uvidíte, že struktura je:

    - Soubor nemá žádné hlavičky. Sloupce indexu bude používat.

    - Existují jenom dva sloupce:

        | Text (index sloupce 0) | Popisek (index sloupce 1)|
        |--------------------------|-------|
        | WOW... Miluju toto místo. | 1 |
        | Povrch ovšem není vhodné. | 0 |
        | Není tasty a byla právě nepříjemným textury. | 0 |
        | ... MNOHO VÍCE ŘÁDKŮ TEXTU... | ... (1 nebo 0)... |

    Ujistěte se, že zavřete soubor datové sady z editoru.

    Nyní jste připraveni začít používat rozhraní příkazového řádku pro tento scénář "Analýza mínění".

    > [!NOTE]
    > Po dokončení tohoto kurzu můžete také zkusit s vlastními datovými sadami, dokud jsou připravená k použití pro všechny úkoly ML aktuálně podporované ve verzi Preview ML.NET rozhraní příkazového řádku, které jsou *"Binární klasifikace", "Roc klasifikaci" a " Regrese "*).

## <a name="run-the-mlnet-auto-train-command"></a>Spusťte příkaz "mlnet automaticky – train"

1. Spusťte následující příkaz rozhraní příkazového řádku ML.NET:

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Tento příkaz spustí  **`mlnet auto-train` příkaz**:
    - pro **ML úloh** typu **`binary-classification`**
    - používá **soubor datové sady `yelp_labelled.txt`**  jako trénování a testování datovou sadu (interně rozhraní příkazového řádku se použít křížové ověření nebo rozdělit ji ve dvou datových sad, jeden pro trénování a jeden pro účely testování)
    - kde **cíle/cílový sloupec** chcete předpovědět (obvykle říká **"štítku"**) je **sloupec s indexem 1** (to znamená druhý sloupec, protože index je založený na nule )
    - nemá **nepoužívat záhlaví souboru** s názvy sloupců, protože tento konkrétní datové sady soubor nemá hlavičku
    - **cílené zkoumání čas** experimentu je **10 sekund**

    Zobrazí se výstup z rozhraní příkazového řádku, podobně jako:

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    V tomto konkrétním případě v jenom 10 sekund a u malé datové sady k dispozici, nástroj rozhraní příkazového řádku bylo možné spustit poměrně několika iteracích, což znamená více než jednou podle různých kombinací algoritmy/konfigurace s různými daty interních školení transformace a pro algoritmus hyperparametrů. 

    A konečně "co nejlepší kvalitu" modelu nalezen za 10 sekund je model s použitím konkrétního trainer/algoritmu s žádnou zvláštní konfiguraci. V závislosti na času zkoumání příkaz může vytvářet jiné výsledky. Výběr vychází z více metrik zobrazených, jako například `Accuracy`.

    **Principy metrik kvality modelu**

    První a nejjednodušší metrika k vyhodnocení binární klasifikační model je přesnost, což je srozumitelný. "Přesnost je poměr správné předpovědi s testovací datové sady.". Blíže na 100 % (1,00), tím lépe.

    Existují však případy, kde právě s metrikou přesnost měření nestačí, zejména v případě, že je v datové sadě testů nevyvážená popisek (0 a 1 v tomto případě).

    Pro další metriky a další **podrobné informace o metriky** například přesnost, AUC, AUCPR F1 skóre používá k vyhodnocení různých modelů, můžete si přečíst [Principy ML.NET metriky](../resources/metrics.md)

    > [!NOTE]
    >  Můžete zkuste tento velmi stejné datové sady a zadejte několik minut, než `--max-exploration-time` (například tři minuty umožňující vám zadat 180 sekund) který najdou lepší "nejlepší model" za vás s konfigurací kanálu různých školení pro tuto datovou sadu (což je velmi malé, řádky 1000). 
        
    Pokud chcete zjistit "kvality nejlepší/dobré" model, který je "připravené pro produkční prostředí model" cílení na větších datových sad, měli byste zajistit experimenty pomocí rozhraní příkazového řádku zadáním obvykle mnohem více času zkoumání v závislosti na velikosti datové sady. Ve skutečnosti v řadě případů může vyžadovat více hodin od času zkoumání zejména v případě, že datová sada je velká na řádky a sloupce. 

1. Předchozí provádění příkazu vygenerovalo následující prostředky:

    - Serializovaný model soubor .zip ("nejlepší model") připravený k použití. 
    - C#vytvořit kód pro spuštění/skóre, které model (k následné predikci ve vašich aplikacích koncového uživatele pomocí tohoto modelu).
    - C#školení kód používaný k vygenerování tohoto modelu (výukové účely).
    - Soubor protokolu s všech iterací s konkrétní podrobnosti o jednotlivých algoritmů s jeho kombinací hyperparametry a data transformace prozkoumali jste ji. 

    První dva prostředky (. Model souboru ZIP a C# kód ke spuštění tohoto modelu) lze použít přímo v aplikacích s koncovým uživatelem (webové aplikace ASP.NET Core, služby, aplikace klasické pracovní plochy, atd.) k následné predikci s generovaných modelu ML.

    Třetí asset školení kód ukazuje, jaký kód ML.NET API rozhraní příkazového řádku použil tak moct trénovat vygenerovaný model, takže si můžete zjistit, jaké konkrétní trainer/algoritmus a hyperparametrů nebyly vybrány pomocí rozhraní příkazového řádku.

Tyto prostředky výčtu jsou vysvětlené v následujících krocích tohoto kurzu.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Prozkoumejte generované C# kód, který použijete pro spouštění model k predikci

1. V sadě Visual Studio (2017 nebo 2019) otevřete řešení, vygeneruje ve složce s názvem `SampleBinaryClassification` v rámci původní cílovou složku (v tomto kurzu se název `/cli-test`). Měli byste vidět podobně jako řešení:

    > [!NOTE]
    > V tomto kurzu doporučujeme používat Visual Studio, ale můžete si taky prostudovat generované C# (dva projekty) pomocí libovolného textového editoru kódu a spuštění aplikace vygenerované konzoly v jazyce `dotnet CLI` v systému macOS, počítače s Linuxem nebo Windows.

    ![Řešení VS, které jsou generovány pomocí rozhraní příkazového řádku](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Vygenerovaný **knihovny tříd** obsahující serializovaná modelu ML (soubor .zip) a datových tříd (datové modely) je něco, co chcete využít přímo ve vaší aplikaci koncový uživatel ještě můžete přímo odkazuje na knihovny tříd (nebo při přenosech kód, jako je dáváte přednost).
    - Vygenerovaný **konzolovou aplikaci** obsahuje provádění kód, který musíte zkontrolovat, a potom obvykle budou bodování kód (kód, který spouští modelu ML k následné predikci) tohoto jednoduchého kódu (jenom pár řádků) se přesunete na vaše koncové uživatele aplikace, ve které chcete predikci. 

1. Otevřít **ModelInput.cs** a **ModelOutput.cs** třídy souborů v projektu knihovny tříd. Uvidíte, že tyto třídy jsou 'datové třídy' nebo POCO třídy sloužící k uchování dat. Je "často používaný kód", ale užitečné mít je generována, pokud vaše datová sada obsahuje desítky nebo stovky sloupce. 
    - `ModelInput` Třída se používá při čtení dat z datové sady. 
    - `ModelOutput` Třída se používá k získání výsledku predikcí (předpověď data).

1. Otevřete soubor Program.cs a prozkoumejte kód. V několika málo řádků budete moct spustit model a předpověď vzorku.

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it 
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- První řádek kódu jednoduše vytvoří `MLContext` objektů potřebných při každém spuštění ML.NET kódu. 

- Druhý řádek kódu je zakomentovaný, protože není nutné pro trénování, že serializován model, protože byl již školení pro vás pomocí nástroje příkazového řádku a uloží do modelu. Soubor ZIP. Ale pokud chcete zobrazit *"jak model se trénuje"* pomocí rozhraní příkazového řádku, mohli byste zrušením komentáře u tohoto řádku a spustit/ladit kód školení použité pro tento konkrétní modelu ML.

- Na třetím řádku kódu načíst model z serializovaný model. Soubor ZIP s `mlContext.Model.Load()` API tím, že poskytuje cestu k tomuto modelu. Soubor ZIP.

- Na čtvrtém řádku kódu můžete načíst vytvořit `PredictionEngine` objektu `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` rozhraní API. Je nutné `PredictionEngine` objekt vždy, když chcete při předpovědích cílí na jeden vzorek dat (v tomto případě jediný textu k předpovědi jeho mínění).

- Pátý řádek kódu je, kde můžete vytvářet, který *jedna ukázková data* použitého pro předpověď voláním funkce `CreateSingleDataSample()`. Protože nástroj rozhraní příkazového řádku nebude vědět, jaký druh ukázková data se mají použít, v rámci této funkce nahrávání první řádek datové sady. Ale pro tento případ můžete také vytvořit můžete vlastní data "pevně" namísto aktuální implementace `CreateSingleDataSample()` funkce aktualizací takto jednodušší implementaci této funkce:

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. Spusťte projekt, buď pomocí původní ukázková data načíst z prvního řádku datové sady nebo tím, že poskytuje vlastní pevně zakódovaný ukázková data. By vám měl predikcí srovnatelná s hodnotou:

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    Spustit konzolovou aplikaci v sadě Visual Studio stisknutím klávesy F5 (tlačítko Přehrát):

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    Spuštění aplikace konzoly z příkazového řádku zadáním následujících příkazů:

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Rozhraní příkazového řádku ML.NET tréninkem automaticky v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Zkuste změnit pevně zakódované ukázková data do jiných vět s jinou mínění a podívejte, jak tento model předpovídá pozitivní nebo negativní zabarvení. 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Do vašich koncových uživatelů aplikací vnést předpovědí modelu ML

Můžete použít, podobně jako "ML model bodování kódu" spustit model ve vašich koncových uživatelů aplikace a zkontrolujte předpovědi. 

Například může přímo přesunete tento kód do jakékoli aplikace klasické pracovní plochy Windows, jako **WPF** a **WinForms** a spustit model stejným způsobem, než jste to udělali v aplikaci konzoly.

Ale způsob, jak implementovat tyto řádky kódu ke spuštění modelu ML by mělo být optimalizované (která je mezipaměť souboru .zip modelu a načtěte ho jednou) a máte objektů typu singleton místo vytvoření u každého požadavku, zejména v případě, že vaše aplikace musí být škálovatelné, jako webové aplikace nebo distribuované služby, jak je vysvětleno v následující části.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Spouštění modelů ML.NET škálovatelné webové aplikace ASP.NET Core a služby (vícevláknové aplikace)

Vytvoření modelu objektu (`ITransformer` načtenou ze souboru ZIP do modelu) a `PredictionEngine` objektu by mělo být optimalizované, zejména pokud provozujete škálovatelných webových aplikací a distribuované služby. Pro první případ objekt modelu (`ITransformer`) optimalizace je jednoduché. Vzhledem k tomu, `ITransformer` objekt je bezpečná pro vlákno, můžete ukládat do mezipaměti objekt jako singleton nebo statický objekt, načíst model jednou.

Pro druhý objekt `PredictionEngine` objektu, není to jednoduché vzhledem k tomu `PredictionEngine` objektu není bezpečná pro vlákno, proto nelze vytvořit instanci tohoto objektu jako singleton nebo statických objektů v aplikaci ASP.NET Core. Tento problém bezpečné pro vlákna a škálovatelnost je podmínkou pro výrazně popsané v tomto [Blogový příspěvek](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/). 

Ale bylo mnohem snazší pro vás než jak je vysvětleno v tomto blogovém příspěvku. Jsme pro vás byla vhodná v jednodušší přístup a vytvořili dobrý **balíček .NET Core integrace** , snadno můžete ve svých aplikacích ASP.NET Core a služby tak, že zaregistrujete ve službě aplikace DI (injektáž závislostí služby) a pak přímo použít v kódu. Zkontrolujte následující kurz a příklad učinit:

- [Kurz: Spouštění modelů ML.NET v ASP.NET Core škálovatelné webové aplikace a WebAPIs](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: Škálovatelný model ML.NET v ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Prozkoumejte generované C# kód, který byl použit pro trénování modelu "co nejlepší kvalitu" 

Pro další pokročilé výukové účely, můžete si taky prostudovat generované C# kód, který se použil nástroj rozhraní příkazového řádku pro trénování vytvořený model.

Že "trénování modelu kódu" je momentálně ve třídě vlastní, vygenerované s názvem `ModelBuilder` tak můžete prozkoumat tento kód školení.

Důležitější je pro tento konkrétní scénář (modelů analýza mínění) můžete také porovnat, že kód vygenerovaný školení s kódem je popsáno v následujícím kurzu:

- Porovnání: [Kurz: Použít ve scénáři binární klasifikace analýzy subjektivního hodnocení ML.NET](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).

To je zajímavé k porovnání zvolené konfigurace algoritmus a kanál v tomto kurzu se kód vygenerovaný pomocí nástroje příkazového řádku. V závislosti na tom, kolik času trávíte iterace a vyhledávání pro lepší modely mohou být odlišná spolu s jeho konkrétním hyperparametry a konfigurace kanálu zvolený algoritmus.

## <a name="see-also"></a>Viz také:

- [Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Kurz: Spouštění modelů ML.NET v ASP.NET Core škálovatelné webové aplikace a WebAPIs](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: Škálovatelný model ML.NET v ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [Rozhraní příkazového řádku ML.NET automaticky trénování příkaz referenční příručka](../reference/ml-net-cli-reference.md) 
- [Postup instalace nástroje ML.NET rozhraní příkazového řádku (CLI)](../how-to-guides/install-ml-net-cli.md)
- [Telemetrie v rozhraní příkazového řádku ML.NET](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Příprava dat pro vybraný úkol ML (problém vyřešit)
> * Spusťte příkaz "mlnet automaticky – train" v nástroji příkazového řádku
> * Kontrola výsledků metrik kvality
> * Vysvětlení generované C# kód spustit model (kód pro použití v aplikaci pro koncové uživatele)
> * Prozkoumejte generované C# kód, který byl použit pro trénování modelu "co nejlepší kvalitu" (výukové účely)

> [!div class="nextstepaction"]
> [Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
