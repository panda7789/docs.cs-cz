---
title: 'Kurz: vytvoření prvního analyzátoru a opravy kódu'
description: V tomto kurzu najdete podrobné pokyny k sestavení analyzátoru a opravy kódu pomocí sady .NET Compiler SDK (rozhraní Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: f6fc21c010f9b5fcd5e709ef822639c020a7c93b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240547"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Kurz: vytvoření prvního analyzátoru a opravy kódu

Sada .NET Compiler Platform SDK poskytuje nástroje, které potřebujete k vytváření vlastních upozornění, která C# cílí na nebo Visual Basic kódu. Váš **analyzátor** obsahuje kód, který rozpoznává porušení vašeho pravidla. **Oprava kódu** obsahuje kód, který vyřeší porušení. Pravidla, která implementujete, může být cokoli od struktury kódu až po kódování stylu a vytváření názvů. .NET Compiler Platform poskytuje rozhraní pro spouštění analýzy, protože vývojáři píší kód a všechny funkce uživatelského rozhraní sady Visual Studio pro úpravu kódu: zobrazení vlnovek v editoru, vyplnění sady Visual Studio Seznam chyb a vytvoření "žárovky". návrhy a zobrazují bohatou verzi Preview navrhovaných oprav.

V tomto kurzu se seznámíte s vytvořením **analyzátoru** a s doprovodnou **opravou kódu** pomocí rozhraní API Roslyn. Analyzátor je způsob, jak provádět analýzu zdrojového kódu a nahlásit problém uživateli. V případě potřeby může analyzátor také poskytnout opravu kódu, která představuje úpravu zdrojového kódu uživatele. V tomto kurzu se vytvoří analyzátor, který najde deklarace místních proměnných, které by mohly být deklarované pomocí modifikátoru `const`, ale ne. Oprava doprovodného kódu upraví tyto deklarace a přidá modifikátor `const`.

## <a name="prerequisites"></a>Předpoklady

- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

**.NET COMPILER Platform SDK** bude nutné nainstalovat pomocí instalační program pro Visual Studio:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Existuje několik kroků k vytvoření a ověření analyzátoru:

1. Vytvořte řešení.
1. Zaregistrujte název a popis analyzátoru.
1. Upozornění a doporučení analyzátoru sestav.
1. Implementací opravy kódu přijměte doporučení.
1. Zlepšete analýzu prostřednictvím jednotkových testů.

## <a name="explore-the-analyzer-template"></a>Prozkoumat šablonu analyzátoru

Analyzátor hlásí uživateli všechny deklarace místních proměnných, které lze převést na místní konstanty. Zvažte například následující kód:

```csharp
int x = 0;
Console.WriteLine(x);
```

Do výše uvedeného kódu `x` je přiřazena konstantní hodnota a nikdy se nemění. Dá se deklarovat pomocí modifikátoru `const`:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Analýza, která určuje, zda může být proměnná vytvořena, je vyžadována syntaktickou analýzou, konstantní analýzou výrazu inicializátoru a analýzou toku dat, aby se zajistilo, že proměnná nebude nikdy zapsána do. .NET Compiler Platform poskytuje rozhraní API, která usnadňují provádění této analýzy. Prvním krokem je vytvoření nového C# **analyzátoru s projektem opravit kód** .

- V aplikaci Visual Studio vyberte **soubor > nový > projekt...** zobrazí se dialogové okno Nový projekt.
- V **části C# rozšiřitelnost vizuálního >** vyberte **analyzátor s opravou kódu (.NET Standard)** .
- Pojmenujte projekt "**MakeConst**" a klikněte na tlačítko OK.

Analyzátor se šablonou opravy kódu vytvoří tři projekty: jeden obsahuje analyzátor a opravu kódu, druhým je projekt testu jednotek a třetí je projekt VSIX. Výchozí spouštěný projekt je projekt VSIX. Stisknutím klávesy **F5** spusťte projekt VSIX. Tím se spustí druhá instance sady Visual Studio, která zavedla nový analyzátor.

> [!TIP]
> Při spuštění analyzátoru spustíte druhou kopii sady Visual Studio. Tato druhá kopie používá k uložení nastavení jiný podregistr registru. To umožňuje odlišit nastavení vizuálu v obou kopiích sady Visual Studio. Můžete vybrat jiný motiv pro experimentální běh sady Visual Studio. Kromě toho nevytvářejte roaming nastavení ani přihlášení k účtu aplikace Visual Studio pomocí experimentálního spuštění sady Visual Studio. Který udržuje nastavení odlišně.

Ve druhé instanci sady Visual Studio, kterou jste právě spustili, vytvořte nový C# projekt konzolové aplikace (.NET Core nebo .NET Framework projekt budou fungovat na úrovni zdroje.) Najeďte myší na token podtrženým vlnovkou a zobrazí se text upozornění, který je k dispozici v analyzátoru.

Šablona vytvoří analyzátor, který ohlásí upozornění na každou deklaraci typu, kde název typu obsahuje malá písmena, jak je znázorněno na následujícím obrázku:

![Upozornění pro generování sestav analyzátoru](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Šablona také poskytuje opravu kódu, která změní jakýkoli název typu obsahující malá písmena na velká písmena. Můžete kliknout na žárovku, která se zobrazuje s upozorněním, a zobrazit navrhované změny. Přijetí navrhovaných změn aktualizuje název typu a všechny odkazy na daný typ v řešení. Teď, když jste viděli počáteční analyzátor v akci, zavřete druhou instanci sady Visual Studio a vraťte se do projektu analyzátoru.

Nemusíte spouštět druhou kopii sady Visual Studio a vytvořit nový kód pro otestování všech změn v analyzátoru. Šablona také vytvoří projekt testu jednotek za vás. Tento projekt obsahuje dva testy. `TestMethod1` zobrazuje typický formát testu, který analyzuje kód bez aktivace diagnostiky. `TestMethod2` zobrazuje formát testu, který aktivuje diagnostiku a poté použije navrhovanou opravu kódu. Při sestavování analyzátoru a opravy kódu budete psát testy pro různé struktury kódu, abyste ověřili svoji práci. Testy jednotek pro analyzátory jsou mnohem rychlejší než interaktivní testování pomocí sady Visual Studio.

> [!TIP]
> Testy jednotek analyzátoru jsou skvělým nástrojem, když víte, které konstrukce kódu by měly a nemají aktivovat analyzátor. Načítání analyzátoru v jiné kopii sady Visual Studio je skvělý nástroj pro zkoumání a hledání konstrukcí, na které jste se ještě nemuseli myslet.

## <a name="create-analyzer-registrations"></a>Vytvoření registrací analyzátoru

Šablona vytvoří počáteční třídu `DiagnosticAnalyzer` v souboru **MakeConstAnalyzer.cs** . Tento počáteční analyzátor zobrazuje dvě důležité vlastnosti každého analyzátoru.

- Každý diagnostický analyzátor musí poskytovat atribut `[DiagnosticAnalyzer]`, který popisuje jazyk, na kterém pracuje.
- Každý diagnostický analyzátor musí být odvozen od <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> třídy.

Šablona také zobrazuje základní funkce, které jsou součástí jakéhokoli analyzátoru:

1. Proveďte registraci akcí. Akce reprezentují změny kódu, které by měly aktivovat analyzátor, aby prozkoumali kód pro porušení. Když Visual Studio detekuje úpravy kódu, které odpovídají zaregistrované akci, volá metodu zaregistrovanou analyzátorem.
1. Vytvořte diagnostiku. Když analyzátor zjistí porušení, vytvoří objekt diagnostiky, který Visual Studio používá k upozorňování uživatele na porušení.

Akce zaregistrujete do přepsání <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metody. V tomto kurzu navštívíte **uzly syntaxe** , které hledají místní deklarace, a zjistíte, které z nich mají konstantní hodnoty. Pokud by deklarace mohla být konstantní, analyzátor vytvoří a nahlásí diagnostiku.

Prvním krokem je aktualizovat konstanty registru a metodu `Initialize` tak, aby tyto konstanty označovaly analyzátor "Make const". Většina řetězcových konstant je definována v souboru prostředků řetězce. Pro snazší lokalizaci byste měli postupovat podle tohoto postupu. Otevřete soubor **Resources. resx** pro projekt analyzátoru **MakeConst** . Tím se zobrazí editor prostředků. Aktualizujte prostředky řetězce následujícím způsobem:

- Změňte `AnalyzerTitle` na "proměnná může být vytvořena konstanta".
- Změňte `AnalyzerMessageFormat` na "lze vytvořit konstantu".
- Změňte `AnalyzerDescription` na "vytvořit konstantu".

Změňte také rozevírací seznam **modifikátor přístupu** na `public`. To usnadňuje používání těchto konstant v testování částí. Po dokončení by se měl editor prostředků zobrazit tak, jak ukazuje následující obrázek:

![Aktualizace prostředků řetězců](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Zbývající změny jsou v souboru analyzátoru. Otevřete **MakeConstAnalyzer.cs** v aplikaci Visual Studio. Změňte zaregistrovanou akci z jedné, která funguje na symbolech, které fungují na syntaxi. V metodě `MakeConstAnalyzerAnalyzer.Initialize` Najděte řádek, který zaregistruje akci na symboly:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Nahraďte ji následujícím řádkem:

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Po této změně můžete metodu `AnalyzeSymbol` odstranit. Tento analyzátor prověřuje <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, nikoli příkazy <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType>. Všimněte si, že `AnalyzeNode` obsahuje červené vlnovky. Kód, který jste právě přidali, odkazuje na metodu `AnalyzeNode`, která nebyla deklarována. Deklarujte tuto metodu pomocí následujícího kódu:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Změňte `Category` na "využití" v **MakeConstAnalyzer.cs** , jak je znázorněno v následujícím kódu:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Najde místní deklarace, které by mohly být const.

Je čas napsat první verzi metody `AnalyzeNode`. Měl by hledat jednu místní deklaraci, která by mohla být `const`, ale ne, jako v následujícím kódu:

```csharp
int x = 0;
Console.WriteLine(x);
```

Prvním krokem je najít místní deklarace. Do **MakeConstAnalyzer.cs**přidejte následující kód pro `AnalyzeNode`:

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Toto přetypování vždy proběhne úspěšně, protože analyzátor zaregistroval pro změny místních deklarací a pouze místní deklarace. Žádný jiný typ uzlu neaktivuje volání metody `AnalyzeNode`. Dále ověřte deklaraci pro všechny modifikátory `const`. Pokud je najdete, vraťte se hned. Následující kód vyhledá všechny modifikátory `const` v místní deklaraci:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Nakonec je třeba ověřit, zda by mohla být proměnná `const`. To znamená, že se po inicializaci nikdy nepřiřazuje.

Pomocí <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>provedete určitou sémantickou analýzu. Pomocí argumentu `context` určíte, zda lze vytvořit deklaraci lokální proměnné `const`. <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> představuje všechny sémantické informace v jednom zdrojovém souboru. Další informace najdete v článku, který pokrývá [sémantické modely](../work-with-semantics.md). Použijete <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> k provedení analýzy toku dat v příkazu místní deklarace. Pak použijete výsledky této analýzy toku dat, abyste zajistili, že místní proměnná nebude zapsána novou hodnotou kdekoli jinde. Voláním metody rozšíření <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> načtete <xref:Microsoft.CodeAnalysis.ILocalSymbol> proměnné a zkontrolujete, že není obsažena v kolekci <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> analýzy toku dat. Na konec `AnalyzeNode` metody přidejte následující kód:

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

Kód, který jste právě přidali, zajistí, že proměnná nebude změněna a lze ji proto nastavit `const`. Je čas vyvolat diagnostiku. Jako poslední řádek v `AnalyzeNode`přidejte následující kód:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Svůj průběh můžete zjistit stisknutím klávesy **F5** ke spuštění analyzátoru. Můžete načíst konzolovou aplikaci, kterou jste vytvořili dříve, a pak přidat následující zkušební kód:

```csharp
int x = 0;
Console.WriteLine(x);
```

Měla by se zobrazit žárovka a analyzátor by měl ohlásit diagnostiku. Žárovka však stále používá opravu kódu vygenerovanou šablonou a oznamuje vám, že může být proveden na velká písmena. V další části se dozvíte, jak napsat opravu kódu.

## <a name="write-the-code-fix"></a>Zapsat opravu kódu

Analyzátor může poskytovat jednu nebo více oprav kódu. Oprava kódu definuje úpravu, která řeší nahlášený problém. Pro analyzátor, který jste vytvořili, můžete zadat opravu kódu, která vloží klíčové slovo const:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Uživatel zvolí tuto možnost z uživatelského rozhraní žárovky v editoru a Visual Studio změní kód.

Otevřete soubor **MakeConstCodeFixProvider.cs** , který šablona přidala.  Tato oprava kódu je již zapojena do ID diagnostiky vytvořeného analyzátorem diagnostiky, ale ještě neimplementuje správnou transformaci kódu. Nejprve byste měli odebrat některý kód šablony. Změňte řetězec nadpisu na "vytvořit konstantu":

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Dále odstraňte metodu `MakeUppercaseAsync`. Už se nepoužívá.

Všichni poskytovatelé oprav kódu jsou odvozeni z <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>. Všechna <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> přepisují, aby nahlásily dostupné opravy kódu. V `RegisterCodeFixesAsync`změňte typ nadřazeného uzlu, který hledáte pro <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>, aby odpovídal diagnostice:

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Dále změňte poslední řádek pro registraci opravy kódu. Vaše oprava vytvoří nový dokument, který bude mít za následek přidání modifikátoru `const` do existující deklarace:

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Všimněte si červené vlnovky v kódu, který jste právě přidali na symbol `MakeConstAsync`. Přidejte deklaraci pro `MakeConstAsync` jako v následujícím kódu:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Vaše nová metoda `MakeConstAsync` transformuje <xref:Microsoft.CodeAnalysis.Document> reprezentující zdrojový soubor uživatele do nového <xref:Microsoft.CodeAnalysis.Document>, který nyní obsahuje deklaraci `const`.

Vytvoříte nový token klíčového slova `const` pro vložení na začátek prohlášení. Buďte opatrní, abyste nejdřív odebrali všechny úvodní minihry z prvního tokenu příkazu deklarace a připojili ho k tokenu `const`. Do metody `MakeConstAsync` přidejte následující kód:

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Dále přidejte token `const` k deklaraci pomocí následujícího kódu:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Dále naformátujte novou deklaraci tak C# , aby odpovídala pravidlům formátování. Formátování změn tak, aby odpovídalo existujícímu kódu, vytvoří lepší prostředí. Přidejte následující příkaz hned za existující kód:

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Pro tento kód je vyžadován nový obor názvů. Do horní části souboru přidejte následující příkaz `using`:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Posledním krokem je provedení úprav. Tento postup má tři kroky:

1. Získejte popisovač pro existující dokument.
1. Vytvořte nový dokument nahrazením existující deklarace novou deklarací.
1. Vrátí nový dokument.

Na konec `MakeConstAsync` metody přidejte následující kód:

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Oprava kódu je připravená k vyzkoušení.  Stisknutím klávesy F5 spusťte projekt analyzátoru v druhé instanci aplikace Visual Studio. Ve druhé instanci sady Visual Studio vytvořte nový C# projekt konzolové aplikace a přidejte několik deklarací místních proměnných inicializovaných s konstantními hodnotami do metody Main. Uvidíte, že jsou hlášeny jako upozornění, jak je uvedeno níže.

![Může vytvořit konstantní upozornění.](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Provedli jste spoustu pokroku. V deklaracích, které mohou být provedeny `const`, jsou vlnovky. I když ale pořád funguje. Tato funkce funguje, pokud přidáte `const` k deklaracím počínaje `i`a pak `j` a nakonec `k`. Pokud však přidáte modifikátor `const` v jiném pořadí, počínaje `k`, analyzátor vytvoří chyby: `k` nelze deklarovat `const`, pokud `i` a `j` oba již `const`. Máte možnost provést další analýzu, abyste se ujistili, že je možné zpracovat různé způsoby, které lze deklarovat a inicializovat.

## <a name="build-data-driven-tests"></a>Vytváření testů řízených daty

Analyzátor a oprava kódu fungují na jednoduchém případu jedné deklarace, která může být vytvořena jako const. Existuje mnoho možných příkazů deklarace, kde tato implementace způsobuje chyby. Tyto případy se řeší při práci s knihovnou testu jednotek zapsanou šablonou. Je mnohem rychlejší než opakované otevření druhé kopie sady Visual Studio.

Otevřete soubor **MakeConstUnitTests.cs** v projektu testování částí. Šablona vytvořila dva testy, které následují dva běžné vzory pro analyzátor a opravu testování částí kódu. `TestMethod1` zobrazuje vzor testu, který zajišťuje, že analyzátor neohlásí diagnostiku, pokud by neměl. `TestMethod2` zobrazuje vzor pro vytváření sestav diagnostiky a spuštění opravy kódu.

Kód pro téměř každý test pro analyzátor následuje po jednom z těchto dvou vzorů. V prvním kroku můžete tyto testy přepracovat jako testy řízené daty. Pak bude snadné vytvořit nové testy přidáním nových řetězcových konstant pro reprezentaci různých testovacích vstupů.

V rámci efektivity je prvním krokem refaktorování dvou testů do testů řízených daty. Pak stačí definovat několik řetězcových konstant pro každý nový test. I když refaktoring, přejmenujte obě metody pro lepší názvy. Nahraďte `TestMethod1` tímto testem, který zajišťuje, že se neaktivuje žádná diagnostika:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Můžete vytvořit nový řádek dat pro tento test definováním jakékoli fragmenty kódu, který by neměl způsobit, že diagnostika spustí upozornění. Toto přetížení `VerifyCSharpDiagnostic` projde, když nejsou pro fragment zdrojového kódu aktivované žádné diagnostiky.

Dále nahraďte `TestMethod2` tímto testem, který zajistí vyvolání diagnostiky, a opravu kódu použitou pro fragment zdrojového kódu:

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

Předchozí kód také provedl několik změn kódu, který vytváří očekávaný výsledek diagnostiky. Používá veřejné konstanty zaregistrované v analyzátoru `MakeConst`. Kromě toho používá dvě řetězcové konstanty pro vstupní a pevný zdroj. Do třídy `UnitTest` přidejte následující řetězcové konstanty:

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Spusťte tyto dva testy, abyste se ujistili, že jsou průchody. V aplikaci Visual Studio otevřete **Průzkumníka testů** výběrem možnosti **Test** > **Windows** > **Test Explorer**.  Stiskněte odkaz **Spustit vše** .

## <a name="create-tests-for-valid-declarations"></a>Vytvořit testy pro platné deklarace

Obecně platí, že analyzátory by měly skončit co nejrychleji, což má minimální práci. Visual Studio volá zaregistrované analyzátory jako kód úprav uživatele. Odezva je klíčovým požadavkem. Existuje několik testovacích případů pro kód, který by neměl vyvolat diagnostiku. Analyzátor již zpracovává jeden z těchto testů, případ, kdy je přiřazena proměnná po inicializaci. Přidejte následující řetězcovou konstantu do testů pro reprezentaci tohoto případu:

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Pak přidejte řádek dat pro tento test, jak je znázorněno v následujícím fragmentu kódu:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Tento test se také projde. Dále přidejte konstanty pro podmínky, které jste ještě nezpracovali:

- Deklarace, které jsou již `const`, protože jsou již const:

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Deklarace, které nemají žádný inicializátor, protože neexistuje žádná hodnota, která se má použít:

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Deklarace, kde inicializátor není konstanta, protože nemohou být konstanty v čase kompilace:

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

Může být ještě složitější, protože C# umožňuje více deklarací v rámci jednoho příkazu. Vezměte v úvahu následující řetězcové konstanty testovacího případu:

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Proměnná `i` může být vytvořena jako konstanta, ale proměnná `j` nemůže. Proto tento příkaz nelze vytvořit jako deklaraci konstanty. Přidejte deklarace `DataRow` pro všechny tyto testy:

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

Spusťte testy znovu a uvidíte, že tyto nové testovací případy selžou.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Aktualizace analyzátoru tak, aby ignoroval správné deklarace

K vyfiltrování kódu, který odpovídá těmto podmínkám, potřebujete některá vylepšení `AnalyzeNode` metody analyzátoru. Jsou to všechny související podmínky, takže podobné změny vyřeší všechny tyto podmínky. Proveďte následující změny `AnalyzeNode`:

- Vaše Sémantická analýza prozkoumala deklaraci jedné proměnné. Tento kód musí být ve smyčce `foreach`, která prověřuje všechny proměnné deklarované v rámci stejného příkazu.
- Každá deklarovaná proměnná musí mít inicializátor.
- Každý inicializátor deklarované proměnné musí být konstanta v čase kompilace.

V metodě `AnalyzeNode` nahraďte původní sémantickou analýzu:

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

s následujícím fragmentem kódu:

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

První `foreach` smyčka prověřuje každou deklaraci proměnné pomocí syntaktické analýzy. První ověření zaručuje, že proměnná má inicializátor. Druhá kontrolu garantuje, že inicializátor je konstanta. Druhá smyčka má původní sémantickou analýzu. Sémantické kontroly jsou samostatné smyčky, protože mají větší vliv na výkon. Spusťte testy znovu a měli byste je vidět, že jsou všechny passované.

## <a name="add-the-final-polish"></a>Přidat konečný polský

Už jste téměř hotovi. Analyzátor může zpracovat několik dalších podmínek. Visual Studio volá analyzátory, zatímco uživatel píše kód. Často se jedná o případ, kdy se analyzátor bude volat pro kód, který se nekompiluje. Metoda `AnalyzeNode` analyzátoru diagnostiky nezjistí, zda je konstantní hodnota převoditelná na typ proměnné. Aktuální implementace tak bude Happily převést nesprávnou deklaraci, jako je int i = "ABC", na místní konstantu. Přidat řetězcovou konstantu zdrojového řetězce pro tuto podmínku:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Odkazové typy se navíc nezpracovávají správně. Jediná hodnota konstanty povolená pro typ odkazu je `null`, s výjimkou případu, kdy <xref:System.String?displayProperty=nameWithType>, která umožňuje řetězcové literály. Jinými slovy, `const string s = "abc"` je právní, ale `const object s = "abc"` ne. Tento fragment kódu ověřuje tuto podmínku:

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Chcete-li být důkladnější, je nutné přidat další test, abyste se ujistili, že můžete vytvořit konstantní deklarace pro řetězec. Následující fragment kódu definuje kód, který vyvolává diagnostiku, a kód po použití opravy:

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Nakonec, pokud je proměnná deklarována s klíčovým slovem `var`, oprava kódu nesprávné věci a vygeneruje deklaraci `const var`, která není C# jazykem podporována. Chcete-li opravit tuto chybu, oprava kódu musí nahradit klíčové slovo `var` názvem odvozeného typu:

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Tyto změny aktualizují deklarace datových řádků pro oba testy. Následující kód ukazuje tyto testy se všemi atributy datových řádků:

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Naštěstí můžete všechny výše uvedené chyby vyřešit pomocí stejných technik, které jste právě naučili.

Chcete-li opravit první chybu, nejprve otevřete **DiagnosticAnalyzer.cs** a vyhledejte smyčku foreach, kde jsou zkontrolovány jednotlivé Inicializátory místní deklarace, aby bylo zajištěno, že jsou přiřazeny pomocí konstantních hodnot. Bezprostředně _před_ první smyčkou foreach volejte `context.SemanticModel.GetTypeInfo()`, aby se načetly podrobné informace o deklarovaném typu místní deklarace:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Potom v rámci smyčky `foreach` zkontrolujte každý inicializátor a ujistěte se, že je převoditelné na typ proměnné. Po ověření, že inicializátor je konstanta, přidejte následující kontrolu:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Další změny se vytvoří po poslední. Před pravou složenou závorkou první smyčky foreach přidejte následující kód pro zkontrolování typu místní deklarace, je-li konstanta řetězec nebo hodnota null.

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

Chcete-li nahradit klíčové slovo var správným názvem typu, je nutné ve svém poskytovateli opravy kódu napsat trochu větší kód. Vraťte se na **CodeFixProvider.cs**. Kód, který přidáte, provede následující kroky:

- Ověřte, zda je deklarace deklarace `var` a zda je:
- Vytvoří nový typ pro odvozený typ.
- Ujistěte se, že deklarace typu není alias. Pokud ano, je právní `const var`deklarovat.
- Ujistěte se, že v tomto programu `var` není název typu. (Pokud ano, `const var` je právní).
- Zjednodušit úplný název typu

Tyto zvuky jako velké množství kódu. Není to. Nahraďte řádek, který deklaruje a inicializuje `newLocal`, pomocí následujícího kódu. Hned po inicializaci `newModifiers`:

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

K použití typu <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> budete muset přidat jeden `using` příkaz:

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Spusťte testy a všechny by měly být passované. Congratulate se tak, že spustíte kompletní analyzátor. Stisknutím kombinace kláves CTRL + F5 spusťte projekt analyzátoru v druhé instanci sady Visual Studio s načteným rozšířením Roslyn Preview.

- Ve druhé instanci sady Visual Studio vytvořte nový C# projekt konzolové aplikace a přidejte `int x = "abc";` do metody Main. Děkujeme, že při první opravě chyby by se pro tuto místní proměnnou proměnné nemělo hlásit žádné upozornění (i když dojde k chybě kompilátoru, jak se očekávalo).
- Dále přidejte `object s = "abc";` do metody Main. Z důvodu druhé opravy chyby by se nemělo hlásit žádné upozornění.
- Nakonec přidejte další místní proměnnou, která používá klíčové slovo `var`. Uvidíte, že se nahlásí upozornění a na levé straně se zobrazí návrh.
- Přesuňte kurzor editoru na podtržení vlnovkou a stiskněte kombinaci kláves CTRL +. pro zobrazení navrhované opravy kódu. Po výběru opravy kódu si všimněte, že klíčové slovo var se nyní zpracovává správně.

Nakonec přidejte následující kód:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Po těchto změnách získáte červené vlnovky pouze první dvě proměnné. Přidejte `const` do `i` i `j`a dostanete nové upozornění na `k`, protože teď může být `const`.

Blahopřejeme! Vytvořili jste první rozšíření .NET Compiler Platform, které provádí průběžnou analýzu kódu k detekci problému a nabízí rychlou opravu pro její opravu. Na cestě jste se naučili mnoho rozhraní API kódu, která jsou součástí sady .NET Compiler Platform SDK (rozhraní API Roslyn). Práci s [dokončenou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) najdete v našem úložišti GitHub Samples.

## <a name="other-resources"></a>Další prostředky

- [Začínáme s analýzou syntaxe](../get-started/syntax-analysis.md)
- [Začínáme se sémantickou analýzou](../get-started/semantic-analysis.md)
