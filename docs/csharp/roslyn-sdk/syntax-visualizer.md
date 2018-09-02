---
title: Prozkoumání kódu pomocí vizualizéru syntaxe Roslyn v sadě Visual Studio
description: Vizualizéru syntaxe poskytuje vizuální nástroj, který chcete prozkoumat modelů, který generuje sada SDK platformy kompilátoru .NET pro kód.
ms.date: 03/07/2018
ms.custom: mvc
ms.openlocfilehash: 3029c868ad9b0384cf11e57a00b123acd1177806
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456461"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Prozkoumání kódu pomocí vizualizéru syntaxe Roslyn v sadě Visual Studio

Tento článek obsahuje přehled nástroje Vizualizéru syntaxe, která je dodávána jako součást .NET Compiler Platform ("Roslyn"), sady SDK. Vizualizéru syntaxe je panel nástrojů, která pomáhá kontrolovat a prozkoumejte stromu syntaxe. Je to důležitý nástroj, abyste pochopili vzory pro kód, který chcete analyzovat. Je také ladění při vývoji vlastních aplikací pomocí .NET Compiler Platform ("Roslyn"), sady SDK. Tento nástroj, jako je vytváření vaší první analyzátory. Vizualizér vám pomůže pochopit modely, které používají rozhraní API. Můžete použít také nástroje, jako je [SharpLab](https://sharplab.io) nebo [LINQPad](https://www.linqpad.net/) ke kontrole kódu a pochopení stromu syntaxe.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Seznamte se s koncepty používané v platformě kompilátoru .NET SDK najdete [přehled](compiler-api-model.md) článku. Poskytuje úvod do stromové struktury syntaxe, uzly, tokenů a triviální prvek.

## <a name="syntax-visualizer"></a>Vizualizéru syntaxe

**Syntax Visualizer** umožňuje kontrolu strom syntaxe pro soubor kódu jazyka C# nebo VB v aktuální okno aktivní editor v integrovaném vývojovém prostředí sady Visual Studio. Vizualizér můžete spustit kliknutím na **zobrazení** > **ostatní Windows** > **Syntax Visualizer**.  Můžete také použít **Snadné spuštění** nástrojů v pravém horním rohu. Typ "syntaxe" a příkaz pro otevření **Syntax Visualizer** by se měla objevit.

Tento příkaz otevře Vizualizéru syntaxe jako plovoucí okno nástroje. Pokud nemáte otevřete okno editoru kódu, zobrazení je prázdný, jak je znázorněno na následujícím obrázku. 

![Panel nástrojů Vizualizéru syntaxe](media/syntax-visualizer/syntax-visualizer.png)

Ukotvěte tomto panelu nástrojů na vhodného umístění v sadě Visual Studio, například na levé straně. Vizualizér s informacemi o aktuální soubor kódu.

Vytvořte nový projekt pomocí **souboru** > **nový projekt** příkazu. Můžete vytvořit buď VB nebo C# projekt. Po otevření souboru hlavní kód pro tento projekt sady Visual Studio zobrazí vizualizéru stromu syntaxe pro něj. Můžete otevřít libovolný existující C# / VB souboru v této instanci aplikace Visual Studio a vizualizéru zobrazí stromu syntaxe. Tento soubor. Pokud máte více souborů kódu, otevřete v sadě Visual Studio, vizualizéru zobrazí strom syntaxe pro soubor aktuálně aktivní kódu (soubor kódu, který má fokus klávesnice.)

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Vizualizace stromu syntaxe jazyka C#](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Vizualizace stromu syntaxe jazyka Visual Basic](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak je znázorněno v předchozí obrázky, zobrazí okno nástroje vizualizátor nahoře a vlastnost mřížky v dolní části stromu syntaxe. Mřížky vlastností zobrazuje vlastnosti položky, která je aktuálně vybrána ve stromu, včetně .NET *typ* a *druh* (SyntaxKind) položky.

Syntaxe stromové struktury tvoří tři typy položek – *uzly*, *tokeny*, a *triviální prvek*. Můžete si přečíst další informace o těchto typů v [práce se syntaxí](work-with-syntax.md) článku. Položky jednotlivých typů jsou reprezentovány pomocí různých barev. Klikněte na tlačítko 'Legendy' získáte přehled o barvy použité.

Každé položky ve stromové struktuře také zobrazí jeho vlastní **span**. **Span** je indexy (pozice počáteční a koncové) v textovém souboru tohoto uzlu.  V předchozím příkladu C#, vybrané "UsingKeyword [0..5)" token má **rozpětí** široké, to znamená 5 znaků [0..5). "[.)" Zápis znamená, že počáteční index je součástí rozsahu, ale koncové index není.

Existují dva způsoby, jak procházet stromu:
* Rozbalit nebo klikněte na položky ve stromové struktuře. Vizualizér automaticky vybere text odpovídá rozpětí pro tuto položku v editoru kódu.
* Klikněte na tlačítko nebo vybrat text v editoru kódu. V předchozím příkladu VB Pokud vyberete řádek obsahující "Modul Module1" v editoru kódu vizualizéru automaticky přejde na odpovídající ModuleStatement uzel ve stromu. 

Vizualizér zvýrazní položky ve stromu, jejichž rozsah nejlepší odpovídá text vybraný v editoru v rozsahu.

Vizualizér aktualizuje stromu tak, aby odpovídaly změny ve zdrojovém souboru aktivní. Přidejte volání do `Console.WriteLine()` uvnitř `Main()`. Při psaní aktualizuje vizualizéru stromu.

Pozastavit jednou zadáte zadali `Console.`. Stromu má některé položky vybarvenými růžově. V typu kódu jsou v tuto chvíli chyby (také označované jako "Diagnostika"). Tyto chyby jsou připojené k uzlům, tokenů a triviální prvek ve stromu syntaxe. Vizualizéru se dozvíte, které položky mají chyby, které jsou připojené k nim zvýraznění na pozadí růžově. Chyby na libovolnou položku barevné růžový najedete myší na položku, můžete si prohlédnout. Vizualizér zobrazí pouze syntaktické chyby (tyto chyby související s syntaxe zadaný kód); nezobrazuje žádné sémantické chyby.
 
## <a name="syntax-graphs"></a>Syntaxe grafy

Klikněte pravým tlačítkem na libovolné položky ve stromové struktuře a klikněte na **zobrazení orientovaného grafu syntaxe**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Vizualizér zobrazí grafické znázornění podstrom umístěných na vybranou položku. Zkuste tyto kroky pro **MethodDeclaration** uzlu odpovídající `Main()` metoda ve příklad jazyka C#. Vizualizér zobrazuje graf s syntaxe vypadá takto:

![Zobrazení grafu syntaxe jazyka C#](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

Zkuste to stejné pro **SubBlock** uzlu odpovídající `Main()` metoda v předchozím příkladu jazyka Visual Basic. Vizualizér zobrazuje graf s syntaxe vypadá takto:

![Zobrazení grafu syntaxe jazyka Visual Basic](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Prohlížeč grafu syntaxe je možnost Zobrazit legendu její barevné schéma. Můžete také myši jednotlivých položek v syntaxi grafu pomocí myši zobrazíte její odpovídající položky.

Syntaxe grafů pro různé položky ve stromové struktuře můžete zobrazit opakovaně a grafy se vždy zobrazí ve stejném okně v sadě Visual Studio. Toto okno na místě v sadě Visual Studio můžete ukotvit, takže nemusíte přepínat mezi kartami k zobrazení grafu nové syntaxe. Dolní části níže oken editoru kódu, je často vhodné.

Tady je dokovací rozložení pomocí okna nástroje vizualizátor a syntaxe grafu:

![Jeden dokovací rozložení pro okno vizualizéru a syntaxe grafu](media/syntax-visualizer/docking-layout.png)

Další možností je umístit okno grafu syntaxe na druhém monitoru, v nastavení dvou monitorů.

# <a name="inspecting-semantics"></a>Kontrola sémantiku

Syntax Visualizer umožňuje základní kontroly symbolů a sémantické informace. Typ `double x = 1 + 1;` uvnitř Main() v příklad jazyka C#. Vyberte výraz `1 + 1` v okně editoru kódu. Zvýrazní vizualizéru **AddExpression** uzlu ve vizualizátoru. Klikněte pravým tlačítkem myši na tomto **AddExpression** a klikněte na **zobrazení symbolů (pokud existuje)**. Všimněte si, že většina položek nabídky má kvalifikátor "je-li k dispozici". Syntax Visualizer zkontroluje, zda obsahuje vlastnosti uzlu, včetně vlastnosti, které nemusí být k dispozici pro všechny uzly. 

Vlastnost mřížky ve vizualizéru aktualizací, jak je znázorněno na následujícím obrázku: symbol výrazu je **SynthesizedIntrinsicOperatorSymbol** s **druh = metoda**.

![Vlastnosti symbolu](media/syntax-visualizer/symbol-properties.png)

Zkuste **TypeSymbol zobrazení (pokud existuje)** pro stejný **AddExpression** uzlu. Mřížku vlastností ve vizualizátoru aktualizací, jak je znázorněno na následujícím obrázku, označující, jestli je typ vybraného výrazu `Int32`.

![Vlastnosti TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Zkuste **zobrazení převedena TypeSymbol (pokud existuje)** pro stejný **AddExpression** uzlu. Aktualizuje vlastnosti mřížky označující, že i když je typ výrazu `Int32`, je převedená typu výrazu `Double` jak je znázorněno na následujícím obrázku. Tento uzel obsahuje informace o symbolech převedeným typem, protože `Int32` dojde k výraz v kontextu, ve kterém musí být převeden do `Double`. Splňuje tento převod `Double` typ zadaný pro proměnnou `x` na levé straně operátoru přiřazení.

![Převedený TypeSymbol vlastnosti](media/syntax-visualizer/converted-type-symbol-properties.png)

A konečně, zkuste **zobrazení konstantní hodnotu (pokud existuje)** pro stejný **AddExpression** uzlu. Mřížky vlastností ukazuje, že hodnota výrazu časovou konstantou kompilace s hodnotou `2`.

![Konstantní hodnota](media/syntax-visualizer/constant-value.png)

V předchozím příkladu se dají taky replikovat v jazyce VB. Typ `Dim x As Double = 1 + 1` v souboru jazyka Visual Basic. Vyberte výraz `1 + 1` v okně editoru kódu. Vizualizér zvýrazní odpovídající **AddExpression** uzlu ve vizualizátoru. Zopakujte předchozí kroky pro tento **AddExpression** a měla by se zobrazit stejné výsledky.

Prozkoumat další kód v jazyce VB. Aktualizujte hlavní soubor jazyka Visual Basic s následujícím kódem:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Tento kód představuje alias s názvem `C` , která se mapuje na typ `System.Console` v horní části souboru a použije tento alias uvnitř `Main()`. Vyberte možnost použít tento alias `C` v `C.WriteLine()`uvnitř `Main()` metody. Vizualizér vybere odpovídající **IdentifierName** uzlu ve vizualizátoru. Klikněte pravým tlačítkem na tento uzel a klikněte na **zobrazení symbolů (pokud existuje)**. Mřížkou označuje, že tento identifikátor je vázán na typ `System.Console` jak je znázorněno na následujícím obrázku:

![Vlastnosti symbolu](media/syntax-visualizer/symbol-visual-basic.png)

Zkuste **AliasSymbol zobrazení (pokud existuje)** pro stejný **IdentifierName** uzlu. Mřížkou označuje identifikátor alias s názvem `C` , který je vázán `System.Console` cíl. Jinými slovy, mřížky vlastností obsahuje informace týkající **AliasSymbol** odpovídající identifikátor `C`.

![Vlastnosti AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Zkontrolujte, zda symbol odpovídá jakékoli deklarovaného typu, metoda, vlastnost. Vyberte odpovídající uzel ve vizualizátoru a klikněte na **zobrazení symbolů (pokud existuje)**. Vyberte metodu `Sub Main()`, včetně těla metody. Klikněte na **zobrazení symbolů (pokud existuje)** pro příslušné **SubBlock** uzlu ve vizualizátoru. U vlastnosti mřížky se zobrazí **MethodSymbol** to **SubBlock** má název `Main` s návratový typ `Void`.

![Zobrazení symbolů pro deklaraci – metoda](media/syntax-visualizer/method-symbol.png)

Výše uvedené příklady VB je možné snadno replikovat v jazyce C#. Typ `using C = System.Console;` místo `Imports C = System.Console` aliasu. Předchozí kroky v jazyce C# poskytují shodné výsledky v okně vizualizér.

Sémantické kontroly operace jsou dostupné jenom pro uzly. Nejsou k dispozici na tokeny nebo triviální prvek. Ne všechny uzly měly zajímavé sémantické informace ke kontrole. Pokud uzel není zajímavé sémantické informace, že kliknete na **zobrazení * Symbol (pokud existuje)** zobrazí mřížku prázdnou vlastnost.

Další informace o rozhraních API pro sémantické analýzy v [práce se sémantikou](work-with-semantics.md) přehled dokumentu.

## <a name="closing-the-syntax-visualizer"></a>Zavření vizualizéru syntaxe

Vizualizéru okno můžete zavřít, když ji nepoužíváte ke kontrole zdrojového kódu. Vizualizéru syntaxe aktualizuje zobrazení průběhu procházení kódu, úpravy a změna zdroje. Můžete získat rušivé, když ji nepoužíváte. 
