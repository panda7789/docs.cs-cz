---
title: Analýza mínění pomocí rozhraní příkazového řádku ML.NET
description: Automatické generování modelu ML a souvisejícího C# kódu z ukázkové datové sady
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 5b3b0af5b46774beff9fb7a2a86c37e5399c0dd2
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957394"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>Analýza mínění pomocí rozhraní příkazového řádku ML.NET

Naučte se používat rozhraní příkazového řádku ML.NET k automatickému generování modelu C# ml.NET a základního kódu. Zadáte datovou sadu a úlohu strojového učení, kterou chcete implementovat, a rozhraní příkazového řádku používá modul AutoML k vytvoření generování modelu a zdrojového kódu nasazení a také binárního modelu.

V tomto kurzu provedete následující kroky:
> [!div class="checklist"]
>
> - Příprava dat pro vybraný úkol strojového učení
> - Spuštění příkazu ' mlnet auto-vlak ' z rozhraní příkazového řádku
> - Kontrola výsledků metrik kvality
> - Pochopení vygenerovaného C# kódu pro použití modelu ve vaší aplikaci
> - Prozkoumejte vygenerovaný C# kód, který se použil pro výuku modelu.

> [!NOTE]
> Toto téma odkazuje na nástroj CLI ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn. Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

ML.NET CLI je součástí ML.NET a jeho hlavním cílem je "Demokratizujte" ML.NET pro vývojáře na platformě .NET při učení ML.NET, takže nemusíte vytvářet kód od začátku, abyste mohli začít.

ML.NET CLI můžete spustit na jakémkoli příkazovém řádku (Windows, Mac nebo Linux) a vygenerovat dobré kvality ML.NET modely a zdrojový kód na základě školení datových sad, které poskytnete.

## <a name="pre-requisites"></a>Předpoklady

- [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo novější
- Volitelné [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)
- [ML.NET CLI](../how-to-guides/install-ml-net-cli.md)

Můžete buď spustit vygenerované C# projekty kódu ze sady Visual Studio nebo pomocí `dotnet run` (.NET Core CLI).

## <a name="prepare-your-data"></a>Příprava dat

Použijeme existující datovou sadu, která se používá pro scénář Analýza mínění, což je úloha strojového učení s binární klasifikací. Můžete použít vlastní datovou sadu podobným způsobem a model a kód budou vygenerovány za vás.

1. Stáhněte [soubor zip datové sady mínění s popiskem "UCI" (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho do libovolné složky, kterou zvolíte.

    > [!NOTE]
    > Tento kurz používá datovou sadu ze skupiny "od" až po jednotlivé štítky pomocí hlubokých funkcí, Kotzias et al,. KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017). UCI Machine Learning úložiště [http://archive.ics.uci.edu/ml ]. Irvine, CA: University of California, školní informace a počítačové vědy.

2. Zkopírujte soubor `yelp_labelled.txt` do jakékoli složky, kterou jste dříve vytvořili (například `/cli-test`).

3. Otevřete preferovaný příkazový řádek a přejděte do složky, do které jste zkopírovali soubor DataSet. Příklad:

    ```console
    > cd /cli-test
    ```

    Pomocí libovolného textového editoru, jako je například Visual Studio Code, můžete otevřít a prozkoumat soubor DataSet `yelp_labelled.txt`. Můžete vidět, že struktura je:

    - Soubor nemá žádnou hlavičku. Budete používat index sloupce.

    - K dispozici jsou pouze dva sloupce:

        | Text (index sloupce 0) | Popisek (index sloupce 1)|
        |--------------------------|-------|
        | Wow... Tohle místo. | první |
        | Crust není dobrá. | 0,8 |
        | Není Tasty a textura byla pouze nepříjemný. | 0,8 |
        | ... MNOHO DALŠÍCH TEXTOVÝCH ŘÁDKŮ... | ... (1 nebo 0)... |

    Ujistěte se, že jste zavřeli soubor datové sady z editoru.

    Nyní jste připraveni začít používat rozhraní příkazového řádku pro tento scénář Analýza mínění.

    > [!NOTE]
    > Po dokončení tohoto kurzu můžete také vyzkoušet vlastní datové sady, pokud jsou připravené k použití pro všechny úlohy ML aktuálně podporované ve verzi ML.NET CLI Preview, které jsou *binární klasifikace, klasifikace s více třídami a regrese.* ).

## <a name="run-the-mlnet-auto-train-command"></a>Spuštění příkazu ' mlnet auto-vlak '

1. Spusťte následující příkaz ML.NET CLI:

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Tento příkaz spustí **příkaz `mlnet auto-train`** :
    - pro **úlohu typu ml** typu **`binary-classification`**
    - používá **soubor dataset `yelp_labelled.txt`** jako školicí a testovací datovou sadu (interně rozhraní PŘÍKAZového řádku použije křížové ověření nebo ho rozdělí ve dvou datových sadách, jeden pro školení a jeden pro testování).
    - kde **sloupec cíl/cíl** , který chcete odhadnout (obvykle se nazývá **"label"** ), je **sloupec s indexem 1** (to je druhý sloupec, protože index je založený na nule).
    - **nepoužívá záhlaví souboru** s názvy sloupců, protože tento konkrétní soubor DataSet nemá hlavičku.
    - **cílený čas průzkumu** experimentu je **10 sekund** .

    Zobrazí se výstup z rozhraní příkazového řádku, podobně jako:

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[macOS bash](#tab/macosbash)

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    V tomto konkrétním případě, během pouhých 10 sekund a s malou datovou sadou, mohl nástroj rozhraní příkazového řádku spustit poměrně několik iterací, což znamená, že se bude na základě různých kombinací algoritmů a konfigurací s různými interními daty podařit školení několikrát. transformace a Hyper-parametry algoritmu. 

    Nakonec model "nejlepší kvality" nalezený za 10 sekund představuje model používající konkrétní Trainer nebo algoritmus s jakoukoli konkrétní konfigurací. V závislosti na době průzkumu může příkaz vytvořit jiný výsledek. Výběr je založen na několika zobrazených metrikách, například `Accuracy`.

    **Princip metrik kvality modelu**

    První a nejjednodušší metrika pro vyhodnocení modelu binární klasifikace je přesnost, která je snadno srozumitelná. "Přesnost je poměrem správných předpovědi se sadou testovacích dat.". Lépe až 100% (1,00), tím lépe.

    Nicméně existují případy, kdy měření se metrikou přesnosti není dostatečné, zejména v případě, že je popisek (0 a 1 v tomto případě) v testovací datové sadě nevyvážený.

    Další metriky a **podrobnější informace o metrikách** , jako je přesnost, AUC, AUCPR, F1-skore využívané k vyhodnocení různých modelů, si můžete přečíst v tématu [Principy metrik ml.NET](../resources/metrics.md) .

    > [!NOTE]
    > Můžete vyzkoušet tuto velmi stejnou datovou sadu a zadat pár minut pro `--max-exploration-time` (například pro tři minuty zadejte hodnotu 180 sekund), která vám pro tuto datovou sadu vyhledá lepší "nejlepší model", a to s jinou konfigurací školicího kanálu (což je poměrně malá , 1000 řádků). 
        
    Aby bylo možné najít model "nejlepší/dobrý kvalita", který je "modelem připraveným pro produkční prostředí", který cílí na větší datové sady, měli byste experimenty s rozhraním příkazového řádku obvykle určit mnohem více času průzkumu v závislosti na velikosti datové sady. V mnoha případech se může stát, že budete potřebovat více hodin doby průzkumu, zejména pokud je datová sada velká na řádcích a sloupcích. 

1. Předchozí spuštění příkazu vygenerovalo následující prostředky:

    - Serializovaný model. zip ("nejlepší model") je připravený k použití. 
    - C#kód pro spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).
    - C#školicí kód používaný k vygenerování tohoto modelu (výukové účely)
    - Soubor protokolu se všemi iteracemi, které se prozkoumaly s konkrétními podrobnějšími informacemi o každém algoritmu, se snaží s jeho kombinací Hyper-Parameters a transformaci dat. 

    První dva prostředky (. Model souboru ZIP a C# kód pro spuštění tohoto modelu) je možné přímo použít v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.), aby se předpovědi s tímto generovaným modelem ml.

    Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat, jaké konkrétní Trainer/algoritmus a Hyper-Parameters byly vybrány rozhraním příkazového řádku.

Tyto vyčíslované prostředky jsou vysvětleny v následujících krocích kurzu.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Prozkoumejte generovaný C# kód, který se použije ke spuštění modelu pro předpovědi.

1. V sadě Visual Studio (2017 nebo 2019) otevřete řešení vygenerované ve složce s názvem `SampleBinaryClassification` v původní cílové složce (v tomto kurzu se jmenovala `/cli-test`). Mělo by se zobrazit podobné řešení:

    > [!NOTE]
    > V tomto kurzu doporučujeme používat Visual Studio, ale můžete také prozkoumat vygenerovaný C# kód (dva projekty) pomocí libovolného textového editoru a spustit vygenerovanou aplikaci konzoly s `dotnet CLI` na počítači s MacOS, Linux nebo Windows.

    ![Řešení VS vygenerované rozhraním CLI](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Vygenerovaná **Knihovna tříd** obsahující serializovaný model ml (soubor. zip) a datové třídy (datové modely) je něco, co můžete přímo použít v aplikaci koncového uživatele, a to i přímo odkazování na tuto knihovnu tříd (nebo přesunutí kódu, jak dáváte přednost ).
    - Vygenerovaná **aplikace konzoly** obsahuje kód spuštění, který je nutné zkontrolovat, a pak obvykle znovu použijete "kód bodování" (kód, který SPUSTÍ model ml, aby předpovědi) přesunutím tohoto jednoduchého kódu (pouze pár řádků) do aplikace koncového uživatele, kde chcete Nastavte předpovědi. 

1. V projektu knihovny tříd otevřete soubory třídy **ModelInput.cs** a **ModelOutput.cs** . Uvidíte, že tyto třídy jsou "datové třídy" nebo třídy POCO používané k ukládání dat. Je to "často používaný kód", ale užitečný pro jeho vygenerování, pokud má vaše datová sada desítky nebo dokonce stovky sloupců. 
    - Třída `ModelInput` se používá při čtení dat z datové sady. 
    - Třída `ModelOutput` slouží k získání výsledku předpovědi (data předpovědi).

1. Otevřete soubor Program.cs a prozkoumejte kód. V několika řádcích je možné spustit model a vytvořit ukázku předpovědi.

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

- První řádek kódu jednoduše vytvoří objekt `MLContext` potřebný při každém spuštění kódu ML.NET. 

- Druhý řádek kódu je komentovaný, protože model nepotřebujete vyškolit, protože už ho pro vás vyškole nástroj CLI a uložil se do serializovaného modelu. Soubor ZIP. Pokud ale chcete vidět, *jak byl model vyškolený* rozhraním příkazového řádku, můžete tento řádek odkomentovat a spustit/ladit školicí kód, který se používá pro konkrétní model ml.

- Ve třetím řádku kódu načtete model z serializovaného modelu. Soubor ZIP s rozhraním API `mlContext.Model.Load()` zadáním cesty k tomuto modelu. Soubor ZIP.

- Ve čtvrtém řádku kódu, který načtete, vytvořte objekt `PredictionEngine` s rozhraním API `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)`. Objekt `PredictionEngine` budete potřebovat vždy, když chcete vytvořit předpověď, která cílí na jeden vzorek dat (v tomto případě jediného textu, který předpovídá své mínění).

- Pátý řádek kódu je místo, kde vytvoříte tato *jediná ukázková data* , která se mají použít pro předpověď voláním funkce `CreateSingleDataSample()`. Vzhledem k tomu, že nástroj rozhraní příkazového řádku neví, jaký druh dat použít, v rámci této funkce načítá první řádek datové sady. Nicméně v tomto případě můžete také vytvořit vlastní "pevně kódovaná" data namísto aktuální implementace funkce `CreateSingleDataSample()`, a to tak, že aktualizujete tento jednodušší kód implementující tuto funkci:

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. Spusťte projekt, a to buď pomocí původních ukázkových dat načtených z prvního řádku datové sady, nebo poskytnutím vlastních pevně zakódovaných ukázkových dat. Měli byste dosáhnout předpovědi srovnatelné s:

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    Spusťte konzolovou aplikaci ze sady Visual Studio tak, že kliknete na F5 (tlačítko Přehrát):

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[macOS bash](#tab/macosbash)

    Spusťte konzolovou aplikaci z příkazového řádku zadáním následujících příkazů:

     ```bash
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![ML.NET CLI auto-vlak v PowerShellu](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Zkuste změnit pevně kódovaná ukázková data na jiné věty s různými mínění a podívejte se, jak model předpovídá kladné nebo záporné mínění. 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Inpředpovědiování aplikací pro koncové uživatele pomocí ML modelu ML

Podobný kód pro vyhodnocování modelu ML můžete použít ke spuštění modelu v aplikaci koncového uživatele a k vytvoření předpovědi. 

Tento kód můžete například přímo přesunout do libovolné aplikace klasické pracovní plochy systému Windows, jako je například **WPF** a **WinForms** , a model spustit stejným způsobem, než byl proveden v konzolové aplikaci.

Způsob, jakým implementujete tyto řádky kódu ke spuštění modelu ML, by se měl optimalizovat (to znamená, uložit soubor. zip modelu do mezipaměti a načíst ho jednou) a mít objekty singleton místo jejich vytváření na všech žádostech, zvlášť pokud vaše aplikace musí být škálovatelná, třeba Webová aplikace nebo distribuovaná služba, jak je vysvětleno v následující části.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Spouštění modelů ML.NET v škálovatelných ASP.NET Core webových aplikacích a službách (vícevláknové aplikace)

Vytvoření objektu modelu (`ITransformer` načtené ze souboru. zip modelu) a objekt `PredictionEngine` by měl být optimalizovaný, zejména při spuštění na škálovatelných webových aplikacích a distribuovaných službách. Pro první případ je objekt modelu (`ITransformer`) optimalizace jednoduchá. Vzhledem k tomu, že objekt `ITransformer` je bezpečný pro přístup z více vláken, lze objekt uložit do mezipaměti jako typ singleton nebo static, aby bylo možné model načíst jednou.

U druhého objektu objekt `PredictionEngine` není tak snadné, protože objekt `PredictionEngine` není bezpečný pro přístup z více vláken, proto nemůžete vytvořit instanci tohoto objektu jako typ singleton nebo statický objekt v aplikaci ASP.NET Core. Tento problémový příspěvek k vláknům a škálovatelnosti je v tomto [blogovém příspěvku](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)podrobněji popsán. 

Věcí vám ale bylo mnohem jednodušší, než je vysvětleno v tomto blogovém příspěvku. Pracovali jsme na jednodušším přístupu a vytvořili jste dobrý **balíček integrace .NET Core** , který můžete snadno použít ve svých ASP.NET Corech aplikacích a službách, a to tak, že ho zaregistrujete ve službě Application di Services (služba pro vkládání závislostí) a pak přímo použijte ho z kódu. Podívejte se na následující kurz a příklad, jak to provést:

- [Kurz: používání modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: škálovatelný ML.NET model na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Prozkoumejte vygenerovaný C# kód, který se použil ke vzdělávání modelu "nejlepší kvality". 

Pro pokročilejší účely učení můžete také prozkoumat generovaný C# kód, který byl použit nástrojem CLI k výuce vygenerovaného modelu.

Tento kód modelu školení se aktuálně generuje ve vlastní třídě vygenerované s názvem `ModelBuilder`, takže můžete tento školicí kód prozkoumat.

Důležitější je, že pro tento konkrétní scénář (Analýza mínění model) můžete také porovnat vygenerovaný školicí kód s kódem, který je vysvětlen v následujícím kurzu:

- Porovnání: [kurz: použití ml.NET v binárním scénáři klasifikace mínění Analysis](sentiment-analysis.md).

Je zajímavá možnost porovnat zvolený algoritmus a konfiguraci kanálu v kurzu s kódem generovaným nástrojem CLI. V závislosti na tom, kolik času strávíte iterací a hledáním lepších modelů, se zvolený algoritmus může lišit spolu s jeho konkrétními parametry Hyper-a a konfigurací kanálu.

## <a name="see-also"></a>Viz také:

- [Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Kurz: používání modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: škálovatelný ML.NET model na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [Referenční příručka k příkazu ML.NET CLI pro automatické učení](../reference/ml-net-cli-reference.md) 
- [Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)](../how-to-guides/install-ml-net-cli.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak:
> [!div class="checklist"]
>
> - Příprava dat pro vybraný úkol ML (problém, který se má vyřešit)
> - Spuštění příkazu ' mlnet auto-vlak ' v nástroji CLI
> - Kontrola výsledků metrik kvality
> - Pochopení generovaného C# kódu pro spuštění modelu (kód pro použití v aplikaci koncového uživatele)
> - Prozkoumejte vygenerovaný C# kód, který se použil ke studiu "nejlepší kvality" modelu (vzdělávací účely).

> [!div class="nextstepaction"]
> [Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
