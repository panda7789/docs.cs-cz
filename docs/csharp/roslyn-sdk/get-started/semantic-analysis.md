---
title: Začínáme se sémantickou analýzou
description: Tento kurz poskytuje přehled práce s sémantickou analýzou pomocí sady SDK kompilátoru .NET.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: a6dcaeeb86acb5c0e1602f01dc5952ffd9d5e3f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240505"
---
# <a name="get-started-with-semantic-analysis"></a>Začínáme se sémantickou analýzou

Tento kurz předpokládá, že jste obeznámeni s rozhraním API syntaxe. Začínáme [s článkem analýzy syntaxe](syntax-analysis.md) poskytuje dostatečný úvod.

V tomto kurzu prozkoumat **symbol** a **vazby API**. Tato úložiště API poskytují informace o _sémantickém významu_ programu. Umožňují vám klást otázky a odpovídat na ně o typech reprezentovaném libovolným symbolem ve vašem programu.

Budete muset nainstalovat **sdk platformy kompilátoru .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Principy kompilací a symbolů

Při další práci s sadou SDK kompilátoru .NET se seznámíte s rozdíly mezi syntaxovým rozhraním API a sémantickým rozhraním API. **Syntaxapi** umožňuje podívat se na _strukturu_ programu. Často však chcete bohatší informace o sémantice nebo _významu_ programu. Zatímco soubor s volným kódem nebo fragment kódu jazyka Nebo Jazyka # může být syntakticky analyzován izolovaně, není smysluplné klást otázky, jako je například "jaký je typ této proměnné" ve vakuu. Význam názvu typu může záviset na odkazech na sestavení, importech oboru názvů nebo jiných souborech kódu. Tyto otázky jsou zodpovězeny pomocí **sémantického rozhraní API**, konkrétně třídy. <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType>

Instance <xref:Microsoft.CodeAnalysis.Compilation> je obdobou jednoho projektu, jak je vidět kompilátoru a představuje vše potřebné ke kompilaci visual basic nebo C# program. **Kompilace** obsahuje sadu zdrojových souborů, které mají být kompilovány, odkazy na sestavení a možnosti kompilátoru. Můžete důvod o významu kódu pomocí všech ostatních informací v tomto kontextu. A <xref:Microsoft.CodeAnalysis.Compilation> umožňuje najít **symboly** - entity, jako jsou typy, obory názvů, členy a proměnné, které názvy a jiné výrazy odkazují. Proces sousto názvů a výrazů se **Binding**nazývá **Binding** .

Stejně jako <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> je abstraktní třída s jazykově specifickými deriváty. Při vytváření instance Kompilace je nutné vyvolat <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> metodu <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>factory ve třídě (nebo).

## <a name="querying-symbols"></a>Dotazování symbolů

V tomto kurzu se znovu podíváte na program "Hello World". Tentokrát dotaz symboly v programu pochopit, jaké typy tyto symboly představují. Dotaz na typy v oboru názvů a naučit se najít metody, které jsou k dispozici na typu.

Hotový kód pro tuto ukázku najdete v [našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy stromů syntaxe používají dědičnost k popisu různých prvků syntaxe, které jsou platné na různých místech v programu. Použití těchto rozhraní API často znamená, že vlastnosti přetypování nebo členy kolekce na konkrétní odvozené typy. V následujících příkladech jsou přiřazení a přetypování samostatné příkazy, které používají explicitně zadané proměnné. Můžete si přečíst kód zobrazíte návratové typy rozhraní API a typ runtime vrácených objektů. V praxi je běžnější používat implicitně zadané proměnné a spoléhat se na názvy rozhraní API k popisu typu zkoumaných objektů.

Vytvořte nový projekt **nástroje pro analýzu samostatného kódu** jazyka C#:

* V Sadě Visual Studio zvolte **Soubor** > **nový** > **projekt,** abyste zobrazili dialogové okno Nový projekt.
* V **části Visual C#** > **Rozšiřitelnost**zvolte **Nástroj pro analýzu samostatného kódu**.
* Pojmenujte projekt **"SémanticQuickStart**" a klepněte na tlačítko OK.

Budete analyzovat základní "Hello World!" program zobrazen dříve.
Přidejte text programu Hello World jako `Program` konstantu ve své třídě:

[!code-csharp[Declare the program test](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Dále přidejte následující kód k vytvoření stromu syntaxe pro text kódu v konstantě. `programText`  Do metody přidejte `Main` následující řádek:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Dále vytvořte <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> ze stromu, který jste již vytvořili. Ukázka "Hello World" závisí <xref:System.String> <xref:System.Console> na a typy. Musíte odkazovat na sestavení, které deklaruje tyto dva typy ve vaší kompilaci. Přidejte do metody `Main` následující řádek a vytvořte kompilaci stromu syntaxe, včetně odkazu na příslušné sestavení:

[!code-csharp[Create the compilation](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

Metoda <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> přidá odkazy na kompilaci. Metoda <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> načte sestavení jako odkaz.

## <a name="querying-the-semantic-model"></a>Dotazování na sémantický model

Jakmile budete <xref:Microsoft.CodeAnalysis.Compilation> mít, můžete požádat o <xref:Microsoft.CodeAnalysis.SemanticModel> pro všechny <xref:Microsoft.CodeAnalysis.SyntaxTree> obsažené v tom <xref:Microsoft.CodeAnalysis.Compilation>. Můžete si myslet, sémantický model jako zdroj pro všechny informace, které by normálně získat z intellisense. A <xref:Microsoft.CodeAnalysis.SemanticModel> můžete odpovědět na otázky jako "Jaké názvy jsou v oboru v tomto umístění?", "Jaké členy jsou přístupné z této metody?", "Jaké proměnné se používají v tomto bloku textu?", a "Co tento název/výraz odkazuje?" Přidejte tento příkaz k vytvoření sémantického modelu:

[!code-csharp[Create the semantic model](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Vazba názvu

Vytvoří <xref:Microsoft.CodeAnalysis.Compilation> <xref:Microsoft.CodeAnalysis.SemanticModel> z <xref:Microsoft.CodeAnalysis.SyntaxTree>. Po vytvoření modelu, můžete dotaz na `using` něj najít první direktivu a načíst informace o symbolu `System` pro obor názvů. Přidejte tyto dva `Main` řádky do metody k vytvoření sémantického modelu a načíst symbol pro první příkaz using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Předchozí kód ukazuje, jak svázat název `using` v první <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> direktivě načíst pro obor `System` názvů. Předchozí kód také ukazuje, že pomocí **modelu syntaxe** najít strukturu kódu; použijete **sémantický model** k pochopení jeho významu. Model **syntaxe** najde `System` řetězec v příkazu using. **Sémantický model** má všechny informace o `System` typech definovaných v oboru názvů.

Z <xref:Microsoft.CodeAnalysis.SymbolInfo> objektu můžete <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> získat <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> pomocí vlastnosti. Tato vlastnost vrátí symbol, na který tento výraz odkazuje. Pro výrazy, které neodkazují na nic (například číselné `null`literály) tato vlastnost je . Pokud <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> není null, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> označuje typ symbolu. V tomto příkladu <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> je <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>vlastnost . Přidejte do `Main` metody následující kód. Načte symbol pro `System` obor názvů a potom zobrazí všechny podřízené obory názvů deklarované v oboru `System` názvů:

[!code-csharp[Display all the child namespaces](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Spusťte program a měli byste vidět následující výstup:

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
> Výstup nezahrnuje každý obor názvů, který je `System` podřízeným oborem názvů oboru názvů. Zobrazí každý obor názvů, který je přítomen v této `System.String` kompilaci, která odkazuje pouze na sestavení, kde je deklarována. Všechny obory názvů deklarované v jiných sestaveních nejsou této kompilaci známy.

### <a name="binding-an-expression"></a>Vazba výrazu

Předchozí kód ukazuje, jak najít symbol vazbou na název. Existují jiné výrazy v programu Jazyka C#, které mohou být vázány, které nejsou názvy. Chcete-li demonstrovat tuto schopnost, pojďme přístup vazby na jednoduchý řetězec literál.

Program "Hello World" <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>obsahuje program " Hello, World!" zobrazený řetězec na konzoli.

Najděte "Ahoj, světe!" řetězce vyhledáním literálu jednoho řetězce v programu. Poté, co jste lokalizovali uzel syntaxe, získejte informace o typu pro tento uzel ze sémantického modelu. Do metody přidejte `Main` následující kód:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Struktura obsahuje <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> vlastnost, která umožňuje přístup k sémantické informace o typu literálu. V tomto příkladu `string` je to typ. Přidejte deklaraci, která přiřadí tuto vlastnost místní proměnné:

[!code-csharp[Find the semantic information about the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Chcete-li dokončit tento kurz, pojďme vytvořit dotaz LINQ, který vytvoří `string` posloupnost `string`všech veřejných metod deklarovaných na typu, které vracejí . Tento dotaz získá složité, takže pojďme jej vytvořit řádek po řádku, pak rekonstruovat jako jeden dotaz. Zdrojem pro tento dotaz je posloupnost `string` všech členů deklarovaných na typu:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Tato zdrojová sekvence obsahuje všechny členy, včetně vlastností a polí, proto je můžete filtrovat pomocí <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> metody k vyhledání prvků, které jsou <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> objekty:

[!code-csharp[Filter the sequence to only methods](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Dále přidejte další filtr, který vrátí pouze `string`ty metody, které jsou veřejné, a vraťte :

[!code-csharp[Filter on return type and accessibility](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Vyberte pouze vlastnost name a pouze odlišné názvy odebráním všech přetížení:

[!code-csharp[find the distinct names.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Můžete také vytvořit úplný dotaz pomocí syntaxe dotazu LINQ a potom zobrazit všechny názvy metod v konzole:

[!code-csharp[build and display the results of this query.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Sestavte a spusťte program. Měl by se zobrazit následující výstup:

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
