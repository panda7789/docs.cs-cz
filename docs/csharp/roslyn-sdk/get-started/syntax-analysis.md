---
title: Začínáme s analýzou syntaxe (rozhraní API Roslyn)
description: Úvod do procházení, dotazování a procházení stromů syntaxe.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 22d1303c9daa2ae35cf130b0c857cd7a5efdbe76
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240510"
---
# <a name="get-started-with-syntax-analysis"></a>Začínáme s analýzou syntaxe

V tomto kurzu prozkoumáte **rozhraní API syntaxe**. Rozhraní API syntaxe poskytuje přístup k datovým strukturám, které C# popisují nebo Visual Basic program. Tyto datové struktury mají dostatek podrobností, které mohou plně představovat libovolný program libovolné velikosti. Tyto struktury mohou popsat kompletní programy, které jsou zkompilovány a spouštěny správně. Můžou také popsat nedokončené programy, jak je píšete v editoru.

Chcete-li povolit tento bohatý výraz, datové struktury a rozhraní API, které tvoří rozhraní API syntaxe, jsou nutně složité. Pojďme začít s tím, jak datová struktura vypadá jako typický program "Hello World":

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

Podívejte se na text předchozího programu. Rozpoznáváte známé prvky. Celý text představuje jeden zdrojový soubor nebo **jednotku kompilace**. První tři řádky tohoto zdrojového souboru používají **direktivy**. Zbývající zdroj je obsažen v **deklaraci oboru názvů**. Deklarace oboru názvů obsahuje **deklaraci podřízené třídy**. Deklarace třídy obsahuje jednu **deklaraci metody**.

Rozhraní API syntaxe vytvoří stromovou strukturu s kořenovou jednotkou, která představuje kompilační jednotku. Uzly ve stromové struktuře reprezentují direktivy using, deklaraci oboru názvů a všechny ostatní prvky programu. Stromová struktura pokračuje na nejnižší úrovni: řetězec "Hello World!" je **řetězcový literálový token** , který je odvozeným **argumentem**. Rozhraní API syntaxe poskytuje přístup ke struktuře programu. Můžete zadávat dotazy na konkrétní postupy kódu, procházet celý strom a porozumět kódu a vytvářet nové stromy úpravou stávajícího stromu.

Tento stručný popis poskytuje přehled o druhu dostupné informace pomocí rozhraní API syntaxe. Rozhraní API syntaxe není nic větší než formální rozhraní API, které popisuje známé konstrukce kódu, ze C#kterých se dozvíte. Všechny možnosti obsahují informace o tom, jak je kód formátovaný, včetně konců řádků, mezer a odsazení. Pomocí těchto informací můžete kód plně vyjádřit jako zapsaný a načtený lidskými programátory nebo kompilátorem. Použití této struktury vám umožní pracovat se zdrojovým kódem na hluboko smysluplné úrovni. Již není to textový řetězec, ale data, která představují strukturu C# programu.

Abyste mohli začít, musíte nainstalovat **sadu .NET Compiler Platform SDK**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Principy stromů syntaxe

Použijete rozhraní API syntaxe pro jakoukoli analýzu struktury C# kódu. **Rozhraní API syntaxe** zveřejňuje analyzátory, stromy syntaxe a nástroje pro analýzu a sestavování stromů syntaxe. Je to způsob, jak hledat v kódu konkrétní prvky syntaxe, nebo si přečtěte kód pro program.

Strom syntaxe je datová struktura, kterou používají kompilátory C# a Visual Basic pro pochopení C# a Visual Basic programů. Stromy syntaxí jsou vytvářeny stejným analyzátorem, který se spouští při sestavení projektu nebo v případě, že je vývojář povede na F5. Stromy syntaxe mají plnou přesnost s jazykem; Všechny bitové informace v souboru kódu jsou reprezentovány ve stromové struktuře. Zápis stromu syntaxe do textu reprodukuje přesný původní text, který byl analyzován. Stromy syntaxe jsou také **neměnné**; Po vytvoření strom syntaxe nelze nikdy změnit. Uživatelé stromů mohou analyzovat stromy ve více vláknech, bez zámků nebo jiných měr souběžnosti, přičemž se data nikdy nemění. Rozhraní API můžete použít k vytvoření nových stromů, které jsou výsledkem úprav existujícího stromu.

Čtyři primární stavební kameny stromů syntaxe jsou:

* Třída <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, instance, která představuje celý strom analýzy. <xref:Microsoft.CodeAnalysis.SyntaxTree> je abstraktní třída, která obsahuje deriváty specifické pro jazyk. Metody Parse třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) slouží k analýze textu C# nebo Visual Basic.
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> třídy, jejichž instance reprezentují syntaktické konstrukce, jako jsou deklarace, příkazy, klauzule a výrazy.
* Struktura <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType>, která představuje jednotlivá klíčová slova, identifikátor, operátor nebo interpunkční znaménko.
* A nakonec <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> strukturu, která představuje syntakticky nevýznamné bity informací, jako jsou prázdné znaky mezi tokeny, direktivami předzpracování a komentáři.

Minihry, tokeny a uzly jsou vytvořeny hierarchicky pro vytvoření stromu, který zcela zastupuje vše v fragmentu Visual Basic nebo C# kódu. Tuto strukturu můžete zobrazit pomocí okna **syntax visualizer** . V aplikaci Visual Studio vyberte možnost **zobrazit** > **jiné > systému Windows** **syntax visualizer**. Například předchozí C# zdrojový soubor testovaný pomocí **syntax visualizer** vypadá jako na následujícím obrázku:

**SyntaxNode**: Blue | **SyntaxToken**: zelená | **SyntaxTrivia**: Red ![C# soubor kódu](media/walkthrough-csharp-syntax-figure1.png)

Přechodem na tuto stromovou strukturu můžete v souboru kódu najít libovolný příkaz, výraz, token nebo bitovou kopii prázdného místa.

I když můžete najít cokoli v souboru kódu pomocí rozhraní API syntaxe, Většina scénářů zahrnuje zkoumání malých fragmentů kódu nebo hledání konkrétních příkazů nebo fragmentů. Následující dva příklady ukazují typické použití pro procházení struktury kódu nebo hledání jednoduchých příkazů.

## <a name="traversing-trees"></a>Procházení stromů

Uzly ve stromu syntaxe můžete prozkoumávat dvěma způsoby. Můžete procházet stromovou strukturou a prozkoumávat jednotlivé uzly, nebo se můžete dotazovat na konkrétní prvky nebo uzly.

### <a name="manual-traversal"></a>Ruční procházení

Dokončený kód pro tuto ukázku najdete v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Typy stromové struktury syntaxe používají dědičnost k popisu různých syntaktických prvků, které jsou platné v různých umístěních v programu. Použití těchto rozhraní API často znamená přetypování vlastností nebo členů kolekce na konkrétní odvozené typy. V následujících příkladech je přiřazení a přetypování samostatné příkazy pomocí explicitně typových proměnných. Můžete si přečíst kód a zobrazit návratové typy rozhraní API a typ modulu runtime vrácených objektů. V praxi je obvyklejší používat implicitně typové proměnné a spoléhat na názvy rozhraní API k popisu typu testovaných objektů.

Vytvořit nový C# projekt **Nástroje pro analýzu samostatného kódu** :

* V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt** . zobrazí se dialogové okno Nový projekt.
* V části **rozšiřitelnost** **vizuálního C#**  > vyberte **Nástroj pro analýzu**samostatného kódu.
* Pojmenujte projekt "**SyntaxTreeManualTraversal**" a klikněte na tlačítko OK.

Chystáte se analyzovat základní "Hello World!" program byl zobrazen výše.
Do `Program` třídy přidejte text pro Hello World program jako konstantu:

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dále přidejte následující kód, který sestaví **strom syntaxe** pro text kódu v konstantě `programText`.  Do metody `Main` přidejte následující řádek:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Tyto dva řádky vytvoří strom a načtou kořenový uzel tohoto stromu. Nyní můžete zkontrolovat uzly ve stromové struktuře. Přidejte tyto řádky do metody `Main` pro zobrazení některých vlastností kořenového uzlu ve stromové struktuře:

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Spusťte aplikaci, abyste viděli, jak kód zjistil kořenový uzel v tomto stromu.

Obvykle byste procházeli procházením stromu, abyste se dozvěděli o kódu. V tomto příkladu analyzujete kód, který znáte pro zkoumání rozhraní API. Přidejte následující kód pro prohlédnutí prvního členu `root` uzlu:

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Tento člen je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Představuje vše v rozsahu deklarace `namespace HelloWorld`. Přidejte následující kód k prohlédnutí uzlů, které jsou deklarovány v oboru názvů `HelloWorld`:

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Spusťte program a podívejte se, co jste se naučili.

Teď, když víte, že je deklarace <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, deklarujte novou proměnnou tohoto typu pro prohlédnutí deklarace třídy. Tato třída obsahuje pouze jednoho člena: metodu `Main`. Přidejte následující kód k nalezení `Main` metody a přetypujte ji na <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Uzel deklarace metody obsahuje všechny syntaktické informace o metodě. Pojďme zobrazit návratový typ metody `Main`, číslo a typy argumentů a text těla metody. Přidejte následující kód:

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Spuštěním programu zobrazíte všechny informace, které jste zjistili o tomto programu:

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

Kromě procházení stromů můžete také prozkoumat strom syntaxe pomocí metod dotazů definovaných v <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Tyto metody by se měly hned seznámit s kýmkoli, kdo zná výraz XPath. Tyto metody můžete použít spolu s LINQ k rychlému vyhledání položek ve stromové struktuře. <xref:Microsoft.CodeAnalysis.SyntaxNode> obsahuje metody dotazů jako <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> a <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Pomocí těchto metod dotazů můžete najít argument metody `Main` jako alternativu k navigaci stromu. Do dolní části `Main` metody přidejte následující kód:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

První příkaz používá výraz LINQ a metodu <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> k vyhledání stejného parametru jako v předchozím příkladu.

Spusťte program a uvidíte, že výraz LINQ našel stejný parametr jako ruční navigace ve stromu.

Ukázka používá `WriteLine` příkazy pro zobrazení informací o stromech syntaxe při jejich procházení. Další informace můžete získat také spuštěním dokončeného programu v rámci ladicího programu. Můžete prozkoumávat více vlastností a metod, které jsou součástí stromu syntaxe vytvořeného pro program Hello World.

## <a name="syntax-walkers"></a>Průvodce syntaxí

Často chcete najít všechny uzly určitého typu ve stromu syntaxe, například každou deklaraci vlastnosti v souboru. Rozšířením třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> a přepsáním <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> metody zpracováváte všechny deklarace vlastností ve stromu syntaxe, aniž byste museli svou strukturu předem znát. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> je konkrétní druh <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor>, který rekurzivně navštíví uzel a každý z jeho podřízených objektů.

Tento příklad implementuje <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>, který prověřuje strom syntaxe. Shromažďuje `using` direktivy, které zjistí, že neimportují obor názvů `System`.

Vytvořit nový C# projekt **Nástroje pro analýzu samostatného kódu** ; pojmenujte ho "**SyntaxWalker**".

Dokončený kód pro tuto ukázku najdete v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). Ukázka na GitHubu obsahuje oba projekty popsané v tomto kurzu.

Stejně jako v předchozím příkladu můžete definovat řetězcovou konstantu, která bude obsahovat text programu, který budete analyzovat:

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Tento zdrojový text obsahuje `using` direktivy rozptýlené ve čtyřech různých umístěních: na úrovni souboru v oboru názvů nejvyšší úrovně a ve dvou vnořených oborech názvů. Tento příklad zvýrazní základní scénář použití třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> pro dotazování kódu. Je nenáročný na návštěvu všech uzlů v kořenovém stromu syntaxe pro vyhledání pomocí deklarací. Místo toho můžete vytvořit odvozenou třídu a přepsat metodu, která bude volána pouze v případě, že aktuální uzel ve stromové struktuře je Direktiva using. Váš návštěvník neprovádí žádnou práci na žádném jiném typu uzlu. Tato jediná metoda prověřuje jednotlivé příkazy `using` a vytvoří kolekci oborů názvů, které nejsou v oboru názvů `System`. Sestavíte <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>, který prověřuje všechny příkazy `using`, ale pouze příkazy `using`.

Nyní, když jste definovali text programu, je třeba vytvořit `SyntaxTree` a získat kořen této stromové struktury:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Dále vytvořte novou třídu. V aplikaci Visual Studio vyberte **projekt** > **Přidat novou položku**. V dialogovém okně **Přidat novou položku** jako název souboru zadejte *UsingCollector.cs* .

Implementujete funkci `using` návštěvníka ve třídě `UsingCollector`. Začněte tím, že třídu `UsingCollector` odvodíte z <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Pro uložení uzlů oboru názvů, které shromažďujete, potřebujete úložiště.  Deklarace veřejné vlastnosti jen pro čtení ve třídě `UsingCollector`; pomocí této proměnné můžete ukládat <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzly, které najdete:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Základní třída <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje logiku pro návštěvě každého uzlu ve stromové struktuře syntaxe. Odvozená třída Přepisuje metody volané pro konkrétní uzly, které vás zajímají. V takovém případě vás zajímá jakákoli `using` direktiva. To znamená, že je nutné přepsat metodu <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)>. Jedním z argumentů této metody je objekt <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType>. To je důležitou výhodou pro použití návštěvníků: volá přepsané metody s argumenty, které už jsou přetypování na konkrétní typ uzlu. Třída <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> obsahuje vlastnost <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name>, která ukládá název importovaného oboru názvů. Je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Do přepsání <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> přidejte následující kód:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Stejně jako v předchozím příkladu jste přidali celou řadu `WriteLine` příkazů, které pomáhají pochopit tuto metodu. Můžete vidět, kdy se volá a kde se do něj předávají argumenty.

Nakonec potřebujete přidat dva řádky kódu pro vytvoření `UsingCollector` a pokaždé, když navštívíte kořenový uzel a budete shromažďovat všechny příkazy `using`. Pak přidejte smyčku `foreach` pro zobrazení všech příkazů `using`, které kolekce nalezla:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Zkompilujte a spusťte program. Měl by se zobrazit následující výstup:

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

Blahopřejeme! Použili jste **rozhraní API syntaxe** k vyhledání konkrétních druhů C# příkazů a deklarací ve C# zdrojovém kódu.
