---
title: Analýza mínění pomocí rozhraní příkazového řádku ML.NET
description: Automaticky generovat model ML a související kód Jazyka C# z ukázkové datové sady
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 832124e6d027b240c4d06692ee87c84f57b982d3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243333"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>Analýza mínění pomocí rozhraní příkazového řádku ML.NET

Zjistěte, jak pomocí ML.NET cli automaticky generovat ML.NET modelu a základní kód C#. Poskytujete datovou sadu a úlohu strojového učení, kterou chcete implementovat, a cli používá modul Automatické ml k vytvoření generování modelu a zdrojového kódu nasazení, stejně jako binární model.

V tomto kurzu provedete následující kroky:
> [!div class="checklist"]
>
> - Příprava dat na vybraný úkol strojového učení
> - Spusťte příkaz "mlnet auto-train" z rozhraní příkazového příkazu
> - Kontrola výsledků metrik kvality
> - Principy generované ho C# kód pro použití modelu ve vaší aplikaci
> - Prozkoumejte vygenerovaný kód jazyka C#, který byl použit k trénování modelu

> [!NOTE]
> Toto téma odkazuje na nástroj ML.NET cli, který je aktuálně ve verzi Preview, a materiál může být může být může změnit. Další informace naleznete na [stránce ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

ML.NET CLI je součástí ML.NET a jeho hlavním cílem je "demokratizovat" ML.NET pro vývojáře .NET při učení ML.NET, takže nemusíte kódovat od nuly, abyste mohli začít.

PříkazclML.NET můžete spustit na libovolném příkazovém řádku (Windows, Mac nebo Linux) a generovat kvalitní ML.NET modely a zdrojový kód založený na trénovacích datových sadách, které zadáte.

## <a name="pre-requisites"></a>Požadavky

- [Sada .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo novější
- (Nepovinné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)
- [Rozhraní příkazového řádku ML.NET](../how-to-guides/install-ml-net-cli.md)

Můžete buď spustit vygenerované projekty kódu Jazyka `dotnet run` C# z Visual Studia nebo pomocí (.NET Core CLI).

## <a name="prepare-your-data"></a>Příprava dat

Budeme používat existující datovou sadu použitou pro scénář analýzy mínění, což je úloha strojového učení s binární klasifikací. Můžete použít vlastní datovou sadu podobným způsobem a model a kód budou generovány za vás.

1. Stáhněte si [soubor zip datové sady UCI Sentiment Labeled Sentences (viz citace v následující poznámce)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte jej v libovolné složce, kterou zvolíte.

    > [!NOTE]
    > Datové sady tohoto kurzu používá datovou sadu ze skupiny na jednotlivé popisky pomocí deep features, Kotzias et al,. KDD 2015 a hostované v Úložišti strojového učení UCI - Dua, D. a Karra Taniskidou, E. (2017). Úložiště strojového učeníhttp://archive.ics.uci.edu/mlUCI [ ]. Irvine, KALIFORNIE: Kalifornská univerzita, Škola informací a informatiky.

2. Zkopírujte `yelp_labelled.txt` soubor do libovolné složky, `/cli-test`kterou jste dříve vytvořili (například ).

3. Otevřete upřednostňovaný příkazový řádek a přesuňte se do složky, do které jste soubor datové sady zkopírovali. Příklad:

    ```console
    cd /cli-test
    ```

    Pomocí libovolného textového `yelp_labelled.txt` editoru, jako je například Visual Studio Code, můžete otevřít a prozkoumat soubor datové sady. Můžete vidět, že struktura je:

    - Soubor nemá záhlaví. Budete používat index sloupce.

    - Existují pouze dva sloupce:

        | Text (index sloupce 0) | Popisek (index sloupce 1)|
        |--------------------------|-------|
        | Wow... Miloval toto místo. | 1 |
        | Kůrka není dobrá. | 0 |
        | Není chutné a textura byla prostě ošklivá. | 0 |
        | ... MNOHO DALŠÍCH ŘÁDKŮ TEXTU... | ... (1 nebo 0)... |

    Ujistěte se, že jste soubor datové sady zavřeli z editoru.

    Nyní jste připraveni začít používat vykreslování lisování- lis pro tento scénář analýzy mínění.

    > [!NOTE]
    > Po dokončení tohoto kurzu můžete také vyzkoušet s vlastní datové sady tak dlouho, dokud jsou připraveny k použití pro některý z úkolů ML v současné době podporuje ML.NET CLI Preview, které jsou *'binární klasifikace', 'Multi-class Klasifikace' a 'Regrese'*).

## <a name="run-the-mlnet-auto-train-command"></a>Spuštění příkazu "mlnet auto-train"

1. Spusťte následující ML.NET příkazem příkazu příkazu k příkazu příkazu:

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Tento příkaz spustí ** `mlnet auto-train` příkaz**:
    - pro **úlohu typu ML****`binary-classification`**
    - používá **soubor `yelp_labelled.txt` datové sady** jako trénovací a testovací datovou sadu (interní zaostřovací systém buď použije křížové ověření, nebo jej rozdělí do dvou datových sad, jednu pro školení a jednu pro testování)
    - kde **sloupec cíle/cíle,** který chcete předpovědět (běžně nazývaný **"popisek"),** je **sloupec s indexem 1** (to je druhý sloupec, protože index je založen na nule)
    - **Nepoužívá záhlaví souboru** s názvy sloupců, protože tento konkrétní soubor datové sady nemá záhlaví
    - **cílená doba průzkumu** experimentu je **10 sekund**

    Zobrazí se výstup z cli, podobně jako:

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[Windows](#tab/windows)

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[macOS Bash](#tab/macosbash)

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    V tomto konkrétním případě, za pouhých 10 sekund a s malou datovou sadou k dispozici, nástroj CLI byl schopen spustit poměrně málo iterací, což znamená školení vícekrát na základě různých kombinací algoritmů / konfigurace s různými interními transformacemi dat a hyperparametry algoritmu.

    Konečně, "nejlepší kvalita" model nalezený za 10 sekund je model pomocí konkrétního trenéra / algoritmu s jakoukoli konkrétní konfiguraci. V závislosti na době průzkumu příkaz může způsobit jiný výsledek. Výběr je založen na více zobrazených `Accuracy`metrikách, například .

    **Pochopení metrik kvality modelu**

    První a nejjednodušší metrika pro vyhodnocení binárního klasifikačního modelu je přesnost, která je snadno pochopitelná. "Přesnost je podíl správných předpovědí se sadou testovacích dat.". Čím blíže k 100% (1,00), tím lépe.

    Existují však případy, kdy stačí měření s metrikou přesnost nestačí, zejména pokud popisek (0 a 1 v tomto případě) je nevyvážený v testovací datové sadě.

    Další metriky a **podrobnější informace o metrikách,** jako je přesnost, AUC, AUCPR a skóre F1 použité k vyhodnocení různých modelů, najdete v [tématu Principy ML.NET metriky](../resources/metrics.md).

    > [!NOTE]
    > Můžete zkusit tuto velmi stejnou datovou `--max-exploration-time` sadu a zadat několik minut (například tři minuty, takže zadáte 180 sekund), který najde lepší "nejlepší model" pro vás s jinou konfiguraci trénovacího kanálu pro tuto datovou sadu (což je docela malé, 1000 řádků).

    Chcete-li najít model "nejlepší/dobrá kvalita", který je "model připravený k výrobě" zaměřený na větší datové sady, měli byste provádět experimenty s příkazovým příkazem, který obvykle určuje mnohem více času průzkumu v závislosti na velikosti datové sady. Ve skutečnosti v mnoha případech můžete vyžadovat více hodin doby průzkumu, zejména pokud je datová sada velká na řádcích a sloupcích.

1. Předchozí spuštění příkazu vygenerovalo následující prostředky:

    - Serializovaný model .zip ("nejlepší model") připravený k použití.
    - C# kód ke spuštění/skóre, které generované model (Chcete-li předpovědi v aplikacích koncových uživatelů s tímto modelem).
    - C# trénovací kód používaný ke generování tohoto modelu (Učení účely).
    - Soubor protokolu se všemi prozkoumány iterací s konkrétní podrobné informace o každém algoritmu se snažil s jeho kombinací hyper-parametry a transformace dat.

    První dva majetek (. ZIP model souboru a C# kód pro spuštění tohoto modelu) lze přímo použít ve vašich aplikacích pro koncové uživatele (ASP.NET základní webové aplikace, služby, desktop aplikace, atd.) k předpovědi s tímto generovaným modelem ML.

    Třetí prostředek, trénovací kód, vám ukáže, jaký ML.NET kód rozhraní API byl použit rozhraním API k trénování generovaného modelu, takže můžete zjistit, jaké konkrétní trenér/algoritmus a hyperparametry byly vybrány rozhraní matřištěm.

Tyto výčtové prostředky jsou vysvětleny v následujících krocích kurzu.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Prozkoumejte vygenerovaný kód Jazyka C#, který se má použít pro spuštění modelu, aby se předpovědi

1. V sadě Visual Studio (2017 nebo 2019) otevřete řešení generované ve složce `SampleBinaryClassification` `/cli-test`pojmenované v původní cílové složce (v kurzu byl pojmenován). Měli byste vidět řešení podobné:

    > [!NOTE]
    > V kurzu doporučujeme použít Visual Studio, ale můžete také prozkoumat generovaný kód Jazyka C# (dva projekty) s libovolným textovým editorem a spustit vygenerovanou konzolovou aplikaci s počítačem `dotnet CLI` s macOS, Linuxem nebo Windows.

    ![Řešení VS generované cli](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Vygenerovaná **knihovna tříd** obsahující serializovaný model ML (soubor ZIP) a datové třídy (datové modely) je něco, co můžete přímo použít v aplikaci koncového uživatele, a to i přímým odkazováním na tuto knihovnu tříd (nebo přesunutím kódu, jak dáváte přednost).
    - Vygenerovaná **konzolová aplikace** obsahuje kód spuštění, který je nutné zkontrolovat, a pak obvykle znovu použijete "bodovací kód" (kód, který spouští model ML, aby se předpovědi) přesunutím tohoto jednoduchého kódu (jen několik řádků) do aplikace koncového uživatele, kde chcete provést předpovědi.

1. Otevřete **soubory tříd ModelInput.cs** a **ModelOutput.cs** v rámci projektu knihovny tříd. Uvidíte, že tyto třídy jsou "třídy dat" nebo POCO třídy používané k ukládání dat. Je to 'často používaný kód', ale užitečné mít generované, pokud vaše datová sada má desítky nebo dokonce stovky sloupců.
    - Třída `ModelInput` se používá při čtení dat z datové sady.
    - Třída `ModelOutput` se používá k získání výsledku předpověď (data předpověď).

1. Otevřete soubor Program.cs a prozkoumejte kód. V několika řádcích, budete moci spustit model a provést ukázkovou předpověď.

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

    - První řádek kódu jednoduše `MLContext` vytvoří objekt potřebný při každém spuštění ML.NET kódu.

    - Druhý řádek kódu je komentovaný, protože nemusíte trénovat model, protože byl již vyškolen pro vás nástrojem CLI a uložen do modelu serializované . ZIP. Ale pokud chcete vidět *"jak byl model trénovaný"* cli, můžete odkomentovat tento řádek a spustit/ladit trénovací kód používaný pro tento konkrétní model ML.

    - Ve třetím řádku kódu načtete model z serializovaného modelu . ZIP s `mlContext.Model.Load()` rozhraním API poskytnutím cesty k tomuto modelu . ZIP.

    - Ve čtvrtém řádku kódu načtete `PredictionEngine` vytvořit `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` objekt s rozhraním API. Potřebujete `PredictionEngine` objekt vždy, když chcete provést předpověď cílení na jeden vzorek dat (V tomto případě jeden kus textu předpovědět jeho mínění).

    - Pátý řádek kódu je místo, kde můžete vytvořit, že *jeden ukázková data,* která mají být použita pro předpověď voláním funkce `CreateSingleDataSample()`. Vzhledem k tomu, že nástroj zaokreslování nezná, jaký druh ukázkových dat použít, v rámci této funkce načítá první řádek datové sady. V tomto případě však můžete také vytvořit vlastní "pevně zakódovaná" `CreateSingleDataSample()` data namísto aktuální implementace funkce aktualizací tohoto jednoduššího kódu implementujícího tuto funkci:

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. Spusťte projekt, a to buď pomocí původní ukázková data načtená z prvního řádku datové sady nebo poskytnutím vlastních pevně zakódovaných ukázkových dat. Měli byste získat předpověď srovnatelnou s:

    # <a name="windows"></a>[Windows](#tab/windows)

    Spusťte konzolovou aplikaci z Visual Studia stisknutím tlačítka F5 (Přehrát):

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bash"></a>[macOS Bash](#tab/macosbash)

    Spusťte konzolovou aplikaci z příkazového řádku zadáním následujících příkazů:

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![ML.NET automatického vytápětka v prostředí PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Zkuste změnit pevně zakódovaná ukázková data na jiné věty s jiným míněním a podívejte se, jak model předpovídá pozitivní nebo negativní mínění.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Naplnit aplikace koncových uživatelů předpověďmi modelu ML

Můžete použít podobný "ML model bodovací kód" ke spuštění modelu v aplikaci koncového uživatele a předpovědi.

Například můžete přímo přesunout tento kód do libovolné desktopové aplikace systému Windows, jako je **WPF** a **WinForms** a spustit model stejným způsobem, než tomu bylo v konzolové aplikaci.

Způsob implementace těchto řádků kódu pro spuštění modelu ML by však měl být optimalizován (tj. ukládat soubor modelu do mezipaměti a načíst jej jednou) a mít objekty singleton namísto jejich vytváření při každém požadavku, zejména pokud vaše aplikace musí být škálovatelná, například webová aplikace nebo distribuovaná služba, jak je vysvětleno v následující části.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Spuštění ML.NET modelů v škálovatelných ASP.NET webových aplikací a služeb Core (aplikace s více vlákny)

Vytvoření objektu modelu`ITransformer` (načteného ze souboru .zip `PredictionEngine` modelu) a objektu by mělo být optimalizováno zejména při spuštění v škálovatelných webových aplikacích a distribuovaných službách. Pro první případ je objekt`ITransformer`modelu ( ) optimalizace přímočará. Vzhledem `ITransformer` k tomu, že objekt je bezpečný pro přístup z více vláken, můžete objekt uložit do mezipaměti jako objekt singleton nebo statický objekt, takže model načtete jednou.

Pro druhý objekt, `PredictionEngine` objekt, není to tak `PredictionEngine` snadné, protože objekt není bezpečný pro přístup z více vláken, proto nelze vytvořit konkretní tento objekt jako singleton nebo statický objekt v aplikaci ASP.NET Core. Tento problém s bezpečností a škálovatelností pro vlákna je hluboce popsán v tomto [příspěvku blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).

Nicméně, věci dostal mnohem jednodušší pro vás, než to, co je vysvětleno v tomto blogu. Pracovali jsme na jednodušším přístupu pro vás a vytvořili jsme pěkný **'.NET Core Integration Package',** který můžete snadno použít ve vašem ASP.NET základní aplikace a služby tím, že ji zaregistrujete v aplikaci DI služby (služby vkládání závislostí) a pak jej přímo používat z vašeho kódu. Podívejte se na následující kurz a příklad pro to, že:

- [Kurz: Spuštění ML.NET modelů na škálovatelných ASP.NET webových aplikacích Core a webapii](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: Škálovatelný model ML.NET na rozhraní ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Prozkoumejte generovaný kód Jazyka C#, který byl použit k trénování modelu "nejlepší kvality"

Pro pokročilejší účely učení můžete také prozkoumat generovaný kód Jazyka C#, který byl použit nástrojem cli k trénování generovaného modelu.

Tento "kód modelu školení" je aktuálně generován ve `ModelBuilder` vlastní třídě generované s názvem, takže můžete prozkoumat, že kód školení.

Ještě důležitější je, pro tento konkrétní scénář (sentiment analýza modelu) můžete také porovnat, že generované trénovací kód s kódem vysvětleným v následujícím kurzu:

- Porovnat: [Kurz: Použití ML.NET v binárním klasifikačním scénáři analýzy mínění](sentiment-analysis.md).

Je zajímavé porovnat zvolený algoritmus a konfiguraci kanálu v kurzu s kódem generovaným nástrojem CLI. V závislosti na tom, kolik času strávíte iterace a hledání lepších modelů, může být zvolený algoritmus odlišný spolu s jeho konkrétní hyper-parametry a konfigurace kanálu.

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Příprava dat na vybraný úkol ML (problém k vyřešení)
> - Spuštění příkazu "mlnet auto-train" v nástroji rozhraní příkazového příkazu
> - Kontrola výsledků metrik kvality
> - Principy generované ho C# kód pro spuštění modelu (Kód pro použití v aplikaci koncového uživatele)
> - Prozkoumejte generovaný kód Jazyka C#, který byl použit k trénování modelu "nejlepší kvality" (účely učení)

## <a name="see-also"></a>Viz také

- [Automatizace tréninku modelu pomocí ML.NET CLI](../automate-training-with-cli.md)
- [Kurz: Spuštění ML.NET modelů na škálovatelných ASP.NET webových aplikacích Core a webapii](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: Škálovatelný model ML.NET na rozhraní ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET referenční příručka příkazu automatického vlakového ústrojí ML.NET](../reference/ml-net-cli-reference.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
