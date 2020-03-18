---
title: Prozkoumejte kód pomocí syntaxe roslyn v sadě Visualstudio
description: Syntaxe vizualizér poskytuje vizuální nástroj pro zkoumat modely .NET Compiler Platform SDK generuje pro kód.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: 27e5a1f0b31dd2af2ac779223538b03cdb4db0c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156984"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Prozkoumejte kód pomocí syntaxe roslyn v sadě Visualstudio

Tento článek obsahuje přehled nástroje Syntax Visualizer, který je dodáván jako součást platformy SDK .NET Compiler Platform ("Roslyn"). Syntax visualizer je okno nástroje, které vám pomůže zkontrolovat a prozkoumat stromy syntaxe. Je to základní nástroj pro pochopení modelů pro kód, který chcete analyzovat. Je to také ladicí pomůcka při vývoji vlastních aplikací pomocí platformy SDK .NET Compiler Platform ("Roslyn"). Otevřete tento nástroj při vytváření prvních analyzátorů. Vizualizér vám pomůže pochopit modely používané api. Můžete také použít nástroje jako [SharpLab](https://sharplab.io) nebo [LINQPad](https://www.linqpad.net/) ke kontrole kódu a pochopení syntaktických stromů.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Seznamte se s koncepty používanými v sdk platformě kompilátoru .NET načtením článku [přehledu.](compiler-api-model.md) Poskytuje úvod do syntaxe stromy, uzly, tokeny a trivia.

## <a name="syntax-visualizer"></a>Vizualizace syntaxe

**Syntaxvisualizer** umožňuje kontrolu stromu syntaxe pro soubor kódu Jazyka C# nebo Visual Basic v aktuálním okně aktivního editoru uvnitř ide sady Visual Studio. Vizualizér lze spustit kliknutím na **zobrazit** > **další Windows** > **Syntax Visualizer**.  Panel nástrojů **Snadné spuštění** můžete také použít v pravém horním rohu. Zadejte "syntaxe" a měl by se zobrazit příkaz pro otevření **syntaxe Visualizer.**

Tento příkaz otevře syntaxi vizualizéru jako plovoucí nástroj okna. Pokud nemáte otevřené okno editoru kódu, zobrazení je prázdné, jak je znázorněno na následujícím obrázku.

![Okno Nástroje Vizualizátor syntaxe](media/syntax-visualizer/syntax-visualizer.png)

Ukotvit toto okno nástroje na vhodném místě uvnitř sady Visual Studio, například na levé straně. Vizualizér zobrazuje informace o aktuálním souboru kódu.

Vytvořte nový projekt pomocí příkazu **Soubor** > **nového projektu.** Můžete vytvořit projekt jazyka Nebo C#. Když Visual Studio otevře hlavní soubor kódu pro tento projekt, vizualizér zobrazí strom syntaxe pro něj. V této instanci sady Visual Studio můžete otevřít libovolný existující soubor jazyka C# / Visual Basic a vizualizér zobrazí syntaktický strom tohoto souboru. Pokud máte v sadě Visual Studio otevřeno více souborů kódu, zobrazí vizualizér strom syntaxe pro aktuálně aktivní soubor kódu (soubor kódu, který má fokus klávesnice.)

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)
![Vizualizace stromu syntaxe jazyka C#](media/syntax-visualizer/visualize-csharp.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)
![Vizualizace stromu syntaxe jazyka Visual Basic](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak je znázorněno na předchozích obrázcích, okno vizualizéru nástroje zobrazí strom syntaxe v horní části a mřížku vlastností v dolní části. Mřížka vlastností zobrazuje vlastnosti položky, která je aktuálně vybrána ve stromu, včetně *typu* .NET a *druhu* (SyntaxKind) položky.

Syntaxe stromy se skládají ze tří typů položek – *uzly*, *tokeny*a *trivia*. Další informace o těchto typech si můžete přečíst v článku [Práce se syntaxí.](work-with-syntax.md) Položky každého typu jsou reprezentovány jinou barvou. Klikněte na tlačítko "Legenda" pro přehled použitých barev.

Každá položka ve stromu také zobrazuje své vlastní **rozpětí**. **Rozsah** je indexy (počáteční a koncová pozice) tohoto uzlu v textovém souboru.  V předchozím příkladu jazyka C# má vybraný token UsingKeyword [0..5)" **rozsah,** který je široký pět znaků [0..5). Zápis "[..)" znamená, že počáteční index je součástí rozsahu, ale koncový index není.

Strom lze procházet dvěma způsoby:

* Rozbalte nebo klikněte na položky ve stromu. Vizualizér automaticky vybere text odpovídající rozpětí této položky v editoru kódu.
* Klikněte nebo vyberte text v editoru kódu. V předchozím příkladu jazyka, pokud vyberete řádek obsahující "Modul modul1" v editoru kódu, vizualizér automaticky přejde na odpovídající uzel ModuleStatement ve stromu.

Vizualizér zvýrazní položku ve stromu, jejíž rozpětí nejlépe odpovídá rozsahu textu vybraného v editoru.

Vizualizér aktualizuje strom tak, aby odpovídal změnám v aktivním souboru kódu. Přidejte volání `Console.WriteLine()` `Main()`do vnitřku . Při psaní vizualizér aktualizuje strom.

Po zadání příkazu pozastavit zadávání pozadejte `Console.`. Strom má některé položky barevné v růžovébarvě. V tomto okamžiku jsou chyby (označované také jako "Diagnostika") v zadaném kódu. Tyto chyby jsou připojeny k uzlům, tokenům a trivia ve stromu syntaxe. Vizualizér ukazuje, ke kterým položkám jsou připojeny chyby, které zvýrazňují pozadí růžově. Chyby můžete zkontrolovat na libovolné položce, která je růžová, najetím na položku. Vizualizér zobrazuje pouze syntaktické chyby (tyto chyby související se syntaxí zadaného kódu); nezobrazuje žádné sémantické chyby.

## <a name="syntax-graphs"></a>Syntaktické grafy

Klikněte pravým tlačítkem myši na libovolnou položku ve stromu a klikněte na **Zobrazit směrovaný syntaktický graf**.

# <a name="c"></a>[C #](#tab/csharp)

Vizualizér zobrazí grafické znázornění podstromu zakořeněného u vybrané položky. Vyzkoušejte tyto kroky pro uzel **MethodDeclaration** odpovídající metodě `Main()` v příkladu C#. Vizualizér zobrazí graf syntaxe, který vypadá takto:

![Zobrazení grafu syntaxe jazyka C#](media/syntax-visualizer/csharp-syntax-graph.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

Zkuste totéž pro uzel **SubBlock** `Main()` odpovídající metodě v předchozím příkladu jazyka Visual Basic. Vizualizér zobrazí graf syntaxe, který vypadá takto:

![Zobrazení grafu syntaxe jazyka Visual Basic](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Prohlížeč syntaktických grafů má možnost zobrazit legendu jeho barvicí schéma. Můžete také najet myší na jednotlivé položky v grafu syntaxe a zobrazit vlastnosti odpovídající této položce.

Můžete zobrazit syntaktické grafy pro různé položky ve stromu opakovaně a grafy se vždy zobrazí ve stejném okně uvnitř sady Visual Studio. Toto okno můžete ukotvit na vhodném místě v sadě Visual Studio, takže není třeba přepínat mezi kartami, abyste mohli zobrazit nový graf syntaxe. Dole, pod okny editoru kódu, je často pohodlné.

Zde je rozložení ukotvení pro použití s oknem nástroje vizualizéru a oknem grafu syntaxe:

![Jedno rozložení ukotvení pro okno vizualizéru a syntaktického grafu](media/syntax-visualizer/docking-layout.png)

Další možností je umístit okno syntaktického grafu na druhý monitor v nastavení duálního monitoru.

## <a name="inspecting-semantics"></a>Kontrola sémantiky

Syntaxvisualizer umožňuje základní kontrolu symbolů a sémantických informací. Zadejte `double x = 1 + 1;` uvnitř Main() v příkladu C#. Potom vyberte `1 + 1` výraz v okně editoru kódu. Vizualizér zvýrazní uzel **AddExpression** ve vizualizéru. Klikněte pravým tlačítkem myši na tento **AddExpression** a klikněte na **Zobrazit symbol (pokud existuje)**. Všimněte si, že většina položek nabídky má kvalifikátor "pokud existuje". Syntaxvisualizer kontroluje vlastnosti uzlu, včetně vlastností, které nemusí být k dispozici pro všechny uzly.

Mřížka vlastností v vizualizéru se aktualizuje, jak je znázorněno na následujícím obrázku: Symbol výrazu je **SynthesizedIntrinsicOperatorSymbol** s **Kind = Method**.

![Vlastnosti symbolu](media/syntax-visualizer/symbol-properties.png)

Zkuste **Zobrazit TypeSymbol (pokud existuje)** pro stejný uzel **AddExpression.** Mřížka vlastností v vizualizéru se aktualizuje, jak je znázorněno `Int32`na následujícím obrázku, což znamená, že typ vybraného výrazu je .

![Vlastnosti TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Zkuste **zobrazit převedený typesymbol (pokud existuje)** pro stejný uzel **AddExpression.** Mřížka vlastností se aktualizuje, což znamená, že i když `Int32`je `Double` typ výrazu , převedený typ výrazu je znázorněn tak, jak je znázorněno na následujícím obrázku. Tento uzel obsahuje informace o převedeném symbolu typu, `Int32` protože výraz se `Double`vyskytuje v kontextu, ve kterém musí být převeden na . Tento převod splňuje `Double` typ zadaný `x` pro proměnnou na levé straně operátoru přiřazení.

![Převedené vlastnosti TypeSymbol](media/syntax-visualizer/converted-type-symbol-properties.png)

Nakonec zkuste **Zobrazit konstantní hodnotu (pokud existuje)** pro stejný uzel **AddExpression.** Mřížka vlastností ukazuje, že hodnota výrazu je `2`časová konstanta kompilace s hodnotou .

![Konstantní hodnota](media/syntax-visualizer/constant-value.png)

Předchozí příklad lze také replikovat v jazyce Visual Basic. Zadejte `Dim x As Double = 1 + 1` soubor jazyka Visual Basic. Vyberte `1 + 1` výraz v okně editoru kódu. Vizualizér zvýrazní odpovídající uzel **AddExpression** v vizualizéru. Opakujte předchozí kroky pro tento **AddExpression** a měli byste vidět identické výsledky.

Prozkoumejte další kód v jazyce Visual Basic. Aktualizujte hlavní soubor jazyka Visual Basic pomocí následujícího kódu:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Tento kód zavádí alias `C` s názvem, `System.Console` který se mapuje na typ `Main()`v horní části souboru a používá tento alias uvnitř . Vyberte použití tohoto aliasu, `C` in `Main()` `C.WriteLine()`, uvnitř metody. Vizualizér vybere odpovídající **uzel IdentifierName** v vizualizéru. Klepněte pravým tlačítkem myši na tento uzel a klikněte na **zobrazit symbol (pokud existuje)**. Mřížka vlastností označuje, že tento `System.Console` identifikátor je vázán na typ, jak je znázorněno na následujícím obrázku:

![Vlastnosti symbolu](media/syntax-visualizer/symbol-visual-basic.png)

Zkuste **zobrazit aliassymbol (pokud existuje)** pro stejný uzel **IdentifierName.** Mřížka vlastností označuje, že `C` identifikátor je alias `System.Console` s názvem, který je vázán na cíl. Jinými slovy, mřížka vlastností poskytuje informace týkající `C`se **AliasSymbol** odpovídající identifikátor .

![AliasSymbol, vlastnosti](media/syntax-visualizer/alias-symbol.png)

Zkontrolujte symbol odpovídající jakémukoli deklarovanému typu, metodě, vlastnosti. Vyberte odpovídající uzel ve vizualizéru a klikněte na **Zobrazit symbol (pokud existuje)**. Vyberte `Sub Main()`metodu , včetně těla metody. Klikněte na **Zobrazit symbol (pokud existuje)** pro odpovídající uzel **SubBlock** v vizualizéru. Mřížka vlastností zobrazuje **MethodSymbol** pro `Main` tento **SubBlock** má název s návratovým typem `Void`.

![Zobrazení symbolu pro deklaraci metody](media/syntax-visualizer/method-symbol.png)

Výše uvedené příklady jazyka lze snadno replikovat v jazyce C#. Místo `using C = System.Console;` aliasu `Imports C = System.Console` zadejte. Předchozí kroky v jazyce C# poskytují identické výsledky v okně vizualizéru.

Sémantické kontrolní operace jsou k dispozici pouze na uzlech. Nejsou k dispozici na žetonech nebo trivia. Ne všechny uzly mají zajímavé sémantické informace ke kontrole. Pokud uzel nemá zajímavé sémantické informace, kliknutím na **zobrazit \* symbol (pokud existuje)** zobrazí prázdnou mřížku vlastností.

Další informace o řešení API pro provádění sémantické analýzy najdete v dokumentu [Přehled práce s sémantikou.](work-with-semantics.md)

## <a name="closing-the-syntax-visualizer"></a>Zavření vizualizéru syntaxe

Okno vizualizéru můžete zavřít, pokud ho nepoužíváte ke kontrole zdrojového kódu. Syntaxe vizualizér aktualizuje jeho zobrazení při procházení kódu, úpravy a změny zdroje. To může dostat rušivé, když ji nepoužíváte.
