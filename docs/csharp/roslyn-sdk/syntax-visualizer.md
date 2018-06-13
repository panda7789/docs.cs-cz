---
title: Prozkoumejte kódu pomocí syntaxe vizualizér Roslyn v sadě Visual Studio
description: Vizualizér syntaxe poskytuje vizuální nástroj, který chcete prozkoumat modely, které .NET SDK kompilátoru platformy generuje pro kód.
ms.date: 03/07/2018
ms.custom: mvc
ms.openlocfilehash: 3029c868ad9b0384cf11e57a00b123acd1177806
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354657"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Prozkoumejte kódu pomocí syntaxe vizualizér Roslyn v sadě Visual Studio

Tento článek obsahuje přehled syntaxe vizualizér nástroj, který se dodává jako součást kompilátoru platformu .NET ("Roslyn") sady SDK. Vizualizér syntaxe je okno nástroje, který vám pomůže zkontrolovat a prozkoumejte stromy syntaxe. Je základní nástroj pochopit modely pro kód, který chcete analyzovat. Je také ladění při vývoji vaší vlastní aplikace s použitím kompilátoru platformu .NET ("Roslyn") sady SDK. Tento nástroj, jako je vytváření vaší první analyzátorů. Vizualizér vám pomůže pochopit modely používá rozhraní API. Můžete použít také nástroje, například [SharpLab](https://sharplab.io) nebo [LINQPad](https://www.linqpad.net/) kontrolovat kódu a pochopit stromy syntaxe.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Seznamte se s koncepty používané v sadě SDK platformy .NET kompilátoru načtením [přehled](compiler-api-model.md) článku. Poskytuje úvod do syntaxe stromy, uzlů, tokeny a trivia.

## <a name="syntax-visualizer"></a>Vizualizér syntaxe

**Syntaxe vizualizér** umožňuje kontroly strom syntaxe pro souboru kódu jazyka C# nebo VB v okně aktuální aktivní editor v prostředí Visual Studio IDE. Kliknutím na může být spuštěn vizualizér **zobrazení** > **ostatní okna** > **syntaxe vizualizér**.  Můžete také **Snadné spuštění** panelu nástrojů v pravém horním rohu. Typ "syntaxe" a příkaz Otevřít **syntaxe vizualizér** by se měla objevit.

Tento příkaz otevře vizualizér syntaxe jako plovoucí okno nástroje. Pokud nemáte, otevřete okno editoru kódu, zobrazení je prázdný, jak je znázorněno na následujícím obrázku. 

![Okno vizualizér syntaxe nástroje](media/syntax-visualizer/syntax-visualizer.png)

Ukotvení toto okno nástroj na vhodné místo v sadě Visual Studio, jako je například na levé straně. Vizualizér zobrazují informace o aktuální souboru kódu.

Vytvoření nového projektu pomocí **soubor** > **nový projekt** příkaz. Můžete vytvořit buď jazyka Visual Basic nebo C# projektu. Po otevření souboru hlavní kódu pro tento projekt sady Visual Studio zobrazí vizualizéru stromu syntaxe pro ni. Můžete otevřít všechny existující C# / VB soubor v této instanci sady Visual Studio a vizualizér zobrazí tento soubor stromu syntaxe. Pokud máte více souborů kódu otevřete v sadě Visual Studio, vizualizér zobrazí strom syntaxe pro k souboru momentálně aktivní kódu (kód souboru, který má právě fokus klávesnice.)

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Vizualizace stromu syntaxe jazyka C#](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Vizualizace stromu syntaxe jazyka Visual Basic](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak ukazuje předchozí bitové kopie, zobrazí okno vizualizér nástroje na začátku článku a mřížku vlastností v dolní části stromu syntaxe. Zobrazí mřížku vlastností vlastnosti položky, který je aktuálně vybrané ve stromu, včetně .NET *typ* a *druh* (SyntaxKind) položky.

Syntaxe stromy tvoří tři typy položek – *uzly*, *tokeny*, a *trivia*. Můžete si přečíst informace o těchto typů v [pracovat s syntaxe](work-with-syntax.md) článku. Položky jednotlivých typů jsou reprezentované pomocí různých barev. Klikněte na tlačítko 'Legendy' Přehled barvy použité.

Každá položka v stromu také zobrazuje vlastní **span**. **Span** je indexy tento uzel v textovém souboru (pozice počáteční a koncové).  V předchozím příkladu C#, vybraný "UsingKeyword [0..5)" token má **rozpětí** široké, který je pět znaků [0..5). "[.)" Zápis znamená, že počáteční index je součástí značka span, ale koncová index není.

Přejděte ke stromu dvěma způsoby:
* Rozbalit nebo klikněte na položky ve stromové struktuře. Vizualizér automaticky vybere text, odpovídající rozpětí tuto položku v editoru kódu.
* Klikněte na tlačítko nebo vyberte text, v editoru kódu. V předchozím příkladu VB Pokud vyberete řádek obsahující "Modul modul 1" v editoru kódu vizualizér automaticky přejde na odpovídající ModuleStatement uzel ve stromu. 

Vizualizér označuje položku ve stromu, jejichž rozpětí nejlepší odpovídá rozpětí textu vybraným v editoru.

Vizualizér aktualizuje stromu tak, aby odpovídaly změny v souboru active kódu. Přidejte volání `Console.WriteLine()` uvnitř `Main()`. Jak budete zadávat, aktualizuje vizualizéru stromu.

Pozastavení jednou zadáním zadali `Console.`. Stromu má některé barva růžově položek. V typu kódu v tomto okamžiku nejsou chyby (také označované jako 'Diagnostiky'). Tyto chyby jsou připojené k uzlům, tokeny a trivia ve stromu syntaxe. Vizualizér se dozvíte, které položky mají chyby, které jsou připojené k je zvýraznění na pozadí růžově. Chyby na libovolnou položku barevné růžový podržením ukazatele nad položku si můžete prohlédnout. Vizualizér se zobrazí jenom syntaktické chyby (tyto chyby související s syntaxe kód typové); nezobrazuje žádné sémantické chyby.
 
## <a name="syntax-graphs"></a>Syntaxe grafy

Klikněte pravým tlačítkem na libovolnou položku v stromu a klikněte na **zobrazit graf syntaxe směrované**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Vizualizér zobrazuje grafické reprezentace podstrom root na vybranou položku. Opakujte tyto kroky **MethodDeclaration** uzlu odpovídající `Main()` metoda v příkladu C#. Vizualizér zobrazí syntaxe graf, který vypadá takto:

![Zobrazení grafu syntaxe jazyka C#](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

Opakujte stejný pro **SubBlock** uzlu odpovídající `Main()` metoda v předchozím příkladu jazyka Visual Basic. Vizualizér zobrazí syntaxe graf, který vypadá takto:

![Zobrazení grafu syntaxe jazyka Visual Basic](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Prohlížeč syntaxe graf má možnost Zobrazit legendu jeho barevné zvýrazňování schéma. Můžete také najet přes jednotlivé položky v syntaxi grafu pomocí myši zobrazíte vlastnosti odpovídající této položky.

Grafy syntaxi pro různé položky ve stromové struktuře můžete zobrazit opakovaně a ve stejném okně v sadě Visual Studio se vždy zobrazí v grafech. Toto okno při do vhodného umístění v sadě Visual Studio můžete ukotvit tak, že nemáte přepínání mezi kartami k zobrazení grafu nové syntaxe. Dolní níže oken editoru kódu, je často vhodné.

Tady je ukotvení rozložení pro použití s okno vizualizér nástroje a okno grafu syntaxe:

![Jeden ukotvení rozložení pro syntaxi a vizualizér okno grafu](media/syntax-visualizer/docking-layout.png)

Další možností je uvést okna grafu syntaxe na druhém monitoru, v rámci instalace dvou monitorů.

# <a name="inspecting-semantics"></a>Probíhá kontrola sémantiku

Vizualizér syntaxe umožní elementární kontrolu symboly a sémantické informace. Typ `double x = 1 + 1;` uvnitř Main() v příkladu C#. Pak vyberte výraz `1 + 1` v okně editoru kódu. Vizualizér klade důraz **AddExpression** uzlu vizualizér. Klikněte pravým tlačítkem na tomto **AddExpression** a klikněte na **zobrazení Symbol (pokud existuje)**. Všimněte si, že většina položky nabídky má kvalifikátor "je-li k dispozici". Vizualizér syntaxe zkontroluje, zda obsahuje vlastnosti uzlu, včetně vlastností, které nemusí být k dispozici pro všechny uzly. 

Mřížku vlastností v vizualizér aktualizací, jak je znázorněno na následujícím obrázku: symbol pro výraz **SynthesizedIntrinsicOperatorSymbol** s **typ = metoda**.

![Vlastnosti symbolu](media/syntax-visualizer/symbol-properties.png)

Zkuste **TypeSymbol zobrazení (pokud existuje)** pro stejné **AddExpression** uzlu. Vlastnost mřížky ve vizualizér aktualizací, jak je znázorněno na následujícím obrázku, která udává, že typ vybraného výrazu je `Int32`.

![Vlastnosti TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Zkuste **TypeSymbol převést zobrazení (pokud existuje)** pro stejné **AddExpression** uzlu. Mřížku vlastností aktualizace, která znamená, že i když je typ výrazu `Int32`, převedený typ výrazu je `Double` jak je znázorněno na následujícím obrázku. Tento uzel obsahuje převedený typ informací o symbolu, protože `Int32` výraz v kontextu, kde musí být převedena na dojde `Double`. Splňuje tento převod `Double` typ určený pro proměnnou `x` na levé straně operátoru přiřazení.

![Převedený TypeSymbol vlastnosti](media/syntax-visualizer/converted-type-symbol-properties.png)

Nakonec zkuste **zobrazení konstantní hodnota (pokud existuje)** pro stejné **AddExpression** uzlu. Mřížku vlastností ukazuje, že hodnota výrazu konstanta doba kompilace s hodnotou `2`.

![Konstantní hodnota](media/syntax-visualizer/constant-value.png)

V předchozím příkladu je možné replikovat také v jazyce VB. Typ `Dim x As Double = 1 + 1` v souboru jazyka Visual Basic. Vyberte výraz `1 + 1` v okně editoru kódu. Upozorňuje vizualizér odpovídající **AddExpression** uzlu vizualizér. Opakujte předchozí kroky pro tento **AddExpression** a měli byste vidět stejné výsledky.

Zkontrolujte další kód v jazyce VB. Aktualizujte si hlavní soubor VB následujícím kódem:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Tento kód představuje alias s názvem `C` která se mapuje na typ `System.Console` v horní části souboru a použije tento alias uvnitř `Main()`. Vyberte použití tento alias `C` v `C.WriteLine()`uvnitř `Main()` metoda. Vizualizér vybere odpovídající **IdentifierName** uzlu vizualizér. Klikněte pravým tlačítkem na tento uzel a klikněte na **zobrazení Symbol (pokud existuje)**. Mřížku vlastností označuje, že tento identifikátor je vázána na typ `System.Console` jak je znázorněno na následujícím obrázku:

![Vlastnosti symbolu](media/syntax-visualizer/symbol-visual-basic.png)

Zkuste **AliasSymbol zobrazení (pokud existuje)** pro stejné **IdentifierName** uzlu. Mřížku vlastností označuje identifikátor, který je alias s názvem `C` která je vázaná `System.Console` cíl. Jinými slovy, mřížku vlastností poskytuje informace o **AliasSymbol** odpovídající identifikátor `C`.

![Vlastnosti AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Zkontrolujte, zda je symbol odpovídající žádné deklarovaný typ, metoda, vlastnost. Vyberte odpovídající uzel v vizualizér a klikněte na **zobrazení Symbol (pokud existuje)**. Vyberte metodu `Sub Main()`, včetně těla metody. Klikněte na **zobrazení Symbol (pokud existuje)** pro příslušné **SubBlock** uzlu vizualizér. Zobrazí mřížky vlastnosti **MethodSymbol** pro tento **SubBlock** má název `Main` s návratovým typem `Void`.

![Zobrazení symbolů pro deklaraci – metoda](media/syntax-visualizer/method-symbol.png)

Příklady uvedené nahoře VB lze snadno replikovat v jazyce C#. Typ `using C = System.Console;` místě `Imports C = System.Console` pro alias. Předchozí kroky v jazyce C# poskytují stejné výsledky v okně vizualizér.

Sémantické kontroly operations jsou dostupné jenom na uzly. Nejsou k dispozici na tokeny nebo trivia. Ne všechny uzly mají zajímavé sémantické informace, chcete-li prověřit. Když uzel nemá zajímavé sémantické informace, kliknutím na **zobrazení * symbolů (pokud existuje)** zobrazí mřížku vlastností prázdné.

Si můžete přečíst informace o rozhraní API pro provádění sémantického analýzy v [pracovat s sémantiku](work-with-semantics.md) přehled dokumentu.

## <a name="closing-the-syntax-visualizer"></a>Zavřením vizualizér syntaxe

Okno vizualizér můžete zavřít, pokud ji nepoužíváte pro zjištění zdrojového kódu. Vizualizér syntaxe aktualizuje jeho zobrazení lze při procházení prostřednictvím kódu, úpravy a změna zdroje. Můžete získat rušivě, pokud ji nepoužíváte. 
