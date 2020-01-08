---
title: Začínáme se sémantickou analýzou
description: Tento kurz poskytuje přehled o práci se sémantickou analýzou pomocí sady .NET Compiler SDK.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 7bf2f40ea0bc059d9c517780016ca5deb805ceb6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346983"
---
# <a name="get-started-with-semantic-analysis"></a>Začínáme se sémantickou analýzou

V tomto kurzu se předpokládá, že jste obeznámeni s rozhraním API syntaxe. Článek Začínáme [s analýzou syntaxe](syntax-analysis.md) poskytuje dostatečný Úvod.

V tomto kurzu prozkoumáte **symbol** a **vazby rozhraní API**. Tato rozhraní API poskytují informace o _sémantickém významu_ programu. Umožňují klást dotazy a odpovídat na typy reprezentované libovolným symbolem v programu.

Budete muset nainstalovat **sadu .NET Compiler Platform SDK**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Porozumění kompilacím a symbolům

Při práci více se sadou .NET Compiler SDK se můžete seznámit s rozdíly mezi syntaxí API a sémantickým rozhraním API. **Rozhraní API syntaxe** vám umožní podívat se na _strukturu_ programu. Nicméně často potřebujete bohatší informace o sémantikě nebo _významu_ programu. I když volný soubor kódu nebo fragment kódu Visual Basic nebo C# kódu mohou být syntakticky analyzovány v izolaci, není smysluplné klást otázky, jako je například typ této proměnné, v vaku. Význam názvu typu může být závislý na odkazech na sestavení, na importech oboru názvů nebo v jiných souborech kódu. Tyto otázky jsou zodpovězeny pomocí **sémantického rozhraní API**, konkrétně <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> třídy.

Instance <xref:Microsoft.CodeAnalysis.Compilation> je podobná jednomu projektu, jak je vidět kompilátorem a představuje vše potřebné pro zkompilování Visual Basic nebo C# programu. **Kompilace** obsahuje sadu zdrojových souborů, které mají být zkompilovány, odkazy na sestavení a možnosti kompilátoru. Důvody týkající se významu kódu můžete získat pomocí všech dalších informací v tomto kontextu. <xref:Microsoft.CodeAnalysis.Compilation> umožňuje najít **symboly** – entity, jako jsou typy, obory názvů, členy a proměnné, které názvy a další výrazy odkazují na. Proces přidružení názvů a výrazů se **symboly** se nazývá **vazba**.

Stejně jako <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> je abstraktní třída s deriváty specifickými pro jazyk. Při vytváření instance kompilace musíte vyvolat metodu objektu pro vytváření na třídě <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>).

## <a name="querying-symbols"></a>Dotazování na symboly

V tomto kurzu se podíváte na Hello World program znovu. Tentokrát zadáte dotaz na symboly v programu, abyste pochopili, jaké typy symbolů představuje. Budete dotazováni na typy v oboru názvů a naučíte se najít metody dostupné pro typ.

Dokončený kód pro tuto ukázku najdete v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy stromové struktury syntaxe používají dědičnost k popisu různých syntaktických prvků, které jsou platné v různých umístěních v programu. Použití těchto rozhraní API často znamená přetypování vlastností nebo členů kolekce na konkrétní odvozené typy. V následujících příkladech je přiřazení a přetypování samostatné příkazy pomocí explicitně typových proměnných. Můžete si přečíst kód a zobrazit návratové typy rozhraní API a typ modulu runtime vrácených objektů. V praxi je obvyklejší používat implicitně typové proměnné a spoléhat na názvy rozhraní API k popisu typu testovaných objektů.

Vytvořit nový C# projekt **Nástroje pro analýzu samostatného kódu** :

* V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt** . zobrazí se dialogové okno Nový projekt.
* V části **rozšiřitelnost** **vizuálního C#**  > vyberte **Nástroj pro analýzu**samostatného kódu.
* Pojmenujte projekt "**SemanticQuickStart**" a klikněte na tlačítko OK.

Chystáte se analyzovat základní "Hello World!" program byl zobrazen výše.
Do `Program` třídy přidejte text pro Hello World program jako konstantu:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dále přidejte následující kód, který sestaví strom syntaxe pro text kódu v konstantě `programText`.  Do metody `Main` přidejte následující řádek:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

V dalším kroku Sestavte <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> ze stromu, který jste už vytvořili. Ukázka "Hello World" spoléhá na typy <xref:System.String> a <xref:System.Console>. Musíte odkazovat na sestavení, které deklaruje tyto dva typy v kompilaci. Přidejte následující řádek do metody `Main` pro vytvoření kompilace stromu syntaxe, včetně odkazu na příslušné sestavení:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

Metoda <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> přidá odkazy na kompilaci. Metoda <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> načte sestavení jako odkaz.

## <a name="querying-the-semantic-model"></a>Dotazování sémantického modelu

Jakmile budete mít <xref:Microsoft.CodeAnalysis.Compilation>, můžete požádat o <xref:Microsoft.CodeAnalysis.SemanticModel> pro všechny <xref:Microsoft.CodeAnalysis.SyntaxTree> obsažené v <xref:Microsoft.CodeAnalysis.Compilation>. Sémantický model si můžete představit jako zdroj pro všechny informace, které byste normálně získali z IntelliSense. <xref:Microsoft.CodeAnalysis.SemanticModel> může odpovídat na otázky, jako je "Jaké názvy jsou v oboru v tomto umístění?", "které členy jsou přístupné z této metody?", "Jaké proměnné jsou použity v tomto bloku textu?" "a" čemu tento název/výraz odkazují na? " Přidáním tohoto příkazu vytvořte sémantický model:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Vazba názvu

<xref:Microsoft.CodeAnalysis.Compilation> vytvoří <xref:Microsoft.CodeAnalysis.SemanticModel> z <xref:Microsoft.CodeAnalysis.SyntaxTree>. Po vytvoření modelu můžete zadat dotaz na první direktivu `using` a načíst informace o symbolech pro `System` oboru názvů. Přidejte tyto dva řádky do metody `Main`, abyste vytvořili sémantický model a načetli symbol pro první příkaz using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Předchozí kód ukazuje, jak vytvořit navázání názvu v první direktivě `using` pro získání <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> pro `System` obor názvů. Předchozí kód také ukazuje použití **modelu syntaxe** k nalezení struktury kódu; použijte **sémantický model** pro pochopení svého významu. **Model syntaxe** vyhledá řetězec `System` v příkazu Using. **Sémantický model** obsahuje všechny informace o typech definovaných v oboru názvů `System`.

Z objektu <xref:Microsoft.CodeAnalysis.SymbolInfo> můžete získat <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> pomocí vlastnosti <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType>. Tato vlastnost vrací symbol, na který tento výraz odkazuje. Pro výrazy, které neodkazují na cokoli (například číselné literály), je tato vlastnost `null`. Pokud <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> není null, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> označuje typ symbolu. V tomto příkladu je vlastnost <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Do metody `Main` přidejte následující kód. Načte symbol pro `System` obor názvů a potom zobrazí všechny podřízené obory názvů deklarované v oboru názvů `System`:

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
> Výstup nezahrnuje každý obor názvů, který je podřízeným oborem názvů `System` oboru názvů. Zobrazuje každý obor názvů, který je k dispozici v této kompilaci, který odkazuje pouze na sestavení, kde je deklarováno `System.String`. V této kompilaci nejsou známy žádné obory názvů deklarované v jiných sestaveních.

### <a name="binding-an-expression"></a>Vazba výrazu

Předchozí kód ukazuje, jak najít symbol pomocí vazby na název. V C# programu existují další výrazy, které mohou být vázány na názvy. K tomu, aby bylo možné tuto funkci předvést, pojďme přistoupit k vazbě na jednoduchý řetězcový literál.

Program "Hello World" obsahuje <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" řetězec zobrazený v konzole.

Najdete "Hello, World!" řetězec vyhledáním jediného řetězcového literálu v programu. Po umístění uzlu syntaxe získáte informace o typu pro tento uzel ze sémantického modelu. Do své `Main` metody přidejte následující kód:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

Struktura <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> obsahuje vlastnost <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType>, která umožňuje přístup k sémantickým informacím o typu literálu. V tomto příkladu je to typ `string`. Přidejte deklaraci, která přiřadí tuto vlastnost místní proměnné:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Pro dokončení tohoto kurzu sestavíme dotaz LINQ, který vytvoří sekvenci všech veřejných metod deklarovaných v typu `string`, který vrací `string`. Tento dotaz je složitý, takže ho sestavíme řádek po řádku a pak ho znovu sestavíte jako jeden dotaz. Zdrojem tohoto dotazu je pořadí všech členů deklarovaných u `string`ho typu:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Tato zdrojová sekvence obsahuje všechny členy, včetně vlastností a polí, a proto ji filtrujte pomocí metody <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> k nalezení prvků, které jsou <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> objekty:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Dále přidejte další filtr, který vrátí pouze ty metody, které jsou veřejné a vracejí `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Vyberte pouze vlastnost název a jedinečné názvy odebráním všech přetížení:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Můžete také vytvořit úplný dotaz pomocí syntaxe dotazu LINQ a pak zobrazit všechny názvy metod v konzole:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Sestavte program a spusťte ho. Měli byste vidět následující výstup:

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
