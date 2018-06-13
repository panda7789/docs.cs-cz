---
title: Začínáme s analýzou syntaxe (Roslyn rozhraní API)
description: Úvod k procházení, dotazování a proti stromy syntaxe.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: e377fe10e094e958627c3503fc39b7e2d02b3d7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356241"
---
# <a name="get-started-with-syntax-analysis"></a>Začínáme s syntaxe analýzy

V tomto kurzu budete prozkoumat **syntaxe API**. Rozhraní API syntaxe poskytuje přístup k datové struktury, které popisují C# nebo Visual Basic program. Tyto datové struktury mít dostatek podrobností, může představovat plně žádné program jakékoli velikosti. Tyto struktury můžete popsat dokončení programy, které zkompilování a spuštění správně. Nedokončené programy, můžete také popisují, jako je v editoru.

Pokud chcete povolit tento bohaté výraz, jsou nutně komplexní datové struktury a rozhraní API, která tvoří rozhraní API syntaxe. Začněme s co datovou strukturu vypadá jako typický programu "Hello World":

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

Podívejte se na text předchozí aplikace. Můžete rozpoznat známé prvky. Celý text představuje jeden zdrojový soubor, nebo **jednotku kompilace**. První tři řádky tohoto souboru zdroje jsou **pomocí direktiv**. Je součástí zbývající zdroj **deklaraci oboru názvů**. Deklarace oboru názvů obsahuje podřízenou **deklarace třídy**. Deklarace třídy obsahuje jeden **deklarace metody**.

Rozhraní API syntaxe vytvoří stromová struktura s kořenovým představující jednotku kompilace. Uzly ve stromu představují použití direktivy, deklaraci oboru názvů a všechny další prvky programu. Stromovou strukturu pokračuje dolů na nejnižší úrovni: text "Hello, World!" je **token řetězcového literálu** tedy následníka **argument**. Rozhraní API syntaxe poskytuje přístup k struktura programu. Pro konkrétního kódu postupů, se můžete dotazovat provede celý strom zjistit kód a vytvořte nové stromy změnou na stávající strom.

Tento stručný popis poskytuje přehled o druh informací, které jsou přístupné pomocí syntaxe rozhraní API. Rozhraní API syntaxe není nic, které větší, než vytvoří formální rozhraní API, který popisuje kód obeznámeni, budete vědět z jazyka C#. Všechny schopnosti zahrnují informace o tom, jak kód formátována včetně konce řádku, mezer a odsazení. Na základě těchto informací můžete plně představují kód jako zapisovat a čtení lidského programátory nebo kompilátoru. Tato struktura pomocí umožňuje interakci se zdrojovým kódem na úrovni hluboko smysluplný. Už je textové řetězce, ale data, která představuje struktura programu v C#.

Abyste mohli začít, budete muset nainstalovat **SDK pro platformu .NET kompilátoru**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Principy syntaxe stromů

Můžete použít rozhraní API syntaxe pro nějakou analýzu struktury kódu C#. **Syntaxe API** zpřístupní analyzátory, stromy syntaxe a nástroje pro analýzu a vytváření stromů syntaxe. Je způsob, jakým vyhledávání kódu pro specifickou syntaxi elementy nebo číst kód programu.

Stromu syntaxe je datová struktura, použít k pochopení programy C# a Visual Basic kompilátory jazyka C# a Visual Basic. Syntaxe stromy vytváří analyzátorem se spouští při sestavení projektu nebo vývojář dotkne F5. Syntaxe stromy mít úplná věrnosti s jazykem; každý bit informace v souboru kódu je reprezentována ve stromové struktuře. Zápis stromu syntaxe na text se shoduje s přesnou původní text, který byl analyzovat. Syntaxe stromy jsou také **neměnné**; po vytvoření syntaxi stromu nesmí nikdy změnit. Příjemci stromy můžete analyzovat stromů ve více vláknech bez zámky nebo jiných opatření souběžnosti s vědomím, že se nikdy mění data. Rozhraní API slouží k vytvoření nové stromy, které jsou výsledkem Úprava stávající strom.

Čtyři základní stavební kameny stromy syntaxe je:

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> Třídy, strom analýzy celého představuje o instanci. <xref:Microsoft.CodeAnalysis.SyntaxTree> je abstraktní třída, která má odvozené konfigurace konkrétní jazyk. Pomocí metody analýzy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) třídy analyzovat textu v C# nebo VB.
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> Třída, která instance představují syntaktické konstrukce, jako je například deklarace, příkazy, výrazy a klauzule.
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> Strukturu, která představuje jednotlivé – klíčové slovo, identifikátor, operátor nebo interpunkce.
* A nakonec <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> struktura, která představuje syntakticky zanedbatelný bity informace, jako je prázdné místo mezi tokeny, direktivy předběžného zpracování a komentáře.

Trivia, tokeny a uzly se skládají hierarchicky vytvoříte strom, který představuje úplně vše v fragment kódu Visual Basic a C#. Můžete zobrazit pomocí tato struktura **syntaxe vizualizér** okno. V sadě Visual Studio, vyberte **zobrazení** > **ostatní okna** > **syntaxe vizualizér**. Například předchozí C# zdrojový soubor zkontrolován pomocí **syntaxe vizualizér** vypadá jako na následujícím obrázku:

**SyntaxNode**: Blue | **SyntaxToken**: zelená | **SyntaxTrivia**: Red ![souboru kódu C#](media/walkthrough-csharp-syntax-figure1.png)

Přechodem tuto stromovou strukturu můžete vyhledat všechny prohlášení, výrazu, token nebo bit prázdné znaky v souboru kódu.

Při nic najdete v souboru kódu pomocí syntaxe rozhraní API, většina scénářů zahrnovat zkoumání Malé fragmenty kódu nebo vyhledat konkrétní příkazy nebo fragmenty. Dva příklady, které následují zobrazit typické používá k procházení struktury kódu nebo vyhledejte jeden příkazy.

## <a name="traversing-trees"></a>Procházení stromů

Můžete zkontrolovat uzly ve stromu syntaxe dvěma způsoby. Můžete procházet stromu prozkoumat každý uzel, nebo můžete vyhledat konkrétní prvky nebo uzlů.

### <a name="manual-traversal"></a>Ruční traversal

Zobrazí kód dokončení pro tato ukázka v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Typy stromu syntaxe využívají dědičnost k popisu různých syntaxe prvky, které jsou platné v různých umístěních v programu. Pomocí těchto rozhraní API často znamená přetypování vlastnosti nebo členy kolekce na konkrétní odvozené typy. V následujících příkladech přiřazení a položky CAST jsou samostatné příkazy, pomocí explicitně typové proměnné. Si můžete přečíst kód návratové typy rozhraní API a typ modulu runtime vrácených objektů. V praxi je dnes běžné použijte implicitně typovaná proměnné a závisí na názvy rozhraní API k popisu typ objektů, je zkontrolován.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu:

* V sadě Visual Studio, vyberte **soubor** > **nový** > **projektu** zobrazíte dialogové okno Nový projekt.
* V části **Visual C#** > **rozšiřitelnost**, zvolte **samostatný nástroj pro analýzu kódu**.
* Název projektu "**SyntaxTreeManualTraversal**" a klikněte na tlačítko OK.

Chcete-li analyzovat základní "Hello, World!" Program uvedena výše.
Přidat text Hello, World programu jako konstanta ve vaší `Program` třídy:

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dál přidejte následující kód k vytvoření **stromu syntaxe** v kódu text `programText` konstantní.  Přidejte následující řádek na vaše `Main` metoda:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Tyto dva řádky vytvořit stromu a získat kořenový uzel stromové struktuře. Nyní můžete zkontrolovat uzly ve stromu. Přidejte tyto řádky do vaší `Main` metodu pro zobrazení některých vlastností kořenový uzel ve stromové struktuře:

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Spuštění aplikace, abyste viděli, co zjistí o kořenový uzel ve stromu tento kód.

Obvykle by prošel stromu Další informace o kód. V tomto příkladu při analýze kódu, které znáte a prozkoumejte rozhraní API. Přidejte následující kód k prozkoumání první člen `root` uzlu:

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Tento člen <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Reprezentuje vše v rámci oboru `namespace HelloWorld` deklarace. Přidejte následující kód zjistit, co jsou uzly uvnitř deklarované `HelloWorld` obor názvů:

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Spusťte aplikaci a zjistěte, co jste se naučili.

Nyní když znáte deklaraci je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, deklarovat nové proměnné tohoto typu a zkontrolujte deklaraci třídy. Tato třída obsahuje pouze jednoho člena: `Main` metoda. Přidejte následující kód k vyhledání `Main` metody a vysílat <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Uzel deklarace metoda obsahuje syntaktické informace o metodě. Umožňuje zobrazit návratový typ `Main` metoda, počet a typy argumentů a základní text metody. Přidejte následující kód:

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Spusťte program zobrazíte všechny informace, které jste se seznámili s o tomto programu:

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

Kromě procházení stromy, můžete si také prostudovat stromu syntaxe dotazu metodami definované na <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Tyto metody by měla být okamžitě známým všem obeznámeni s XPath. Tyto metody s dotazy LINQ vám pomůže rychle najít věcí ve stromu. <xref:Microsoft.CodeAnalysis.SyntaxNode> , Jako má metody dotazů <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> a <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Tyto metody dotazů můžete použít k vyhledání argument `Main` metoda jako alternativu k procházení stromu. Přidejte následující kód k dolnímu okraji vaší `Main` metoda:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

První příkaz používá výrazu LINQ a <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> metodu vyhledání parametr stejné jako v předchozím příkladu.

Spustit program a zobrazí se, zda výraz LINQ najít stejný parametr jako ručně navigace stromu.

Příklad používá `WriteLine` příkazy pro zobrazení informací o syntaxi stromy jako jejich je provázán. Můžete si také přečíst víc spuštěním programu dokončení pod ladicího programu. Můžete zkontrolovat informace o vlastnosti a metody, které jsou součástí strom syntaxe pro hello world program.

## <a name="syntax-walkers"></a>Syntaxe walkers

Často budete chtít najít všechny uzly určitého typu ve stromu syntaxe, například každých deklarace vlastnosti v souboru. Tím, že rozšíří <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> třídy a přepsání <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> metoda, při zpracování každé deklarace vlastnosti ve stromu syntaxe bez znalosti jeho struktura předem. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> je zvláštní druh <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> této rekurzivně navštíví uzlu a každý z jeho podřízených položek.

Tento příklad implementuje <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> který zkoumá stromu syntaxe. Shromáždí `using` direktivy najde, které nejsou importu `System` oboru názvů.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu; název "**SyntaxWalker**."

Zobrazí kód dokončení pro tato ukázka v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). Ukázce na Githubu obsahuje oba projekty popsané v tomto kurzu.

Stejně jako v předchozím příkladu můžete definovat na řetězcovou konstantu pro uložení text programu, který se chystáte analýza:

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Tento zdroj text obsahuje `using` direktivy rozmístěny na čtyři různých umístěních: úrovni souborů, v oboru názvů nejvyšší úrovně a v dva vnořené obory názvů. Tento příklad klade důraz základní scénáře použití <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> třída kódu dotazu. Je náročná navštívit každý uzel ve stromu syntaxe kořenové najít pomocí deklarace. Místo toho vytvořte odvozené třídě a přepsat metodu, která je volána jenom v případě, že je aktuální uzel ve stromové struktuře pomocí – direktiva. Návštěvník neprovádí žádné další práce z jiné typy uzlů. Tato metoda jeden kontroluje všechny `using` příkazy a vytvoří kolekci oborů názvů, které nejsou v `System` oboru názvů. Sestavování <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> , hledá všechny `using` příkazy, ale pouze `using` příkazy.

Teď, když jste definovali text programu, je nutné vytvořit `SyntaxTree` a získat kořenovém stromové struktuře:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Dál vytvořte novou třídu. V sadě Visual Studio, vyberte **projektu** > **přidat novou položku**. V **přidat novou položku** typ dialogu *UsingCollector.cs* jako název souboru.

Můžete implementovat `using` návštěvníka funkce v `UsingCollector` třídy. Spustit tím, že `UsingCollector` třída odvozena od <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Je třeba úložiště pro uložení oboru názvů uzly, které shromažďujete.  Deklarace veřejné vlastnosti jen pro čtení ve `UsingCollector` třída; pomocí této proměnné můžete ukládat <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzly můžete najít:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Základní třída <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje logiku pro navštívit každý uzel ve stromu syntaxe. Odvozené třídy přepíše metody volána pro konkrétní uzly, které vás zajímají. V takovém případě byste chtěli v žádném `using` – direktiva. To znamená, že je nutné přepsat <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> metoda. Jeden argument této metody je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> objektu. To je důležité nabízí použití návštěvníkům: volání metody přepsaného s argumenty již přetypovat na typ konkrétním uzlu. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> Třída má <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> vlastnost, která ukládá název oboru názvů importována. Je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Přidejte následující kód v <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> přepsání:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Jako předchozí příklad, jste přidali celou řadu `WriteLine` příkazy, které pomáhají při pochopení této metody. Uvidíte, kdy se nazývá a jaké argumenty jsou do ní předán pokaždé, když.

Nakonec budete muset přidat dva řádky kódu k vytvoření `UsingCollector` a mějte ho navštívit kořenového uzlu, shromažďování všech `using` příkazy. Potom přidat `foreach` smyčky pro zobrazení všech `using` příkazy nalezen vaší kolekce:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Zkompilování a spuštění programu. Byste měli vidět následující výstup:

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

Blahopřejeme! Jste použili **syntaxe API** najít konkrétní typy C# příkazy a deklarace v jazyce C# zdrojový kód.
