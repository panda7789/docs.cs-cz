---
title: Začínáme s sémantická analýza
description: Tento kurz obsahuje přehled práce s sémantické analýzy pomocí sady .NET SDK kompilátoru.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 188104c3430b4ca32578cd35d3e161a6eb0e0e1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61676063"
---
# <a name="get-started-with-semantic-analysis"></a>Začínáme s sémantická analýza

Tento kurz předpokládá, že jste obeznámeni s rozhraním API syntaxe. [Vám umožní začít analýza syntaxe](syntax-analysis.md) článek obsahuje úvod dostatečná.

V tomto kurzu, můžete prozkoumat **Symbol** a **vazba rozhraní API**. Tato rozhraní API poskytují informace o _sémantický význam_ programu. Umožňují o typech reprezentována žádný symbol ve svém programu otázek a odpovědí.

Budete muset nainstalovat **sada SDK platformy kompilátoru .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Principy kompilace a symboly

Při práci více s využitím .NET SDK kompilátoru, byste se seznámit s rozdíly mezi syntaxe rozhraní API a sémantické rozhraní API. **Syntaxe API** můžete se podívat _struktura_ programu. Často však chcete rozsáhlejší informace o sémantiku nebo _význam_ programu. Když dojde ke ztrátě kódu souboru nebo fragment kódu jazyka Visual Basic nebo C# mohou být v izolaci analyzovány syntakticky, není smysluplné klást otázky, jako "Jaký je typ této proměnné" v takový. Význam názvu typu může být závislá na odkazy na sestavení, importů oboru názvu nebo jiné soubory kódu. Tyto otázky jsou zodpovězeny pomocí **sémantické API**, konkrétně <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> třídy.

Instance <xref:Microsoft.CodeAnalysis.Compilation> je obdobou do jednoho projektu, jak je vidět v kompilátoru a představuje vše potřebné pro kompilaci programu Visual Basic nebo C#. **Kompilace** zahrnuje sadu zdrojových souborů ke kompilaci, odkazy na sestavení a možnosti kompilátoru. Můžete odůvodnitelný význam kódu pomocí všechny ostatní informace v tomto kontextu. A <xref:Microsoft.CodeAnalysis.Compilation> umožňuje najít **symboly** -entity jako jsou typy, obory názvů, členy a proměnné, které názvy a jiných výrazech odkazovat. Proces přiřazení názvy a výrazy s **symboly** nazývá **vazby**.

Stejně jako <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> je abstraktní třídy odvozené konfigurace specifické pro jazyk. Při vytváření instance kompilace, je nutné vyvolat výrobní metoda na <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) třídy.

## <a name="querying-symbols"></a>Dotazování na symboly

V tomto kurzu se podíváte na "Hello World" program znovu. Tento čas dotazování symboly v programu pochopit, jaké typy představují tyto symboly. Dotazování pro typy v oboru názvů a zjistěte, jak najít dostupné metody na typu.

Zobrazí se dokončený kód pro tuto ukázku v [našeho úložiště GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy stromu syntaxe. použít k podrobnému popisu různé prvky syntaxe, které jsou platné v různých umístěních v programu dědičnosti. Pomocí těchto rozhraní API často znamená, že vlastnosti přetypování nebo členy kolekce na konkrétní odvozené typy. V následujících příkladech jsou přiřazení a položky CAST samostatných příkazů pomocí explicitně proměnných. Si můžete přečíst kód chcete zobrazit návratové typy rozhraní API a modulu runtime typu vrácených objektů. V praxi je běžné použití implicitně typované proměnné a závisí na názvy rozhraní API pro popis typu objektů zkoumají.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu:

* V sadě Visual Studio, zvolte **souboru** > **nový** > **projektu** zobrazíte dialogové okno Nový projekt.
* V části **Visual C#** > **rozšiřitelnost**, zvolte **samostatný nástroj pro analýzu kódu**.
* Pojmenujte svůj projekt "**SemanticQuickStart**" a klikněte na tlačítko OK.

Chystáte se analyzovat základní "Hello World!" Program je uvedeno výše.
Přidejte text pro program Hello World jako konstanta ve vaší `Program` třídy:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dále přidejte následující kód k vytvoření stromu syntaxe v kódu text `programText` konstantní.  Přidejte následující řádek, který vaše `Main` metody:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

V dalším kroku sestavení <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> ze stromu, který jste už vytvořili. Ukázka "Hello World" spoléhá na <xref:System.String> a <xref:System.Console> typy. Potřebujete odkazovat na sestavení, který deklaruje tyto dva typy v kompilaci. Přidejte následující řádek, který vaše `Main` metodu pro vytvoření kompilace stromu syntaxe, včetně odkazu na odpovídající sestavení:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Metoda přidá odkazy na sestavení. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Metoda načte sestavení jako odkaz.

## <a name="querying-the-semantic-model"></a>Dotazování sémantického modelu

Jakmile budete mít <xref:Microsoft.CodeAnalysis.Compilation> můžete požádat pro <xref:Microsoft.CodeAnalysis.SemanticModel> pro všechny <xref:Microsoft.CodeAnalysis.SyntaxTree> součástí, která <xref:Microsoft.CodeAnalysis.Compilation>. Sémantický model si lze představit jako zdroj pro všechny informace, které by obvykle získáte z technologie intellisense. A <xref:Microsoft.CodeAnalysis.SemanticModel> lze zodpovědět otázky typu "Co jsou názvy v oboru na tomto místě?", "co mohou členové jsou přístupné z této metody?", "jaké proměnné se používají v tomto bloku textu?" a "Co tento název nebo výraz odkazovat?" Přidejte tento příkaz vytvoří sémantického modelu:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Vytvoření vazby názvu

<xref:Microsoft.CodeAnalysis.Compilation> Vytvoří <xref:Microsoft.CodeAnalysis.SemanticModel> z <xref:Microsoft.CodeAnalysis.SyntaxTree>. Po vytvoření modelu, můžete dát dotaz na hledání první `using` směrnice a získat informace o symbolech pro `System` oboru názvů. Přidejte následující dva řádky do vaší `Main` metodu pro vytvoření sémantického modelu a načtení symbolů pro první příkaz using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Předchozí kód ukazuje, jak vytvořit vazbu názvu v prvním `using` směrnice pro načtení <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> pro `System` oboru názvů. Předchozí kód také ukazuje, že používáte **syntaxe modelu** najít struktury kódu; použijete **sémantického modelu** pochopit jeho význam. **Syntaxe modelu** najde řetězec `System` v pomocí příkazu. **Sémantického modelu** má všechny informace týkající se typy definované v `System` oboru názvů.

Z <xref:Microsoft.CodeAnalysis.SymbolInfo> objektu můžete získat <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> pomocí <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> vlastnost. Tato vlastnost vrátí symbol, na který odkazuje tento výraz. Výrazy, které není odkazují na nic (jako je například číselné literály) této vlastnosti je `null`. Když <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> nemá hodnotu null, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> označuje typ symbolu. V tomto příkladu <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> je vlastnost <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Přidejte následující kód, který vaše `Main` metody. Načtení symbolů pro `System` obor názvů a zobrazí všechny podřízené obory názvů deklarovaný v `System` obor názvů:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Spusťte program a zobrazí se následující výstup:

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
> Výstup nezahrnuje každého oboru názvů, který je z podřízených oborů názvů `System` oboru názvů. Zobrazí každý obor názvů, který je k dispozici v této kompilaci, která odkazuje pouze na sestavení kde `System.String` je deklarována. Všechny obory názvů deklarovaný v jiných sestaveních nejsou známá, mají tato kompilace

### <a name="binding-an-expression"></a>Vazba výraz

Předchozí kód ukazuje, jak najít symbol vazbou na název. Existují jiné výrazy v programu v C#, která může být vázaný, které nejsou názvy. Abychom si předvedli tuto funkci, umožňuje přístup k vazby na jednoduché řetězcový literál.

Program "Hello World" obsahuje <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" řetězec se zobrazí v konzole.

Vyhledejte "Hello, World!" řetězec, který vyhledává jeden řetězcový literál v programu. Poté po nacházíte uzel syntaxe, získejte informace o typu pro tento uzel z sémantického modelu. Přidejte následující kód, který vaše `Main` metody:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Struktura zahrnuje <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> vlastnost, která umožňuje přístup k sémantické informace o typu literál. V tomto příkladu to `string` typu. Přidání deklarace, která se přiřadí tuto vlastnost na místní proměnnou:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

K dokončení tohoto kurzu Vytvořme dotaz LINQ, který vytvoří posloupnost všechny veřejné metody deklarované `string` typ, který vrací `string`. Tento dotaz získá složitá, takže můžeme sestavit řádek po řádku, pak rekonstrukci jako jeden dotaz. Zdroj pro tento dotaz je posloupnost všechny členy deklarované `string` typu:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Této zdrojové sekvence obsahuje všechny členy, včetně vlastností a polí, takže filtrovat pomocí <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> metodu najít prvky, které jsou <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> objekty:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

V dalším kroku přidejte další filtrem pro vrácení pouze těch metod, které jsou veřejné a návratový `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Vyberte pouze vlastnost name a pouze odlišné názvy odstraněním všech přetížení:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Můžete také sestavit celý dotaz pomocí syntaxe dotazu LINQ a zobrazte všechny názvy metod v konzole:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Sestavte program a spusťte ho. Byste měli vidět následující výstup:

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

Rozhraní API pro sémantické jste použili k vyhledání a zobrazení informací o symbolech, které jsou součástí tohoto programu.
