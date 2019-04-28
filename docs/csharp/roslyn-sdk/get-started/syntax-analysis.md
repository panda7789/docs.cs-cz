---
title: Začínáme s analýzou syntaxe (rozhraní Roslyn API)
description: Úvod do procházení, dotazování a procházení stromu syntaxe.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: e377fe10e094e958627c3503fc39b7e2d02b3d7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706622"
---
# <a name="get-started-with-syntax-analysis"></a>Začínáme s analýzou syntaxe

V tomto kurzu prozkoumáte **syntaxe API**. Syntaxe rozhraní API poskytuje přístup k datové struktury, které popisují C# nebo Visual Basic programu. Tyto datové struktury mají dostatek podrobných informací, že plně představují žádný program libovolné velikosti. Tyto struktury můžete popsat kompletních programů, které zkompilovat a spustit správně. Můžete najdete zde také popis neúplné programy, při psaní v editoru.

Pokud chcete povolit tento bohaté výraz, jsou nutně složité datových struktur a rozhraní API, která tvoří rozhraní API syntaxe. Začněme vypadá strukturu dat pro typické program "Hello World":

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Podívejte se na text předchozí aplikace. Můžete rozpoznat známé prvky. Celý text představuje jeden zdrojový soubor, nebo **kompilační jednotky**. První tři řádky daném zdrojovém souboru jsou **direktiv using**. Je součástí zbývající zdroje **deklarace oboru názvů**. Deklarace oboru názvů obsahuje podřízený **deklarace třídy**. Deklarace třídy obsahuje jeden **deklarace metody**.

Rozhraní API syntaxe vytvoří stromové struktury s kořenem představující kompilační jednotky. Uzly ve stromu představují na pomocí direktivy, deklarace oboru názvů a všechny ostatní prvky programu. Stromovou strukturu pokračuje dolů na nejnižší úroveň: řetězec "Hello World!" je **řetězcový literál token** , který je následníka **argument**. Syntaxe rozhraní API poskytuje přístup ke struktuře program. Můžete zadat dotaz na konkrétním kódu postupy provedou celý strom pochopit kód a vytvořit nové stromové struktury tak, že upravíte na stávající strom.

Tento stručný popis poskytuje přehled o druh informací, které jsou přístupné pomocí syntaxe rozhraní API. Rozhraní API syntaxe není nic víc než formální rozhraní API, které popisuje známé kód vytvoří, můžete znát z jazyka C#. Všechny možnosti zahrnují informace o formátování kódu včetně konce řádků, prázdné znaky a odsazení. Na základě těchto informací můžete plně představují kódu, jak je uvedená a čtení lidské programátory nebo kompilátor. Pomocí této struktury vám umožní pracovat se zdrojovým kódem na úrovni hluboce smysluplné. Už je textové řetězce, ale data, která reprezentuje strukturu těchto programu v jazyce C#.

Abyste mohli začít, budete muset nainstalovat **sada SDK platformy kompilátoru .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Principy stromů syntaxe

Použití syntaxe rozhraní API pro analýzu struktury kódu jazyka C#. **Syntaxe API** zpřístupňuje analyzátory, stromové struktury syntaxe a nástroje pro analýzu a vytváření stromu syntaxe. Je jak vyhledávání kódu pro konkrétní syntaxe prvků, nebo si přečtěte kód programu.

Strom syntaxe je datová struktura používaná kompilátory C# a Visual Basic pro pochopení programů jazyka C# a Visual Basic. Stromy syntaxe se produkují analyzátorem spouští, když je sestaven projekt nebo vývojář narazí F5. Syntaxe stromové struktury mají Plnohodnotná jazyk; každý bit informace v souboru kódu je reprezentován ve stromové struktuře. Zápis stromu syntaxe. text se shoduje s přesnou původní text, který byl analyzován. Struktury syntaxe jsou také **neměnné**; po vytvoření syntaxi na strom lze nikdy změnit. Příjemci stromy můžete analyzovat stromů ve více vláknech, bez uzamčení nebo jiné míry souběžnosti vědomím, že data se nikdy nemění. Rozhraní API slouží k vytvoření nové stromové struktury, které jsou výsledkem Úprava stávající strom.

Má čtyři primární syntaxe stromů součásti:

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> Třídu, instanci z nich představuje strom celého analýzy. <xref:Microsoft.CodeAnalysis.SyntaxTree> je abstraktní třída, která má odvozené konfigurace specifické pro jazyk. Použití metod pro posunutí analýzy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) třídy se analyzovat text v jazyce C# nebo VB.
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> Třída, která instance představují syntaktické konstrukce, jako je například prohlášení, příkazy, klauzule a výrazy.
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> Strukturu, která představuje jednotlivé – klíčové slovo, identifikátor, operátor nebo interpunkční znaménka.
* A nakonec <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> struktura, která představuje syntakticky nevýznamné bits informace, jako jsou prázdné znaky mezi tokeny, direktivy předběžného zpracování a komentáře.

Triviální prvek, tokenů a uzly se skládají hierarchicky tvoří strom, který představuje úplně vše v fragment kódu jazyka Visual Basic nebo C#. Můžete zobrazit pomocí tato struktura **Syntax Visualizer** okna. V sadě Visual Studio, zvolte **zobrazení** > **ostatní Windows** > **Syntax Visualizer**. Například předchozím zdrojový soubor C# prozkoumat pomocí **Syntax Visualizer** vypadá podobně jako na následujícím obrázku:

**SyntaxNode**: Blue | **SyntaxToken**: Green | **SyntaxTrivia**: Červená ![ C# soubor kódu](media/walkthrough-csharp-syntax-figure1.png)

Otevřením této stromové struktury najdete prohlášení, výraz, token nebo trochu prázdné znaky v souboru kódu.

Když najdete něco v souboru kódu pomocí syntaxe rozhraní API, většina scénářů zahrnují zkoumání Malé fragmenty kódu nebo hledáním konkrétní příkazy nebo fragmentech. Tyto dva příklady, které následují zobrazit typické používá k procházení strukturu kódu, nebo vyhledejte jednotlivé příkazy.

## <a name="traversing-trees"></a>Procházení stromové struktury

Můžete prozkoumat uzlů ve stromu syntaxe dvěma způsoby. Můžete procházet stromu a zkontrolujte každý uzel, nebo můžete vyhledávat konkrétní prvky nebo uzly.

### <a name="manual-traversal"></a>Ruční procházení

Zobrazí se dokončený kód pro tuto ukázku v [našeho úložiště GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Typy stromu syntaxe. použít k podrobnému popisu různé prvky syntaxe, které jsou platné v různých umístěních v programu dědičnosti. Pomocí těchto rozhraní API často znamená, že vlastnosti přetypování nebo členy kolekce na konkrétní odvozené typy. V následujících příkladech jsou přiřazení a položky CAST samostatných příkazů pomocí explicitně proměnných. Si můžete přečíst kód chcete zobrazit návratové typy rozhraní API a modulu runtime typu vrácených objektů. V praxi je běžné použití implicitně typované proměnné a závisí na názvy rozhraní API pro popis typu objektů zkoumají.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu:

* V sadě Visual Studio, zvolte **souboru** > **nový** > **projektu** zobrazíte dialogové okno Nový projekt.
* V části **Visual C#** > **rozšiřitelnost**, zvolte **samostatný nástroj pro analýzu kódu**.
* Pojmenujte svůj projekt "**SyntaxTreeManualTraversal**" a klikněte na tlačítko OK.

Chystáte se analyzovat základní "Hello World!" Program je uvedeno výše.
Přidejte text pro program Hello World jako konstanta ve vaší `Program` třídy:

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dále přidejte následující kód k vytvoření **stromu syntaxe** v kódu text `programText` konstantní.  Přidejte následující řádek, který vaše `Main` metody:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Tyto dva řádky vytvoření stromu a načtení kořenového uzlu stromu. Nyní můžete prozkoumat uzlů ve stromu. Přidejte tyto řádky do vaší `Main` metodu pro zobrazení některých vlastností kořenový uzel ve stromu:

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Spusťte aplikaci, abyste viděli, co váš kód zjistí kořenový uzel v této struktuře.

Obvykle by procházení stromu Další informace o kód. V tomto příkladu při analýze kódu, který znáte prozkoumávat rozhraní API. Přidejte následující kód k prozkoumání prvního člena `root` uzlu:

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Je daný člen <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Představuje všechno, co je v oboru `namespace HelloWorld` deklarace. Přidejte následující kód pro zjištění, co jsou uzly deklarované uvnitř `HelloWorld` obor názvů:

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Spusťte program, abyste viděli, co jste se naučili.

Teď, když víte, deklarace je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, deklarovat novou proměnnou daného typu prozkoumat deklaraci třídy. Tato třída obsahuje pouze jednoho člena: `Main` metody. Přidejte následující kód k vyhledání `Main` metody a přetypovat ji na <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Uzel deklarace metody obsahuje syntaktické informace o metodě. Umožňuje zobrazit návratového typu `Main` metoda, počet a typy argumentů a text těla metody. Přidejte následující kód:

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Spusťte program, abyste viděli všechny informace, které jste se seznámili o tomto programu:

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration.
There are 1 members declared in this namespace.
The first member is a ClassDeclaration.
There are 1 members declared in the Program class.
The first member is a MethodDeclaration.
The return type of the Main method is void.
The method has 1 parameters.
The type of the args parameter is string[].
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a>Metody dotazů

Kromě procházení stromové struktury, můžete také prozkoumat pomocí dotazu metody definované ve stromu syntaxe <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Tyto metody by měl být okamžitě každý, kdo zná XPath. Tyto metody můžete použít s dotazy LINQ a rychle najít, co ve stromové struktuře. <xref:Microsoft.CodeAnalysis.SyntaxNode> Metody dotazu, jako má <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> a <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Tyto metody dotazu můžete použít k vyhledání argument `Main` metody jako alternativu k procházení stromu. Přidejte následující kód do spodní části vašeho `Main` metody:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

První příkaz používá výraz LINQ a <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> metodu vyhledání stejný parametr stejně jako v předchozím příkladu.

Spusťte program a uvidíte, že výraz LINQ nalezen stejný parametr jako ručně procházení stromu.

Ukázka používá `WriteLine` příkazy pro zobrazení informací o stromové struktury syntaxe, jako je provázán. Můžete také zjistíte, mnohem více spuštěním dokončení programu v ladicím programu. Můžete prozkoumat další vlastnosti a metody, které jsou součástí stromu syntaxe pro hello world program.

## <a name="syntax-walkers"></a>Syntaxe chodce

Často budete chtít najít všechny uzly určitého typu ve stromu syntaxe, například všechny deklarace vlastnosti v souboru. Tím, že rozšíří <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> třídy a přepsáním <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> metody zpracovat každou deklaraci vlastnosti ve stromu syntaxe bez znalosti jeho strukturu předem. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> je zvláštní druh <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> této rekurzivně navštíví uzlu a všech jejích potomků.

V tomto příkladu implementuje <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> , které bude zkoumat stromu syntaxe. Shromažďuje `using` direktivy najde, které nejsou import `System` oboru názvů.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu; je název "**SyntaxWalker**."

Zobrazí se dokončený kód pro tuto ukázku v [našeho úložiště GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). Ukázka na Githubu obsahuje oba projekty popsané v tomto kurzu.

Stejně jako v předchozí ukázce můžete definovat konstantu řetězce k uložení textu programu, který se chystáte analýza:

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Tento zdrojový text obsahuje `using` direktivy rozmístěno jinde ve čtyřech různých umístěních: úrovni souborů, v oboru nejvyšší úrovně a dvě vnořené obory názvů. Tento příklad ukazuje základní scénář pro použití <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> třídy dotazu kódu. Bylo by náročná navštívit každý uzel ve stromu syntaxe. kořenový najít pomocí deklarace. Místo toho vytvořte odvozené třídy a přepsat metodu, která je volána pouze v případě, že je aktuální uzel ve stromu using – direktiva. Návštěvník neprovádí žádné další práce z jiných typů uzlů. Tuto jedinou metodu prozkoumá všech `using` příkazy a sestavuje kolekci oborů názvů, které nejsou v `System` oboru názvů. Sestavení <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> , které bude zkoumat všechny `using` příkazy, ale jen `using` příkazy.

Teď, když jste definovali textem programu, je potřeba vytvořit `SyntaxTree` a získejte kořen stromu:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Dále vytvořte novou třídu. V sadě Visual Studio, zvolte **projektu** > **přidat novou položku**. V **přidat novou položku** typ dialogu *UsingCollector.cs* jako název souboru.

Můžete implementovat `using` návštěvníka funkce v `UsingCollector` třídy. Začněte tím, že `UsingCollector` třídu odvodit z <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Potřebujete úložiště pro uložení uzly oboru názvů, které děláte.  Deklarace veřejné vlastnosti jen pro čtení v `UsingCollector` třídy; můžete pomocí této proměnné můžete ukládat <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzly nenajdete:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Základní třída <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje logiku navštívit každý uzel ve stromu syntaxe. Odvozená třída přepíše metodami volanými pro konkrétním uzlům, které vás zajímají. V takovém případě máte zájem žádné `using` směrnice. To znamená, že je nutné přepsat <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> metody. Jeden argument této metody je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> objektu. To je důležité výhodou použití návštěvníkům: volání přetížené metody s argumenty již přetypovat na typ konkrétní uzel. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> Třída nemá <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> vlastnost, která ukládá název oboru názvů importu. Jde <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Přidejte následující kód <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> přepsat:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Jak s předchozím příkladu si přidáte širokou škálu `WriteLine` příkazy pro výpomoc s principy této metody. Zobrazí se, když je volána, a jaké argumenty jsou předány do ní pokaždé, když.

Nakonec budete muset přidat kód, který vytvoří dva řádky `UsingCollector` a jeho navštivte kořenový uzel, shromažďování všech `using` příkazy. Pak přidejte `foreach` smyčky pro zobrazení všech `using` příkazy vaše sběrač nalezl:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Kompilace a spuštění programu. Byste měli vidět následující výstup:

```console
        VisitUsingDirective called with System.
        VisitUsingDirective called with System.Collections.Generic.
        VisitUsingDirective called with System.Linq.
        VisitUsingDirective called with System.Text.
        VisitUsingDirective called with Microsoft.CodeAnalysis.
                Success. Adding Microsoft.CodeAnalysis.
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp.
                Success. Adding Microsoft.CodeAnalysis.CSharp.
        VisitUsingDirective called with Microsoft.
                Success. Adding Microsoft.
        VisitUsingDirective called with System.ComponentModel.
        VisitUsingDirective called with Microsoft.Win32.
                Success. Adding Microsoft.Win32.
        VisitUsingDirective called with System.Runtime.InteropServices.
        VisitUsingDirective called with System.CodeDom.
        VisitUsingDirective called with Microsoft.CSharp.
                Success. Adding Microsoft.CSharp.
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

Blahopřejeme! Využili jste **syntaxe API** najít konkrétní typy jazyka C# příkazy a deklarace v jazyce C# zdrojový kód.
