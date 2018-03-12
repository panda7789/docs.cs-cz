---
title: "Začínáme s sémantického analýzy"
description: "V tomto kurzu poskytuje přehled o práci s sémantického analysis pomocí .NET SDK kompilátoru."
author: billwagner
ms.author: wiwagn
ms.date: 02/06/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 94a28d21cfec1894c3ee3b631335043e1d0ec817
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2018
---
# <a name="get-started-with-semantic-analysis"></a>Začínáme s sémantického analýzy

Tento kurz předpokládá, že jste obeznámeni s rozhraním API syntaxe. [Začít pracovat s syntaxe analysis](syntax-analysis.md) článek obsahuje úvod dostatečná.

V tomto kurzu můžete prozkoumat **Symbol** a **vazby rozhraní API**. Tato rozhraní API zadání informací o _význam sémantického_ programu. Umožňují vám klást otázky a odpovědi na otázky o typech reprezentována žádné symbol v programu.

## <a name="understanding-compilations-and-symbols"></a>Principy kompilace a symboly.

Při práci více pomocí .NET SDK kompilátoru, byste se seznámit s rozdíly mezi syntaxe rozhraní API a sémantické rozhraní API. **Syntaxe API** umožňuje prohlížet _struktura_ programu. Často ale chcete bohatší informace o sémantiky nebo _význam_ programu. Při souboru přijít kódu nebo fragment kódu jazyka Visual Basic nebo C# lze Syntakticky analyzovat v izolaci, není smysluplný klást otázky, jako "co je typ Tato proměnná" ve vakuu. Význam název typu může být závislá na odkazy na sestavení, importy oboru názvů nebo jiné soubory kódu. Tyto otázky jsou zodpovězeny pomocí **sémantického API**, konkrétně <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> třídy.

Instance <xref:Microsoft.CodeAnalysis.Compilation> je obdobou k jedinému projektu jak je vidět kompilátorem a představuje vše potřebné ke kompilaci Visual Basic a C# program. **Kompilace** zahrnuje sadu zdrojových souborů, které mají být zkompilovány, do, odkazy na sestavení a možnosti kompilátoru. Vám může důvodu o význam kódu pomocí všechny ostatní informace v tomto kontextu. A <xref:Microsoft.CodeAnalysis.Compilation> umožňuje najít **symboly** -entit, jako jsou typy, obory názvů, členů a proměnné, které názvy a jiné výrazy. Proces přiřazení názvy a výrazy s **symboly** nazývá **vazby**.

Jako <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> je abstraktní třídy odvozené konfigurace konkrétní jazyk. Při vytváření instance kompilace, je nutné vyvolat metodu rodiny na <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) třída.

## <a name="querying-symbols"></a>Dotazování symboly

V tomto kurzu si prohlédnete "Hello World" program znovu. Tentokrát dotaz symboly v programu pochopit, jaké typy těchto představují symboly. Dotaz pro typy v oboru názvů a zjistěte, jak lze najít dostupné metody pro typ.

> [!IMPORTANT]
> Následující ukázky vyžadují **.NET SDK kompilátoru** nainstalován jako součást Visual Studio 2017. .NET SDK kompilátoru můžete najít jako poslední volitelné součásti, které jsou uvedené v části **vývoj rozšíření pro Visual Studio** zatížení. Šablony nejsou nainstalovány bez této součásti.

Zobrazí kód dokončení pro tato ukázka v [našem úložišti GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy stromu syntaxe využívají dědičnost k popisu různých syntaxe prvky, které jsou platné v různých umístěních v programu. Pomocí těchto rozhraní API často znamená přetypování vlastnosti nebo členy kolekce na konkrétní odvozené typy. V následujících příkladech přiřazení a položky CAST jsou samostatné příkazy, pomocí explicitně typové proměnné. Si můžete přečíst kód návratové typy rozhraní API a typ modulu runtime vrácených objektů. V praxi je dnes běžné použijte implicitně typovaná proměnné a závisí na názvy rozhraní API k popisu typ objektů, je zkontrolován.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu:

* V sadě Visual Studio, vyberte **soubor** > **nový** > **projektu** zobrazíte dialogové okno Nový projekt.
* V části **Visual C#** > **rozšiřitelnost**, zvolte **samostatný nástroj pro analýzu kódu**.
* Název projektu "**SemanticQuickStart**" a klikněte na tlačítko OK.

Chcete-li analyzovat základní "Hello, World!" Program uvedena výše.
Přidat text Hello, World programu jako konstanta ve vaší `Program` třídy:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dál přidejte následující kód k vytvoření strom syntaxe pro text v kódu `programText` konstantní.  Přidejte následující řádek na vaše `Main` metoda:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

V dalším kroku sestavení <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> ze stromu jste již vytvořili. Ukázka "Hello World" spoléhá na <xref:System.String> a <xref:System.Console> typy. Budete muset referenční sestavení, který deklaruje tyto dva typy v kompilaci. Přidejte následující řádek na vaše `Main` metodu pro vytvoření kompilace stromu syntaxe, včetně odkaz na příslušné sestavení:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Metoda přidá reference na kompilace. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Metoda načte sestavení jako odkaz. 

## <a name="querying-the-semantic-model"></a>Dotazování sémantického modelu

Jakmile máte <xref:Microsoft.CodeAnalysis.Compilation> můžete požádat ho <xref:Microsoft.CodeAnalysis.SemanticModel> pro žádné <xref:Microsoft.CodeAnalysis.SyntaxTree> obsažené v tom, že <xref:Microsoft.CodeAnalysis.Compilation>. Sémantický model si lze představit jako zdroj pro všechny informace, které by normálně sám intellisense. A <xref:Microsoft.CodeAnalysis.SemanticModel> lze zodpovědět otázky typu "co názvů jsou v oboru v tomto umístění?", "co členové jsou přístupné z této metody?", "jaké proměnné se používají v tomto bloku textu?" a "Co tento název nebo výraz k vztahuje?" Přidejte tento příkaz pro vytvoření sémantického modelu:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Vazba název

<xref:Microsoft.CodeAnalysis.Compilation> Vytvoří <xref:Microsoft.CodeAnalysis.SemanticModel> z <xref:Microsoft.CodeAnalysis.SyntaxTree>. Po vytvoření modelu, můžete ji najít první dotaz `using` – direktiva a získat informace o symbol `System` obor názvů. Přidejte tyto dva řádky do vaší `Main` metodu pro vytvoření sémantického modelu a načíst symbol pro první použití příkazu:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Předchozí kód ukazuje, jak vytvořit vazbu název v prvním `using` – direktiva k načtení <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> pro `System` oboru názvů. Předchozí kód také ukazuje, že používáte **syntaxe modelu** najít struktury kódu; použijete **sémantického modelu** pochopit její význam. **Syntaxe modelu** najde řetězec `System` v pomocí příkazu. **Sémantického modelu** všechny informace o typech definovaný v `System` oboru názvů.

Z <xref:Microsoft.CodeAnalysis.SymbolInfo> objekt můžete získat <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> pomocí <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> vlastnost. Tato vlastnost vrátí, které tento výraz odkazuje na symbol. Výrazy, které nejsou odkazují na nic (jako je například číselné literály) této vlastnosti je `null`. Když <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> nemá hodnotu null, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> označuje typ symbolu. V tomto příkladu <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> vlastnost je <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Přidejte následující kód do vaší `Main` metoda. Načte symbol pro `System` obor názvů a potom zobrazí všechny podřízené obory názvů deklarované v `System` obor názvů:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Spusťte program a měli byste vidět následující výstup:

```
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> Výstup nezahrnuje každý obor názvů, který není podřízeného oboru `System` oboru názvů. Zobrazí se každý obor názvů, který není součástí této kompilace, která pouze odkazuje na sestavení kde `System.String` je deklarován. Všechny obory názvů v ostatních sestavení deklarována nejsou známá, mají tato kompilace

### <a name="binding-an-expression"></a>Vazba výrazu

Předchozí kód ukazuje, jak najít symbol podle vazbu na název. Existují jiné výrazy v programu C#, který může být vázaný, které nejsou názvy. K předvedení tato možnost, umožňuje přístup k vazby ke jednoduché řetězcový literál.

Program "Hello World" obsahuje <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" řetězec zobrazení v konzole.

Najít "Hello, World!" řetězec tím, že jeden řetězcový literál v programu. Potom po nalezení uzel syntaxe, získáte typ informace pro tento uzel z sémantického modelu. Přidejte následující kód do vaší `Main` metoda:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Struktura zahrnuje <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> vlastnost, která umožňuje přístup k sémantické informace o typu literál. V tomto příkladu to je `string` typu. Přidejte deklaraci, která přiřadí tato vlastnost místní proměnné:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

K dokončení tohoto kurzu, Vytvořme LINQ dotazu, který vytvoří posloupnost všechny veřejné metody deklarovaná u `string` typ, který vrací `string`. Tento dotaz získá komplexní, proto budeme ho vytvořili řádek po řádku, pak je rekonstrukci jako jeden dotaz. Zdroj pro tento dotaz je pořadí deklarovaná u všech členů `string` typu:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Tento zdroj pořadí obsahuje všechny členy, včetně vlastnosti a pole, proto filtrovat pomocí <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> metody na hledání elementy, které jsou <xref:Microsoft.CodeAnalysis.IMethodSymbol?diplayProperty=nameWithType> objekty:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

V dalším kroku přidejte další filtr vrátit pouze těch metod, které jsou veřejné a zpět `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Vyberte jenom vlastnost název a pouze jedinečné názvy odebráním žádné přetížení:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Můžete také vytvořit celý dotaz pomocí syntaxe dotazů LINQ a potom v konzole zobrazit názvy všech metoda:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Build and display the results of the query.")]

Sestavte a spusťte program. Byste měli vidět následující výstup:

```
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```
Rozhraní API sémantického jste použili k vyhledání a zobrazení informací o symboly, které jsou součástí tohoto programu.
