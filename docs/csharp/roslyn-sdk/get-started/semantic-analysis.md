---
title: Začínáme se sémantickou analýzou
description: Tento kurz poskytuje přehled o práci se sémantickou analýzou pomocí sady .NET Compiler SDK.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 80a814054ab95a5b6585289e8580a725b18ca44e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252937"
---
# <a name="get-started-with-semantic-analysis"></a>Začínáme se sémantickou analýzou

V tomto kurzu se předpokládá, že jste obeznámeni s rozhraním API syntaxe. Článek Začínáme [s analýzou syntaxe](syntax-analysis.md) poskytuje dostatečný Úvod.

V tomto kurzu prozkoumáte **symbol** a **vazby rozhraní API**. Tato rozhraní API poskytují informace o _sémantickém významu_ programu. Umožňují klást dotazy a odpovídat na typy reprezentované libovolným symbolem v programu.

Budete muset nainstalovat **sadu .NET Compiler Platform SDK**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Porozumění kompilacím a symbolům

Při práci více se sadou .NET Compiler SDK se můžete seznámit s rozdíly mezi syntaxí API a sémantickým rozhraním API. **Rozhraní API syntaxe** vám umožní podívat se na _strukturu_ programu. Nicméně často potřebujete bohatší informace o sémantikě nebo _významu_ programu. Přestože volný soubor kódu nebo fragment kódu jazyka VB nebo C# kódu lze syntakticky analyzovat v izolaci, není smysluplné klást otázky, jako je například typ této proměnné, v vaku. Význam názvu typu může být závislý na odkazech na sestavení, na importech oboru názvů nebo v jiných souborech kódu. Tyto otázky jsou zodpovězeny pomocí **sémantického rozhraní API**, konkrétně <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> třídy.

Instance <xref:Microsoft.CodeAnalysis.Compilation> je analogická k jednomu projektu, jak je vidět kompilátorem a představuje vše potřebné pro zkompilování Visual Basic nebo C# programu. **Kompilace** obsahuje sadu zdrojových souborů, které mají být zkompilovány, odkazy na sestavení a možnosti kompilátoru. Důvody týkající se významu kódu můžete získat pomocí všech dalších informací v tomto kontextu. Umožňuje vyhledat symboly – entity, jako jsou typy, obory názvů, členy a proměnné, které názvy a další výrazy odkazují na. <xref:Microsoft.CodeAnalysis.Compilation> Proces přidružení názvů a výrazů se **symboly** se nazývá **vazba**.

Jako <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>jeabstraktnítřída sderivátyspecifickýmiprojazyk.<xref:Microsoft.CodeAnalysis.Compilation> Při vytváření instance kompilace musíte vyvolat metodu objektu pro vytváření ve <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> třídě (nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>).

## <a name="querying-symbols"></a>Dotazování na symboly

V tomto kurzu se podíváte na Hello World program znovu. Tentokrát zadáte dotaz na symboly v programu, abyste pochopili, jaké typy symbolů představuje. Budete dotazováni na typy v oboru názvů a naučíte se najít metody dostupné pro typ.

Dokončený kód pro tuto ukázku najdete v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy stromové struktury syntaxe používají dědičnost k popisu různých syntaktických prvků, které jsou platné v různých umístěních v programu. Použití těchto rozhraní API často znamená přetypování vlastností nebo členů kolekce na konkrétní odvozené typy. V následujících příkladech je přiřazení a přetypování samostatné příkazy pomocí explicitně typových proměnných. Můžete si přečíst kód a zobrazit návratové typy rozhraní API a typ modulu runtime vrácených objektů. V praxi je obvyklejší používat implicitně typové proměnné a spoléhat na názvy rozhraní API k popisu typu testovaných objektů.

Vytvořit nový C# projekt **Nástroje pro analýzu samostatného kódu** :

* V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt** a zobrazte tak dialogové okno Nový projekt.
* V části **rozšiřitelnost**  >  **vizuálu C#** vyberte **Nástroj pro analýzu**samostatného kódu.
* Pojmenujte projekt "**SemanticQuickStart**" a klikněte na tlačítko OK.

Chystáte se analyzovat základní "Hello World!" program byl zobrazen výše.
Přidejte text pro Hello World program jako konstantu do vaší `Program` třídy:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dále přidejte následující kód, který sestaví strom syntaxe pro text kódu v `programText` konstantě.  Do `Main` metody přidejte následující řádek:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Dále Sestavte <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> ze stromu, který jste už vytvořili. Ukázka "Hello World" spoléhá na <xref:System.String> typy a. <xref:System.Console> Musíte odkazovat na sestavení, které deklaruje tyto dva typy v kompilaci. Přidejte následující řádek do `Main` metody pro vytvoření kompilace stromu syntaxe, včetně odkazu na příslušné sestavení:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Metoda přidá odkazy na kompilaci. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Metoda načte sestavení jako odkaz.

## <a name="querying-the-semantic-model"></a>Dotazování sémantického modelu

Jakmile budete mít k <xref:Microsoft.CodeAnalysis.Compilation> dispozici, můžete si ji <xref:Microsoft.CodeAnalysis.SemanticModel> vyžádat <xref:Microsoft.CodeAnalysis.SyntaxTree> pro všechny, <xref:Microsoft.CodeAnalysis.Compilation>které obsahují. Sémantický model si můžete představit jako zdroj pro všechny informace, které byste normálně získali z IntelliSense. <xref:Microsoft.CodeAnalysis.SemanticModel> Může odpovídat na otázky, jako je "Jaké názvy jsou v oboru v tomto umístění?", "které členy jsou přístupné z této metody?" "," Jaké proměnné jsou použity v tomto bloku textu? "" a "čemu tento název/výraz odkazují na?" Přidáním tohoto příkazu vytvořte sémantický model:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Vazba názvu

<xref:Microsoft.CodeAnalysis.Compilation> Vytvoří z.<xref:Microsoft.CodeAnalysis.SemanticModel> <xref:Microsoft.CodeAnalysis.SyntaxTree> Po vytvoření modelu se můžete dotazovat na jeho první `using` direktivu a načíst informace o symbolech `System` pro obor názvů. Přidejte tyto dva řádky do `Main` metody, abyste vytvořili sémantický model a načetli symbol pro první příkaz using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Předchozí kód ukazuje, jak vytvořit název v první `using` direktivě pro <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> načtení pro `System` obor názvů. Předchozí kód také ukazuje použití **modelu syntaxe** k nalezení struktury kódu; použijte **sémantický model** pro pochopení svého významu. **Model syntaxe** vyhledá řetězec `System` v příkazu Using. **Sémantický model** obsahuje všechny informace o typech definovaných v `System` oboru názvů.

Z objektu můžete <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> získat pomocí <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> vlastnosti. <xref:Microsoft.CodeAnalysis.SymbolInfo> Tato vlastnost vrací symbol, na který tento výraz odkazuje. Pro výrazy, které neodkazují na cokoli (například číselné literály) Tato vlastnost `null`je. Pokud není null <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> , označuje typ symbolu. <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> V tomto příkladu <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>je vlastnost. Do `Main` metody přidejte následující kód. Načte symbol pro `System` obor názvů a potom zobrazí všechny podřízené obory názvů deklarované `System` v oboru názvů:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Spusťte program a měl by se zobrazit následující výstup:

```output
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
> Výstup nezahrnuje každý obor názvů, který je podřízeným oborem `System` názvů oboru názvů. Zobrazuje každý obor názvů, který je k dispozici v této kompilaci, který odkazuje pouze `System.String` na sestavení, které je deklarováno. V této kompilaci nejsou známy žádné obory názvů deklarované v jiných sestaveních.

### <a name="binding-an-expression"></a>Vazba výrazu

Předchozí kód ukazuje, jak najít symbol pomocí vazby na název. V C# programu existují další výrazy, které mohou být vázány na názvy. K tomu, aby bylo možné tuto funkci předvést, pojďme přistoupit k vazbě na jednoduchý řetězcový literál.

Program "Hello World" obsahuje <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" řetězec zobrazený v konzole.

Najdete "Hello, World!" řetězec vyhledáním jediného řetězcového literálu v programu. Po umístění uzlu syntaxe získáte informace o typu pro tento uzel ze sémantického modelu. Do `Main` metody přidejte následující kód:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Struktura<xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> obsahuje vlastnost, která umožňuje přístup k sémantickým informacím o typu literálu. V tomto příkladu je to `string` typ. Přidejte deklaraci, která přiřadí tuto vlastnost místní proměnné:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Pro dokončení tohoto kurzu sestavíme dotaz LINQ, který vytvoří sekvenci všech veřejných metod deklarovaných v `string` typu, který `string`vrací. Tento dotaz je složitý, takže ho sestavíme řádek po řádku a pak ho znovu sestavíte jako jeden dotaz. Zdroj pro tento dotaz je sekvence všech členů deklarovaných u `string` tohoto typu:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Tato zdrojová sekvence obsahuje všechny členy, včetně vlastností a polí, takže je vyfiltrujte <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> pomocí metody pro nalezení prvků, <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> které jsou objekty:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Dále přidejte další filtr, který vrátí pouze ty metody, které jsou veřejné a vrátí `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Vyberte pouze vlastnost název a jedinečné názvy odebráním všech přetížení:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Můžete také vytvořit úplný dotaz pomocí syntaxe dotazu LINQ a pak zobrazit všechny názvy metod v konzole:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Sestavte program a spusťte ho. Měl by se zobrazit následující výstup:

```output
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

Použili jste sémantické rozhraní API k vyhledání a zobrazení informací o symbolech, které jsou součástí tohoto programu.
