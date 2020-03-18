---
title: Začínáme se syntaktickou analýzou (Roslyn API)
description: Úvod do procházení, dotazování a chůze syntaxe stromy.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 22d1303c9daa2ae35cf130b0c857cd7a5efdbe76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240510"
---
# <a name="get-started-with-syntax-analysis"></a>Začínáme se syntaktickou analýzou

V tomto kurzu budete zkoumat **syntaxní rozhraní API**. Syntaxe ROZHRANÍ API poskytuje přístup k datovým strukturám, které popisují c# nebo visual basic program. Tyto datové struktury mají dostatek podrobností, aby mohly plně reprezentovat libovolný program libovolné velikosti. Tyto struktury mohou popisovat úplné programy, které kompilují a spouštějí správně. Mohou také popsat neúplné programy, jak je píšete, v editoru.

Chcete-li povolit tento bohatý výraz, datové struktury a rozhraní API, které tvoří syntaxe rozhraní API jsou nutně složité. Začněme s tím, jak vypadá datová struktura pro typický program "Hello World":

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

Podívejte se na text předchozího programu. Poznáváte známé prvky. Celý text představuje jeden zdrojový soubor nebo **jednotku kompilace**. První tři řádky tohoto zdrojového souboru **používají direktivy**. Zbývající zdroj je obsažen v **deklaraci oboru názvů**. Deklarace oboru názvů obsahuje deklaraci podřízené **třídy**. Deklarace třídy obsahuje **jednu deklaraci metody**.

Syntaxe ROZHRANÍ API vytvoří stromovou strukturu s kořenem představující jednotku kompilace. Uzly ve stromu představují pomocí směrnic, deklarace oboru názvů a všechny ostatní prvky programu. Stromová struktura pokračuje až na nejnižší úroveň: řetězec "Hello World!" je **řetězec literál token,** který je potomkem **argumentu**. Syntaxapi poskytuje přístup ke struktuře programu. Můžete dotaz na konkrétní postupy kódu, chodit celý strom pochopit kód a vytvořit nové stromy úpravou existující strom.

Tento stručný popis poskytuje přehled o druhu informací přístupných pomocí syntaxe API. Syntaxapi není nic jiného než formální rozhraní API, které popisuje známé konstrukce kódu znáte z Jazyka C#. Úplné možnosti zahrnují informace o tom, jak je kód formátován, včetně konců řádků, prázdného místa a odsazení. Pomocí těchto informací můžete plně reprezentovat kód jako napsaný a přečtený lidskými programátory nebo kompilátorem. Pomocí této struktury umožňuje interakci se zdrojovým kódem na hluboce smysluplné úrovni. Již nejsou textové řetězce, ale data, která představují strukturu programu Jazyka C#.

Chcete-li začít, budete muset nainstalovat **sdk platformy kompilátoru .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Principy stromů syntaxe

Syntaxe ROZHRANÍ API pro všechny analýzy struktury kódu Jazyka C#. Syntaxe **ROZHRANÍ API** zpřístupňuje analyzátory, stromy syntaxe a nástroje pro analýzu a vytváření stromů syntaxe. Je to, jak hledat kód pro konkrétní prvky syntaxe nebo číst kód pro program.

Strom syntaxe je datová struktura používaná kompilátory jazyka C# a Visual Basic k pochopení programů jazyka C# a Visual Basic. Syntaxe stromy jsou vytvářeny stejným analyzátorem, který běží při vytvoření projektu nebo vývojář hity F5. Stromy syntaxe mají plnou věrnost s jazykem; každý bit informací v souboru kódu je reprezentován ve stromu. Zápis stromu syntaxe do textu reprodukuje přesný původní text, který byl analyzován. Syntaxe stromy jsou také **neměnné**; po vytvoření stromu syntaxe nelze nikdy změnit. Spotřebitelé stromů můžete analyzovat stromy na více vláken, bez zámky nebo jiné souběžnosti opatření, s vědomím, že data se nikdy nezmění. Pomocí prostředí API můžete vytvořit nové stromy, které jsou výsledkem úpravy existujícího stromu.

Čtyři primární stavební bloky syntaktických stromů jsou:

* Třída, <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> jejíž instance představuje celý strom analýzy. <xref:Microsoft.CodeAnalysis.SyntaxTree>je abstraktní třída, která má deriváty specifické pro jazyk. Metody analýzy třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (nebo) <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>slouží k analýzě textu v jazyce C# nebo visual basicu.
* Třída, <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> jejíž instance představují syntaktické konstrukce, jako jsou deklarace, příkazy, klauzule a výrazy.
* Struktura, <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> která představuje jednotlivé klíčové slovo, identifikátor, operátor nebo interpunkci.
* A konečně <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> struktura, která představuje syntakticky nevýznamné bity informací, jako je například prázdné místo mezi tokeny, předzpracování směrnic a komentáře.

Trivia, tokeny a uzly jsou skládány hierarchicky tvořit strom, který zcela představuje vše v fragmentu kódu jazyka Nebo C#. Tuto strukturu můžete zobrazit pomocí okna **Vizualizace syntaxe.** Ve Visual Studiu zvolte **Zobrazit** > jiný**vizualizátor syntaxe****windows** > . Například předchozí zdrojový soubor Jazyka C# zkoumaný pomocí **vizualizéru syntaxe** vypadá jako následující obrázek:

**Syntaxnode**: Modrá | **Syntaxtoken**: Zelená | **Syntaxtrivia**: ![Červený soubor kódu C#](media/walkthrough-csharp-syntax-figure1.png)

Procházením této stromové struktury můžete najít libovolný příkaz, výraz, token nebo bit prázdného místa v souboru kódu.

Zatímco můžete najít cokoli v souboru kódu pomocí syntaxe rozhraní API, většina scénářů zahrnují zkoumání malé fragmenty kódu nebo hledání konkrétní příkazy nebo fragmenty. Dva následující příklady ukazují typické použití procházet strukturu kódu nebo hledat jednotlivé příkazy.

## <a name="traversing-trees"></a>Projíždějící stromy

Uzly ve stromu syntaxe můžete prozkoumat dvěma způsoby. Můžete procházet stromem prozkoumat každý uzel, nebo můžete dotaz na určité prvky nebo uzly.

### <a name="manual-traversal"></a>Ruční průchod

Hotový kód pro tuto ukázku najdete v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Typy stromů syntaxe používají dědičnost k popisu různých prvků syntaxe, které jsou platné na různých místech v programu. Použití těchto rozhraní API často znamená, že vlastnosti přetypování nebo členy kolekce na konkrétní odvozené typy. V následujících příkladech jsou přiřazení a přetypování samostatné příkazy, které používají explicitně zadané proměnné. Můžete si přečíst kód zobrazíte návratové typy rozhraní API a typ runtime vrácených objektů. V praxi je běžnější používat implicitně zadané proměnné a spoléhat se na názvy rozhraní API k popisu typu zkoumaných objektů.

Vytvořte nový projekt **nástroje pro analýzu samostatného kódu** jazyka C#:

* V Sadě Visual Studio zvolte **Soubor** > **nový** > **projekt,** abyste zobrazili dialogové okno Nový projekt.
* V **části Visual C#** > **Rozšiřitelnost**zvolte **Nástroj pro analýzu samostatného kódu**.
* Pojmenujte projekt **"SyntaxTreeManualTraversal**" a klepněte na tlačítko OK.

Budete analyzovat základní "Hello World!" program zobrazen dříve.
Přidejte text programu Hello World jako `Program` konstantu ve své třídě:

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dále přidejte následující kód k vytvoření **stromu syntaxe** pro text kódu v konstantě. `programText`  Do metody přidejte `Main` následující řádek:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Tyto dva řádky vytvořit strom a načíst kořenový uzel tohoto stromu. Nyní můžete prozkoumat uzly ve stromu. Přidejte tyto `Main` řádky do metody, abyste zobrazili některé vlastnosti kořenového uzlu ve stromu:

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Spusťte aplikaci a zjistěte, co váš kód zjistil o kořenovém uzlu v tomto stromu.

Obvykle byste procházet stromu se dozvíte o kódu. V tomto příkladu analyzujete kód, který znáte k prozkoumání api. Přidejte následující kód a zkontrolujte `root` prvního člena uzlu:

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Tento člen <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>je . Představuje vše, co je `namespace HelloWorld` v rozsahu deklarace. Přidejte následující kód a prozkoumejte, `HelloWorld` jaké uzly jsou deklarovány uvnitř oboru názvů:

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Spusťte program a zjistěte, co jste se naučili.

Nyní, když víte, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>že deklarace je , deklarujte novou proměnnou tohoto typu, abyste prozkoumali deklaraci třídy. Tato třída obsahuje pouze `Main` jeden člen: metoda. Přidejte následující kód, `Main` který najde metodu, a přetypujte ji do . <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Uzel deklarace metody obsahuje všechny syntaktické informace o metodě. Zobrazme návratový typ `Main` metody, počet a typy argumentů a základní text metody. Přidejte následující kód:

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Spuštěním programu zobrazíte všechny informace, které jste o tomto programu zjistili:

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

### <a name="query-methods"></a>Metody dotazu

Kromě procházení stromů můžete také prozkoumat strom syntaxe pomocí <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>metod dotazu definovaných v aplikaci . Tyto metody by měly být okamžitě obeznámeni s kýmkoli, kdo je obeznámen s XPath. Tyto metody můžete použít s LINQ rychle najít věci ve stromu. Má <xref:Microsoft.CodeAnalysis.SyntaxNode> metody dotazu, jako <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>jsou například , <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> a <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Tyto metody dotazu můžete najít argument `Main` metody jako alternativu k navigaci stromu. Přidejte následující kód na `Main` konec metody:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

První příkaz používá výraz LINQ <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> a metodu k vyhledání stejného parametru jako v předchozím příkladu.

Spusťte program a uvidíte, že výraz LINQ našel stejný parametr jako ruční navigace ve stromu.

Ukázka `WriteLine` používá příkazy k zobrazení informací o stromech syntaxe při jejich procházení. Můžete se také dozvědět mnohem více spuštěním dokončeného programu v ladicím programu. Můžete prozkoumat další vlastnosti a metody, které jsou součástí stromu syntaxe vytvořeného pro program Hello World.

## <a name="syntax-walkers"></a>Syntaxe chodci

Často chcete najít všechny uzly určitého typu ve stromu syntaxe, například každou deklaraci vlastností v souboru. Rozšířením <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> třídy a <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> přepsáním metody zpracujete každou deklaraci vlastnosti ve stromu syntaxe, aniž byste předem znali její strukturu. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>je specifický druh, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> který rekurzivně navštíví uzel a každý z jeho dětí.

Tento příklad implementuje, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> který zkoumá strom syntaxe. Shromažďuje direktivy, `using` které neimportují obor `System` názvů.

Vytvořte nový projekt **nástroje pro analýzu samostatného kódu** jazyka C#. pojmenujte **"SyntaxWalker**".

Hotový kód pro tuto ukázku najdete v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). Ukázka na GitHubu obsahuje oba projekty popsané v tomto kurzu.

Stejně jako v předchozí ukázce můžete definovat řetězcovou konstantu pro uložení textu programu, který budete analyzovat:

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Tento zdrojový `using` text obsahuje direktivy rozptýlené ve čtyřech různých umístěních: úroveň souboru, v oboru názvů nejvyšší úrovně a ve dvou vnořených oborech názvů. Tento příklad zvýrazní základní <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> scénář pro použití třídy k dotazu kódu. Bylo by těžkopádné navštívit každý uzel ve stromu syntaxe kořene najít pomocí deklarací. Místo toho vytvoříte odvozenou třídu a přepsat metodu, která se nazývá pouze v případě, že aktuální uzel ve stromu je using směrnice. Návštěvník neprovádí žádnou práci na jiných typech uzlů. Tato jediná metoda zkoumá `using` každý z příkazů a vytvoří kolekci oborů `System` názvů, které nejsou v oboru názvů. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> Sestavení, který zkoumá všechny `using` příkazy, `using` ale pouze příkazy.

Nyní, když jste definovali text programu, `SyntaxTree` musíte vytvořit a získat kořen tohoto stromu:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Dále vytvořte novou třídu. V Sadě Visual Studio zvolte Přidat**novou položku** **projektu** > . V dialogovém okně **Přidat novou položku** *UsingCollector.cs* jako název souboru.

Implementovat `using` funkce návštěvníka `UsingCollector` ve třídě. Začněte tím, `UsingCollector` že <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>třída odvodit z .

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Potřebujete úložiště pro uložení uzlů oboru názvů, které shromažďujete.  Deklarujte veřejnou vlastnost `UsingCollector` jen pro čtení ve třídě; tuto proměnnou použijete <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> k uložení uzlů, které najdete:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Základní třída <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje logiku k návštěvě každého uzlu ve stromu syntaxe. Odvozená třída přepíše metody volané pro konkrétní uzly, které vás zajímají. V tomto případě vás zajímá `using` jakákoliv směrnice. To znamená, že <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> je nutné přepsat metodu. Jeden argument této metody <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> je objekt. To je důležitá výhoda pro použití návštěvníků: volají přepsané metody s argumenty již přetypované na konkrétní typ uzlu. Třída <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> má <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> vlastnost, která ukládá název oboru názvů, který se importuje. Je to <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Do přepsání <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> přidejte následující kód:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Stejně jako v předchozím příkladu jste `WriteLine` přidali různé příkazy, které pomáhají pochopit tuto metodu. Můžete vidět, kdy se nazývá a jaké argumenty jsou předány pokaždé.

Nakonec je třeba přidat dva řádky kódu `UsingCollector` k vytvoření a mít navštívit kořenový uzel, shromažďování všech `using` příkazů. Potom přidejte `foreach` smyčku, `using` která zobrazí všechny příkazy, které váš sběratel našel:

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

Blahopřejeme! Syntaxe rozhraní **API** jste použili k vyhledání konkrétních druhů příkazů a deklarací jazyka C# ve zdrojovém kódu jazyka C#.
