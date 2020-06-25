---
title: Analýza mínění pomocí rozhraní příkazového řádku ML.NET
description: Automaticky generovat model ML a související kód v jazyce C# z ukázkové datové sady
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: fcd325d518b276ccb042f3702db978e9189715b8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326029"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>Analýza mínění pomocí rozhraní příkazového řádku ML.NET

Naučte se používat rozhraní příkazového řádku ML.NET k automatickému generování modelu ML.NET a základního kódu jazyka C#. Zadáte datovou sadu a úlohu strojového učení, kterou chcete implementovat, a rozhraní příkazového řádku používá modul AutoML k vytvoření generování modelu a zdrojového kódu nasazení a také klasifikační model.

V tomto kurzu provedete následující kroky:
> [!div class="checklist"]
>
> - Příprava dat pro vybraný úkol strojového učení
> - Spuštění příkazu "mlnet Classification" z rozhraní příkazového řádku
> - Kontrola výsledků metrik kvality
> - Pochopení generovaného kódu jazyka C# pro použití modelu ve vaší aplikaci
> - Prozkoumat generovaný kód C#, který se použil ke výukě modelu

> [!NOTE]
> Toto téma odkazuje na nástroj CLI ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn. Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

ML.NET CLI je součástí ML.NET a jeho hlavním cílem je "Demokratizujte" ML.NET pro vývojáře na platformě .NET při učení ML.NET, takže nemusíte vytvářet kód od začátku, abyste mohli začít.

ML.NET CLI můžete spustit na jakémkoli příkazovém řádku (Windows, Mac nebo Linux) a vygenerovat dobré kvality ML.NET modely a zdrojový kód na základě školení datových sad, které poskytnete.

## <a name="pre-requisites"></a>Požadavky

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) nebo novější
- Volitelné [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)
- [Rozhraní příkazového řádku ML.NET](../how-to-guides/install-ml-net-cli.md)

Můžete buď spustit vygenerované projekty kódu C# ze sady Visual Studio nebo pomocí `dotnet run` (.NET Core CLI).

## <a name="prepare-your-data"></a>Příprava dat

Použijeme existující datovou sadu, která se používá pro scénář Analýza mínění, což je úloha strojového učení s binární klasifikací. Můžete použít vlastní datovou sadu podobným způsobem a model a kód budou vygenerovány za vás.

1. Stáhněte [soubor zip datové sady mínění s popiskem "UCI" (viz citace v následující poznámce)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho do libovolné složky, kterou zvolíte.

    > [!NOTE]
    > Tento kurz používá datovou sadu ze skupiny "od" až po jednotlivé štítky pomocí hlubokých funkcí, Kotzias et al,. KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017). UCI Machine Learning úložiště [ http://archive.ics.uci.edu/ml ]. Irvine, CA: University of California, školní informace a počítačové vědy.

2. Zkopírujte `yelp_labelled.txt` soubor do složky, kterou jste dříve vytvořili (například `/cli-test` ).

3. Otevřete preferovaný příkazový řádek a přejděte do složky, do které jste zkopírovali soubor DataSet. Příklad:

    ```console
    cd /cli-test
    ```

    Pomocí libovolného textového editoru, jako je Visual Studio Code, můžete otevřít a prozkoumat `yelp_labelled.txt` soubor DataSet. Můžete vidět, že struktura je:

    - Soubor nemá žádnou hlavičku. Budete používat index sloupce.

    - K dispozici jsou pouze dva sloupce:

        | Text (index sloupce 0) | Popisek (index sloupce 1)|
        |--------------------------|-------|
        | Wow... Tohle místo. | 1 |
        | Crust není dobrá. | 0 |
        | Není Tasty a textura byla pouze nepříjemný. | 0 |
        | ... MNOHO DALŠÍCH TEXTOVÝCH ŘÁDKŮ... | ... (1 nebo 0)... |

    Ujistěte se, že jste zavřeli soubor datové sady z editoru.

    Nyní jste připraveni začít používat rozhraní příkazového řádku pro tento scénář Analýza mínění.

    > [!NOTE]
    > Po dokončení tohoto kurzu můžete také vyzkoušet vlastní datové sady, pokud jsou připravené k použití pro všechny úlohy ML aktuálně podporované ve verzi ML.NET CLI Preview, které jsou *binární klasifikace, klasifikace, regrese* a *doporučení*.

## <a name="run-the-mlnet-classification-command"></a>Spuštění příkazu "mlnet Classification"

1. Spusťte následující příkaz ML.NET CLI:

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    Tento příkaz spustí ** `mlnet classification` příkaz**:
    - pro **úlohu klasifikace ml** *klasifikace*
    - používá **soubor `yelp_labelled.txt` DataSet** jako školicí a testovací datovou sadu (interně rozhraní příkazového řádku použije křížové ověření nebo ho rozdělí ve dvou datových sadách, jeden pro školení a jeden pro testování).
    - kde **sloupec cíl/cíl** , který chcete odhadnout (obvykle se nazývá **"label"**), je **sloupec s indexem 1** (to je druhý sloupec, protože index je založený na nule).
    - **nepoužívá záhlaví souboru** s názvy sloupců, protože tento konkrétní soubor DataSet nemá hlavičku.
    - **Cílová doba průzkumu a výuky** pro experiment je **10 sekund** .

    Zobrazí se výstup z rozhraní příkazového řádku, podobně jako:

    ![Klasifikace rozhraní příkazového řádku ML.NET v prostředí PowerShell](./media/mlnet-cli/mlnet-classification-powershell.gif)

    V tomto konkrétním případě, během 10 sekund a s malou datovou sadou, mohl nástroj rozhraní příkazového řádku spustit poměrně několik iterací, což znamená, že se bude na základě různých kombinací algoritmů a konfigurací s různými interními transformacemi dat a možnostmi Hyper-v algoritmu použít více než jednou.

    Nakonec model "nejlepší kvality" nalezený za 10 sekund představuje model používající konkrétní Trainer nebo algoritmus s jakoukoli konkrétní konfigurací. V závislosti na době průzkumu může příkaz vytvořit jiný výsledek. Výběr je založen na několika zobrazených metrikách, například `Accuracy` .

    **Princip metrik kvality modelu**

    První a nejjednodušší metrika pro vyhodnocení modelu binární klasifikace je přesnost, která je snadno srozumitelná. "Přesnost je poměrem správných předpovědi se sadou testovacích dat.". Lépe až 100% (1,00), tím lépe.

    Nicméně existují případy, kdy měření se metrikou přesnosti není dostatečné, zejména v případě, že je popisek (0 a 1 v tomto případě) v testovací datové sadě nevyvážený.

    Další metriky a **podrobnější informace o metrikách** , jako je přesnost, AUC, AUCPR a F1 – skóre, které slouží k vyhodnocení různých modelů, najdete v tématu [Principy metrik ml.NET](../resources/metrics.md).

    > [!NOTE]
    > Můžete vyzkoušet tuto velmi stejnou datovou sadu a zadat několik minut `--max-exploration-time` (například tři minuty, takže zadáte 180 sekund), což vám pro tuto datovou sadu vyhledá lepší "nejlepší model", a to s jinou konfigurací školicího kanálu (což je poměrně malé, 1000 řádků).

    Aby bylo možné najít model "nejlepší/dobrý kvalita", který je "modelem připraveným pro produkční prostředí", který cílí na větší datové sady, měli byste experimenty s rozhraním příkazového řádku obvykle určit mnohem více času průzkumu v závislosti na velikosti datové sady. V mnoha případech se může stát, že budete potřebovat více hodin doby průzkumu, zejména pokud je datová sada velká na řádcích a sloupcích.

1. Předchozí spuštění příkazu vygenerovalo následující prostředky:

    - Serializovaný model. zip ("nejlepší model") je připravený k použití.
    - Kód jazyka C# ke spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).
    - Kód školení C# používaný k vygenerování tohoto modelu (Learning).
    - Soubor protokolu se všemi iteracemi, které se prozkoumaly s konkrétními podrobnějšími informacemi o každém algoritmu, se snaží s jeho kombinací Hyper-Parameters a transformaci dat.

    První dva prostředky (. Model souborů ZIP a kód C# ke spuštění tohoto modelu) je možné přímo použít v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.), aby se předpovědi s tímto generovaným modelem ML.

    Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat, jaké konkrétní Trainer/algoritmus a Hyper-Parameters byly vybrány rozhraním příkazového řádku.

Tyto vyčíslované prostředky jsou vysvětleny v následujících krocích kurzu.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Prozkoumejte generovaný kód C#, který se použije ke spuštění modelu pro předpovědi.

1. V sadě Visual Studio (2017 nebo 2019) otevřete řešení vygenerované ve složce s názvem v `SampleClassification` původní cílové složce (v tomto kurzu se jmenovalo `/cli-test` ). Mělo by se zobrazit podobné řešení:

    > [!NOTE]
    > V tomto kurzu doporučujeme používat Visual Studio, ale můžete také prozkoumat generovaný kód C# (dva projekty) pomocí libovolného textového editoru a spustit aplikaci generovanou konzolou s použitím `dotnet CLI` počítače s MacOS, Linux nebo Windows.

    ![Řešení VS vygenerované rozhraním CLI](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - Vygenerovaná **Knihovna tříd** obsahující serializovaný model ml (soubor. zip) a datové třídy (datové modely) je něco, co můžete přímo použít v aplikaci koncového uživatele, a to i přímo odkazování na tuto knihovnu tříd (nebo přesunutí kódu, jak dáváte přednost).
    - Vygenerovaná **aplikace konzoly** obsahuje kód spuštění, který je nutné zkontrolovat, a pak obvykle znovu použijete "hodnoticí kód" (kód, který SPUSTÍ model ml, aby předpovědi) přesunutím tohoto jednoduchého kódu (pouze pár řádků) do aplikace koncového uživatele, kde chcete vytvořit předpovědi.

1. V projektu knihovny tříd otevřete soubory třídy **ModelInput.cs** a **ModelOutput.cs** . Uvidíte, že tyto třídy jsou "datové třídy" nebo třídy POCO používané k ukládání dat. Je to "často používaný kód", ale užitečný pro jeho vygenerování, pokud má vaše datová sada desítky nebo dokonce stovky sloupců.
    - `ModelInput`Třída se používá při čtení dat z datové sady.
    - `ModelOutput`Třída slouží k získání výsledku předpovědi (data předpovědi).

1. Otevřete soubor Program.cs a prozkoumejte kód. V několika řádcích je možné spustit model a vytvořit ukázku předpovědi.

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - První řádky kódu vytvářejí *Jednoduchá ukázková data*, v tomto případě na základě prvního řádku datové sady, která se má použít pro předpověď. Můžete také vytvořit vlastní "pevně zakódované" data aktualizací kódu:

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - Další řádek kódu používá `ConsumeModel.Predict()` metodu pro zadaná vstupní data k vytvoření předpovědi a vrácení výsledků (na základě schématu ModelOutput.cs).
    - Poslední řádky kódu tisknou vlastnosti vzorových dat (v tomto případě komentář) i předpověď mínění a odpovídající skóre pro kladné mínění (1) a záporné mínění (2).

1. Spusťte projekt, a to buď pomocí původních ukázkových dat načtených z prvního řádku datové sady, nebo poskytnutím vlastních pevně zakódovaných ukázkových dat. Měli byste dosáhnout předpovědi srovnatelné s:

![ML.NET CLI spustí aplikaci ze sady Visual Studio.](./media/mlnet-cli/mlnet-cli-console-app.png))

1. Zkuste změnit pevně kódovaná ukázková data na jiné věty s různými mínění a podívejte se, jak model předpovídá kladné nebo záporné mínění.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Inpředpovědiování aplikací pro koncové uživatele pomocí ML modelu ML

Podobný kód pro vyhodnocování modelu ML můžete použít ke spuštění modelu v aplikaci koncového uživatele a k vytvoření předpovědi.

Tento kód můžete například přímo přesunout do libovolné aplikace klasické pracovní plochy systému Windows, jako je například **WPF** a **WinForms** , a model spustit stejným způsobem, než byl proveden v konzolové aplikaci.

Způsob, jakým implementujete tyto řádky kódu ke spuštění modelu ML, by se měl optimalizovat (to znamená ukládat do mezipaměti soubor. zip modelu a načíst ho jednou) a mít objekty singleton místo jejich vytváření na všech žádostech, zejména v případě, že vaše aplikace musí být škálovatelná, jako je webová aplikace nebo distribuovaná služba, jak je vysvětleno v následující části.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Spouštění modelů ML.NET v škálovatelných ASP.NET Core webových aplikacích a službách (vícevláknové aplikace)

Vytvoření objektu modelu ( `ITransformer` načteného ze souboru. zip modelu) a `PredictionEngine` objektu by mělo být optimalizované hlavně při spuštění na škálovatelných webových aplikacích a distribuovaných službách. V první případě je objekt modelu ( `ITransformer` ) optimalizace jednoduchá. Vzhledem k `ITransformer` tomu, že je objekt bezpečný pro přístup z více vláken, můžete objekt uložit do mezipaměti jako typ singleton nebo static, abyste model načetli pouze jednou.

U druhého objektu `PredictionEngine` objekt není tak snadné, protože objekt není bezpečný pro přístup z `PredictionEngine` více vláken, proto nemůžete vytvořit instanci tohoto objektu jako typ singleton nebo statický objekt v aplikaci ASP.NET Core. Tento problémový příspěvek k vláknům a škálovatelnosti je v tomto [blogovém příspěvku](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)podrobněji popsán.

Věcí vám ale bylo mnohem jednodušší, než je vysvětleno v tomto blogovém příspěvku. Pracovali jsme na jednodušším přístupu a vytvořili jste dobrý **balíček integrace .NET Core** , který můžete snadno použít ve svých ASP.NET Corech aplikacích a službách, a to tak, že ho zaregistrujete ve službě Application di Services (služba pro vkládání závislostí) a pak ho přímo použijete z vašeho kódu. Podívejte se na následující kurz a příklad, jak to provést:

- [Kurz: používání modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: škálovatelný ML.NET model na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Prozkoumejte vygenerovaný kód C#, který se použil ke vzdělávání modelu nejlepší kvality.

Pro pokročilejší účely učení můžete také prozkoumat generovaný kód C#, který byl použit nástrojem CLI k výuce vygenerovaného modelu.

Tento kód školicího modelu je aktuálně vygenerován ve vlastní třídě generované s názvem, `ModelBuilder` abyste mohli prozkoumat tento školicí kód.

Důležitější je, že pro tento konkrétní scénář (Analýza mínění model) můžete také porovnat vygenerovaný školicí kód s kódem, který je vysvětlen v následujícím kurzu:

- Porovnání: [kurz: použití ml.NET v binárním scénáři klasifikace mínění Analysis](sentiment-analysis.md).

Je zajímavá možnost porovnat zvolený algoritmus a konfiguraci kanálu v kurzu s kódem generovaným nástrojem CLI. V závislosti na tom, kolik času strávíte iterací a hledáním lepších modelů, se zvolený algoritmus může lišit spolu s jeho konkrétními parametry Hyper-a a konfigurací kanálu.

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Příprava dat pro vybraný úkol ML (problém, který se má vyřešit)
> - Spuštění příkazu "mlnet Classification" v nástroji CLI
> - Kontrola výsledků metrik kvality
> - Pochopení generovaného kódu C# ke spuštění modelu (kód pro použití v aplikaci koncového uživatele)
> - Prozkoumejte vygenerovaný kód C#, který se použil ke vzdělávání modelu nejlepší kvality (k tomuto využití).

## <a name="see-also"></a>Viz také

- [Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Kurz: používání modelů ML.NET na škálovatelných ASP.NET Core Web Apps a rozhraní WebApi](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Ukázka: škálovatelný ML.NET model na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [Referenční příručka k příkazu ML.NET CLI pro automatické učení](../reference/ml-net-cli-reference.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
