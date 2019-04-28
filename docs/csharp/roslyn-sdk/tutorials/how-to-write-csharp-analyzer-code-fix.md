---
title: 'Kurz: Zápis první opravu analyzátoru a kódu'
description: Tento kurz obsahuje podrobné pokyny k sestavení analyzátor a oprava kódu pomocí sady SDK kompilátoru .NET (Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 7e3d1ac3a1ef692a1b7f1980fd00f95b04a8d047
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706738"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Kurz: Zápis první opravu analyzátoru a kódu

Sada SDK platformy kompilátoru .NET poskytuje nástroje, které potřebujete k vytvoření vlastní upozornění tento cíl C# nebo kódu jazyka Visual Basic. Vaše **analyzátor** obsahuje kód, který rozpozná porušení pravidla. Vaše **opravu kódu** obsahuje kód, který opraví porušení zásady. Pravidla, která můžete implementovat můžou být čímkoli od strukturu kódu na kódování styl konvence pojmenování a další. .NET Compiler Platform poskytuje rozhraní pro spuštění analýzy jako vývojáři psaní kódu a funkce všech rozhraní Visual Studia pro opravu kódu: zobrazující podtržení vlnovkou v editoru Visual Studio seznamu chyb, vytváření "žárovky" vyplnění návrhy a zobrazuje bohaté možnosti ve verzi preview návrhy jejich oprav.

V tomto kurzu prozkoumáte vytváření **analyzátor** a je v doprovodné **opravu kódu** pomocí rozhraní Roslyn API. Analyzátor je způsob, jak provést analýzu zdrojového kódu a ohlásit problém pro uživatele. Analyzátor Volitelně můžete zadat taky opravy kódu, který představuje úpravy zdrojového kódu uživatele. Tento kurz vytvoří analyzátor, který hledá místní deklarace proměnných, které mohou být deklarovány pomocí `const` modifikátor ale nejsou. Související opravu kódu upravuje tyto deklarace pro přidání `const` modifikátor.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017](https://www.visualstudio.com/downloads)

Budete muset nainstalovat **sada SDK platformy kompilátoru .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Existuje několik kroků k vytvoření a ověření vašich analyzer:

1. Vytvořte řešení.
1. Registrace analyzátoru název a popis.
1. Sestavy analyzátoru upozornění a doporučení.
1. Implementujte opravu kódu tak, aby přijímal doporučení.
1. Vylepšení analýzy prostřednictvím testů jednotek.

## <a name="explore-the-analyzer-template"></a>Prozkoumání šablony analyzátoru

Vaše analyzátor ohlásí uživateli žádné místní deklarace proměnných, které lze převést na lokální konstanty. Zvažte například následující kód:

```csharp
int x = 0;
Console.WriteLine(x);
```

Ve výše uvedeném kódu `x` přiřazena konstantní hodnotou a se nikdy nemění. Mohou být deklarovány pomocí `const` modifikátor:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Součástí analýzy k určení, zda proměnné může být změněna na konstantní vyžadující syntaktické analýzy, konstantní analýzy inicializačního výrazu a analýzy datového toku k zajištění, že proměnná je nikdy zapsána do. Na platformě kompilátoru .NET poskytuje rozhraní API, která usnadňují provádění této analýzy. Prvním krokem je vytvoření nového jazyka C# **analyzátor s opravu kódu** projektu.

* V sadě Visual Studio, zvolte **soubor > Nový > projekt...**  zobrazíte dialogové okno Nový projekt.
* V části **Visual C# > rozšíření**, zvolte **Analyzátor se oprava kódu (.NET Standard)**.
* Pojmenujte svůj projekt "**MakeConst**" a klikněte na tlačítko OK.

Vytvoří analyzátor s šablonou opravu kódu tři projekty: jeden obsahuje analyzer a oprava kódu, projekt testování částí je druhý a třetí je projekt VSIX. Výchozí spouštěný projekt je projekt VSIX. Stisknutím klávesy **F5** ke spuštění projektu VSIX. Otevře se druhá instance sady Visual Studio, který byl načten nový analyzátor.

> [!TIP]
> Při spuštění vaší analyzer spusťte druhé kopie sady Visual Studio. Tato druhá kopie využívá k ukládání nastavení různých podregistru. Která umožňuje rozlišovat visual nastavení v dvě kopie sady Visual Studio. Můžete si vybrat jiný motiv pro experimentální spuštění sady Visual Studio. Kromě toho není roaming nastavení nebo přihlášení k Visual Studio spustit účtu pomocí experimentální instanci sady Visual Studio. Která udržuje jiné nastavení.

Ve druhé instanci aplikace Visual Studio, který jste právě spustili vytvořte nový projekt konzolové aplikace jazyka C# (.NET Core nebo projekt se rozhraní .NET Framework pracovat – analyzátory práce na úrovni zdroje.) Najeďte myší token s podtržení vlnovkou a zobrazí se text upozornění poskytované analyzátor.

Šablona vytvoří analyzátor, který bude hlásit upozornění na deklaraci typu, kde název typu obsahuje malá písmena, jak je znázorněno na následujícím obrázku:

![Analyzátor reporting upozornění](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Šablona také nabízí opravu kódu, který změní libovolný typ název obsahuje malá písmena na velká písmena. Kliknutím na žárovku, zobrazí se upozornění zobrazíte navrhované změny. Přijetí aktualizací navrhované změny, název typu a všechny odkazy na tento typ v řešení. Teď, když už víte, počáteční analyzátor v akci, zavřete druhou instanci aplikace Visual Studio a vraťte se do projektu analyzátor.

Není nutné ke spuštění druhé kopie sady Visual Studio a vytvořte nový kód pro testování každé změně ve vaší analyzátor. Šablona vytvoří projekt testu jednotek také za vás. Tento projekt obsahuje dva testy. `TestMethod1` ukazuje typický formát test, který analyzuje kódu bez aktivace diagnostiky. `TestMethod2` ukazuje formátu test, který se spustí Diagnostika a poté použije opravu navrhované kódu. Během vytváření analyzer a oprava kódu bude psaní testů pro různý kód struktury ověřit svou práci. Testy jednotek pro analyzátory jsou mnohem rychleji než při testování interaktivně pomocí sady Visual Studio.

> [!TIP]
> Analyzátor testování jednotek je skvělý nástroj, když víte, jaký kód konstrukce by měl a nesmí aktivovat váš analyzátor. Načítají se vaše analyzátor v jiné kopii sady Visual Studio je skvělý nástroj pro zkoumání a najít konstrukce, které vás nemusí mít myslet na ještě.

## <a name="create-analyzer-registrations"></a>Vytvoření registrace analyzátoru

Šablona vytvoří počáteční `DiagnosticAnalyzer` třídy v **MakeConstAnalyzer.cs** souboru. Tento počáteční analyzátor ukazuje dvě důležité vlastnosti každé analyzátor.

* Musíte zadat každou diagnostického analyzátoru `[DiagnosticAnalyzer]` atribut, který popisuje pracuje na jazyk.
* Každý diagnostického analyzátoru musí být odvozen od <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> třídy.

Šablona také ukazuje základní funkce, které jsou součástí žádné analyzer:

1. Zaregistrujte akce. Akce představují změny kódu, které by měly aktivovat váš analyzátor pro zkoumání kódu pro porušení. Když Visual Studio zjistí úpravy kódu, které odpovídají registrované akce, volá metodu v analyzéru registrovaný.
1. Vytvoření diagnostiky. Když vaše analyzátor zjistí narušení, vytvoří objekt diagnostické, využívající Visual Studio na upozornění pro uživatele porušení zásady.

Zaregistrovat akce v přepsání metody <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metoda. V tomto kurzu budete navštívíte **syntaxe uzly** hledá místní deklarace a zjistili, který z nich jsou konstantní hodnoty. Pokud deklarace může být konstantní, bude vaše analyzátor vytvořit a nahlaste diagnostiku.

Prvním krokem je aktualizace konstanty registrace a `Initialize` metoda tak tyto konstanty označení vaší analyzátor "Ujistěte se, Const". Většina řetězcové konstanty jsou definovány v souboru prostředků řetězce. Měli byste postupovat podle této normy pro jednodušší lokalizace. Otevřít **Resources.resx** souboru **MakeConst** analyzátor projektu. Zobrazí se editor prostředků. Aktualizace řetězcové prostředky následujícím způsobem:

* Změna `AnalyzerTitle` na "Proměnná může být změněna na konstantní".
* Změna `AnalyzerMessageFormat` do "Může být změněna na konstantní".
* Změna `AnalyzerDescription` aby "konstanty".

Změnit také, **modifikátor přístupu** rozevíracího seznamu `public`. Který usnadňuje použití tyto konstanty při testech jednotek. Jakmile budete hotovi, editor prostředků by měla vypadat jako postupujte podle obrázku je vidět:

![Aktualizovat prostředky řetězců](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Zbývající změny jsou v souboru analyzátor. Otevřít **MakeConstAnalyzer.cs** v sadě Visual Studio. Změňte registrované akce z jednoho, který funguje na symboly, který funguje na syntaxi. V `MakeConstAnalyzerAnalyzer.Initialize` metoda, vyhledejte řádek, který registruje akce na symboly:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Nahraďte ho následující řádek:

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Po této změně můžete odstranit `AnalyzeSymbol` metody. Tento analyzátor kontroluje <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, nikoli <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> příkazy. Všimněte si, že `AnalyzeNode` má červenou vlnovkou pod ním. Kód, který jste právě přidali odkazy `AnalyzeNode` metodu, která nebyla deklarována. Deklarujte metody pomocí následujícího kódu:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Změnit `Category` "Využití" v **MakeConstAnalyzer.cs** jak je znázorněno v následujícím kódu:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Najít místní deklarace, které by mohly být const

Je čas zápisu první verzi `AnalyzeNode` metody. Měl by vypadat pro jeden místní deklarace, které by mohly `const` , ale není k dispozici, jako v následujícím kódu:

```csharp
int x = 0;
Console.WriteLine(x);
```

Prvním krokem je najít místní deklarace. Přidejte následující kód, který `AnalyzeNode` v **MakeConstAnalyzer.cs**:

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Toto přetypování vždy úspěšná, protože vaše analyzátor zaregistrovat pro změny místní deklarace a jenom místní deklarace. Žádný jiný typ uzlu aktivuje volání dané k vaší `AnalyzeNode` metody. Dále zkontrolujte deklaraci pro všechny `const` modifikátory. Pokud je najít, vrátí okamžitě. Následující kód vyhledá všechny `const` modifikátory u místní deklarace:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

A konečně, je potřeba zkontrolovat, že může být proměnná `const`. To znamená, že provedení, ji není nikdy přiřazeno po inicializaci.

Budete provádět některé pomocí sémantické analýzy <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>. Můžete použít `context` argument k určení, zda mohou být vytvořeny deklarace lokální proměnné `const`. A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> představuje všech sémantických informací v jediném souboru. Můžete další informace najdete v článku určeného po [sémantickým modelům](../work-with-semantics.md). Budete používat <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> provádět analýzy toku dat v příkazu místní deklarace. Potom použijte výsledky této analýzy toku dat k zajištění, že místní proměnná není zapsán s novou hodnotou někde jinde. Volání <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodu rozšíření k získání <xref:Microsoft.CodeAnalysis.ILocalSymbol> pro proměnnou a zkontrolujte, že se nenachází se <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> kolekce dat tok analýzy. Přidejte následující kód do konce `AnalyzeNode` metody:

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

Kód, který právě přidali zajistí, že proměnné není upraven a proto nelze realizovat `const`. Je čas vyvolání diagnostiky. Přidejte následující kód jako poslední řádek v `AnalyzeNode`:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Průběh můžete zkontrolovat stisknutím kombinace kláves **F5** ke spouštění vaší analyzer. Můžete načíst konzolové aplikace, kterou jste vytvořili dříve a pak přidejte následující kód testu:

```csharp
int x = 0;
Console.WriteLine(x);
```

Žárovky by se měla objevit a vaše analyzátor ohlaste diagnostiku. Ale žárovky stále používá vygenerovanou šablonu opravu kódu a zjistíte, že ji můžete nastavit na velká písmena. V další části vysvětluje, jak napsat kód opravy.

## <a name="write-the-code-fix"></a>Zápis opravy kódu

Analyzátor můžete zadat jednu nebo více oprav kódu. Oprava kódu definuje úpravy, které řeší nahlášeného problému. Pro analyzátor, který jste vytvořili mohli zajistit opravu kódu, který se vkládá const – klíčové slovo:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Uživatel vybere z žárovky uživatelského rozhraní v editoru a sady Visual Studio změny kódu.

Otevřít **MakeConstCodeFixProvider.cs** soubory přidané pomocí šablony.  Tato oprava kódu je již svázanou s ID diagnostiky vytvářených diagnostického analyzátoru, ale ještě neimplementuje transformace správný kód. Nejdřív byste měli odebrat některé kód šablony. Změna názvu řetězec "Zkontrolujte konstanta":

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

V dalším kroku odstranit `MakeUppercaseAsync` metody. To už neplatí.

Všechny opravy kódu jsou odvozeny z <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>. Všechny přepsat <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> hlášení opravy kódu k dispozici. V `RegisterCodeFixesAsync`, změňte typ uzlu předchůdce hledáte k <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tak, aby odpovídaly diagnostiky:

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

V dalším kroku změňte poslední řádek k registraci opravu kódu. Jste kód opravili správně vytvoří nový dokument, který je výsledkem přidání `const` modifikátor na existující deklaraci:

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Můžete si všimnout červenou vlnovkou v kódu, kterou jste právě přidali na symbol `MakeConstAsync`. Přidat deklaraci `MakeConstAsync` , jako je následující kód:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Vaše nová `MakeConstAsync` metoda provede transformaci <xref:Microsoft.CodeAnalysis.Document> představující uživatele zdrojový soubor do nového <xref:Microsoft.CodeAnalysis.Document> , která teď obsahuje `const` deklarace.

Vytvoření nového `const` – klíčové slovo token pro vložení do přední části příkazu deklarace. Dejte pozor, abyste nejdřív odebrat všechny úvodní triviální prvek z první token příkazu deklarace a připojte ji k `const` token. Přidejte následující kód, který `MakeConstAsync` metody:

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

V dalším kroku přidejte `const` token deklarace pomocí následujícího kódu:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

V dalším kroku naformátujte nové deklarace tak, aby odpovídaly pravidla formátování C#. Lepší prostředí pro formátování provedené změny tak, aby odpovídaly existujícího kódu vytvoří. Přidejte následující příkaz ihned po existující kód:

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Nový obor názvů se vyžaduje pro tento kód. Přidejte následující `using` příkaz do horní části souboru:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Posledním krokem je provést úpravy. K tomuto procesu tři kroky:

1. Získejte popisovač pro k existujícímu dokumentu.
1. Vytvoření nového dokumentu tak, že nahradíte existující deklarace s novou deklaraci.
1. Vrátí nový dokument.

Přidejte následující kód do konce `MakeConstAsync` metody:

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Jste kód opravili správně kódu připravená k vyzkoušení.  Stisknutím klávesy F5 spusťte analyzátor projektu ve druhé instanci aplikace Visual Studio. Ve druhé instanci aplikace Visual Studio vytvořte nový projekt konzolové aplikace jazyka C# a přidejte několik místní deklarace proměnných inicializována s konstantní hodnoty do metody Main. Uvidíte, že jsou hlášeny jako varování, jak je uvedeno níže.

![Může být const upozornění](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Jsme udělali spoustu průběh. Existují podtržení vlnovkou v rámci deklarace, které mohou být provedeny `const`. Ale bude stále na práci není. To funguje správně, pokud přidáte `const` deklaracích počínaje `i`, pak `j` a nakonec `k`. Ale pokud přidáte `const` modifikátor v jiném pořadí, počínaje `k`, vaše analyzátor vytvoří chyby: `k` nejde použít deklaraci `const`, není-li `i` a `j` jsou již `const`. Máte s nimi dělat další analýzy k zajištění, že zpracovávat různé způsoby proměnné mohou být deklarovány a inicializovány.

## <a name="build-data-driven-tests"></a>Vytvořit testy řízené daty

Analyzátoru a kódu opravit práce v jednoduchém případě jedné deklarace, které můžete provést const. Existuje mnoho příkazy možné deklarace, kde je tato implementace chyby. Při práci s knihovnou testovací jednotky zapsány pomocí šablony budete řešit tyto případy. Je mnohem rychlejší než opakovaného otevírání druhé kopie sady Visual Studio.

Otevřít **MakeConstUnitTests.cs** souboru v projektu testování částí. Šablona vytvoří dva testy, které následují dvě běžné vzory pro analyzátor a testování částí opravu kódu. `TestMethod1` ukazuje, že vzor pro test, který zajišťuje, analyzátor nebude hlásit Diagnostika v případě, že by se neměly. `TestMethod2` ukazuje vzor pro vytváření sestav Diagnostika a spuštěný opravu kódu.

Kód pro téměř každý test pro vaše analyzátor používá jednu z těchto dvou vzorků. Pro první krok můžete tyto testy Přepracujte jako testy řízené daty. Pak bude možné snadno vytvořit nové testy tak, že přidáte nový řetězec konstanty k reprezentaci různých testovací vstupy.

Z důvodu efektivity prvním krokem je lze refaktorovat dva testy do testy řízené daty. Potom stačí definovat několik řetězcové konstanty pro každý nový test. Při vaší refaktoring přejmenování obě metody lepší názvy. Nahraďte `TestMethod1` je vyvolána s tímto testem, který zajišťuje žádné diagnostiky:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Nový řádek dat pro tento test můžete vytvořit tak, že definujete jakékoli fragment kódu, který by nemělo způsobit vaší diagnostiky pro aktivaci upozornění. Toto přetížení `VerifyCSharpDiagnostic` úspěšný, pokud neexistují žádné diagnostiky pro fragment kódu zdroje.

V dalším kroku nahraďte `TestMethod2` tento test, který zajišťuje diagnostiky se vyvolá, a oprava kódu u zdroje fragment kódu:

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

Předchozí kód také provedli několik změn kódu, který sestaví očekávaný výsledek diagnostiky. Používá veřejné konstanty zaregistrovaný v `MakeConst` analyzátor. Kromě toho používá dva řetězcové konstanty pro zdroje vstupu a oprava. Přidejte následující konstanty na řetězec `UnitTest` třídy:

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Spusťte tyto dva testy, abyste měli jistotu, že bude úspěšné. V sadě Visual Studio, otevřete **Průzkumník testů** tak, že vyberete **testovací** > **Windows** > **Průzkumník testů**.  Stiskněte klávesu **spustit všechny** odkaz.

## <a name="create-tests-for-valid-declarations"></a>Vytvořit testy pro platné deklarace

Jako obecné pravidlo má analyzátory ukončit co nejrychleji, provádění minimálním úsilím. Visual Studio volání analyzátory zaregistrovaný jako uživatelského kódu pro úpravy. Schopnost reagovat je klíčovým požadavkem. Existuje několik testovacích případů pro kód, který by neměl zvýšit vaši diagnostiky. Vaše analyzátor již zpracovává jeden z těchto testů, případ, kdy se po jejich inicializaci přiřazenou proměnnou. Přidejte následující konstantu řetězce do testů pro reprezentaci případ:

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Pak přidejte řádek dat pro tento test, jak je znázorněno v následujícím fragmentu kódu:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Tento test úspěšný také. V dalším kroku přidejte konstanty pro podmínky, které nebyly dosud zpracovány:

* Deklarace, které jsou již `const`, protože jsou již const:

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

* Deklarace, které mají žádný inicializátor, protože neexistuje žádná hodnota používat:

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

* Deklarace, kde inicializátor není konstantní, protože nemohou být konstanty z doby kompilace:

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

Může být ještě složitější, protože C# umožňuje více deklarací jako jeden příkaz. Vezměte v úvahu následující řetězcová konstanta testovacího případu:

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Proměnná `i` provádět – konstanta, ale proměnná `j` nelze. Proto tento příkaz nelze nastavit jako deklarace const. Přidat `DataRow` deklarace pro tyto testy:

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Znovu spusťte testy a zobrazí se vám tyto nové testovací případy selhání.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Aktualizujte vaše analyzátor ignorovat správné deklarace

V analyzéru je potřeba určitá vylepšení `AnalyzeNode` metoda odfiltrovat kód, který splňuje tyto podmínky. Všechny související podmínky jsou podobné změny budou opravit tyto podmínky. Proveďte následující změny `AnalyzeNode`:

* Sémantická analýza prozkoumat jedné deklarace proměnné. Tento kód musí být v `foreach` smyčku, která zkontroluje všechny proměnné deklarované ve stejném příkazu.
* Každou deklaraci proměnných musí mít inicializátor.
* Inicializátor každé deklarované proměnné musí být konstanta za kompilace.

Ve vaší `AnalyzeNode` metoda, nahraďte původní sémantické analýzy:

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

Pomocí následujícího fragmentu kódu:

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

První `foreach` smyčky zkontroluje každou deklaraci proměnné pomocí syntaktické analýzy. První kontrola zaručuje, že má proměnná inicializátor. Druhý kontrola zaručuje, že inicializátoru je konstanta. Druhý smyčka má původní sémantické analýzy. Sémantické kontroly jsou v samostatné smyčky, protože má větší vliv na výkon. Znovu spusťte testy a měli byste vidět jejich předávání.

## <a name="add-the-final-polish"></a>Přidejte poslední polština

Už jste téměř hotovi. Existuje několik další podmínky pro vaše analyzátor pro zpracování. Visual Studio volá analyzátory, když uživatel píše kód. Je často případ, který vaše analyzátor bude volána pro kód, který nepodporuje kompilaci. Diagnostického analyzátoru `AnalyzeNode` metoda nekontroluje, jestli je konstantní hodnoty lze převést na typ proměnné. Ano, aktuální implementace využívá elastic převést nesprávná deklarace například int i = "abc" "na lokální konstanta. Přidáte konstantu zdrojové řetězce pro tuto podmínku:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Kromě toho nejsou správně zpracovány typy odkazů. Pouze konstantní hodnota povolená pro typ odkazu je `null`, s výjimkou v tomto případě <xref:System.String?displayProperty=nameWIthType>, což umožňuje řetězcové literály. Jinými slovy `const string s = "abc"` je právní, ale `const object s = "abc"` není. Tento fragment kódu ověří tuto podmínku:

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Bude důkladné, budete muset přidat další test, abyste měli jistotu, že můžete vytvořit deklaraci konstanty pro řetězec. Následující fragment kódu definuje kód, který vyvolá diagnostickou i kód po použití opravy:

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Nakonec pokud je proměnná deklarována s `var` – klíčové slovo, nemá špatného opravu kódu a generuje `const var` prohlášení, což není podporováno v jazyce C#. Chcete-li vyřešit tuto chybu, musíte nahradit opravu kódu `var` – klíčové slovo s názvem odvozený typ:

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Tyto změny aktualizují data řádku deklarace pro oba testy. Následující kód ukazuje tyto testy se všechny atributy řádků dat:

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Naštěstí všechny výše uvedené chyby se dají řešit pomocí stejné techniky, které právě jste se dozvěděli.

Chcete-li oprava první chyby, nejdřív otevřete **DiagnosticAnalyzer.cs** a vyhledejte smyčky foreach, kde každý z místní deklarace inicializátory jsou zkontrolovány Ujistěte se, že jsou přiřazení konstantní hodnoty. Okamžitě _před_ první smyčka foreach, volání `context.SemanticModel.GetTypeInfo()` načíst podrobnosti o deklarovaný typ lokální deklarace:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Potom v rámci vaší `foreach` opakovat, zkontrolujte každý inicializační výraz, ujistěte se, že je lze převést na typ proměnné. Přidejte následující kontroly až se ujistíte, že inicializátoru je konstanta:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Další změně staví na poslední z nich. Před uzavírací složenou závorku prvního foreach smyčky, přidejte následující kód pro kontrolu typu místní deklarace při konstanty je řetězec nebo hodnota null.

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

Je nutné napsat kód o něco více ve zprostředkovateli opravu kódu k nahrazení var' – klíčové slovo s názvem správného typu. Vraťte se na **CodeFixProvider.cs**. Kód, který přidáte provede následující kroky:

* Zkontrolujte, jestli je deklarace `var` deklarace, a pokud je:
* Vytvoření nového typu odvozeného typu.
* Ujistěte se, že deklarace typu není alias. Pokud ano, je možné deklarovat `const var`.
* Ujistěte se, že `var` není název typu v rámci tohoto programu. (Pokud ano, `const var` je platný).
* Zjednodušení úplný název typu

Že zdá se, že velké množství kódu. Není. Nahraďte řádek, který deklaruje a inicializuje `newLocal` následujícím kódem. Prochází hned po inicializaci `newModifiers`:

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Bude nutné, aby vám ho přidal `using` příkaz k použití <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> typu:

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Spuštění testů a bude by všechny úspěšné. Spuštěním na dokončení analyzátor Blahopřání sami. Načíst, stiskněte Ctrl + F5 ke spuštění projektu analyzátor v druhé instance sady Visual Studio s rozšířením Roslyn ve verzi Preview.

* Ve druhé instanci aplikace Visual Studio vytvořte nový projekt konzolové aplikace jazyka C# a přidejte `int x = "abc";` do metody Main. Díky první oprava chyby bez upozornění by se měly hlásit pro deklarace lokální proměnné (i když dochází k chybě kompilátoru podle očekávání).
* V dalším kroku přidejte `object s = "abc";` do metody Main. Z důvodu druhý oprava chyby by se měly hlásit bez upozornění.
* Nakonec přidejte další místní proměnná, která používá `var` – klíčové slovo. Uvidíte, že upozornění je hlášeno a návrh se zobrazí pod vlevo.
* Přesune blikající kurzor editoru přes podtržení vlnovkou a stiskněte klávesu Ctrl +. Chcete-li zobrazit opravu navrhované kódu. Po výběru kód opravit, Všimněte si, že var' – klíčové slovo nyní správně zpracovaly.

Nakonec přidejte následující kód:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Po provedení těchto změn získat červenou vlnovkou jenom na prvních dvou proměnných. Přidat `const` zároveň `i` a `j`, a získat nové upozornění `k` vzhledem k tomu, že teď může být `const`.

Blahopřejeme! Vytvořili jste své první rozšíření .NET Compiler Platform, který provádí analýzu kódu na průběžné rozpoznat potíže a nabízí rychlé opravy na opravu. Na cestě když jste se naučili řadu kódu rozhraní API, která jsou součástí sady SDK platformy kompilátoru .NET (rozhraní Roslyn API). Můžete zkontrolovat práce proti [úplnou vzorovou](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) v našem úložišti GitHub s ukázkami. Nebo si můžete stáhnout [soubor zip dokončení projektu](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)

## <a name="other-resources"></a>Další zdroje

- [Začínáme s analýzou syntaxe](../get-started/syntax-analysis.md)
- [Začínáme s sémantická analýza](../get-started/semantic-analysis.md)
