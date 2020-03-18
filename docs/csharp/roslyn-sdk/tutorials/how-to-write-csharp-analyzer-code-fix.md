---
title: 'Kurz: Napište svůj první analyzátor a opravu kódu'
description: Tento kurz obsahuje podrobné pokyny k sestavení analyzátoru a opravy kódu pomocí sady SDK .NET Compiler SDK (Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: f6fc21c010f9b5fcd5e709ef822639c020a7c93b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240547"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Kurz: Napište svůj první analyzátor a opravu kódu

Sada SDK platformy kompilátoru .NET poskytuje nástroje, které potřebujete k vytvoření vlastních upozornění, která cílí na kód jazyka C# nebo Visual Basic. **Analyzátor** obsahuje kód, který rozpozná porušení pravidla. **Oprava kódu** obsahuje kód, který opravuje porušení. Pravidla, která implementujete může být cokoli od struktury kódu na styl kódování na konvence pojmenování a další. Platforma kompilátoru .NET poskytuje rámec pro spuštění analýzy, protože vývojáři píší kód a všechny funkce rozhraní Visual Studio pro opravu kódu: zobrazení vlnovek v editoru, vyplnění seznamu chyb sady Visual Studio, vytvoření "žárovky" návrhy a zobrazení bohaté náhledu navrhovaných oprav.

V tomto kurzu se budete zabývat **vytvořeníanalyzátoru** a doprovodný **kód opravit** pomocí Roslyn API. Analyzátor je způsob, jak provést analýzu zdrojového kódu a nahlásit problém uživateli. Volitelně může analyzátor také poskytnout opravu kódu, která představuje změnu zdrojového kódu uživatele. Tento kurz vytvoří analyzátor, který vyhledá deklarace místní `const` proměnné, které by mohly být deklarovány pomocí modifikátoru, ale nejsou. Doprovodný kód opravit upravuje tyto deklarace přidat `const` modifikátor.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

Budete muset nainstalovat **sdk platformy kompilátoru .NET** prostřednictvím Instalačního programu sady Visual Studio:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Existuje několik kroků k vytvoření a ověření analyzátoru:

1. Vytvořte řešení.
1. Zaregistrujte název a popis analyzátoru.
1. Nahlásit upozornění a doporučení analyzátoru.
1. Implementujte opravu kódu přijímat doporučení.
1. Zlepšete analýzu pomocí jednotkových testů.

## <a name="explore-the-analyzer-template"></a>Prozkoumejte šablonu analyzátoru

Analyzátor hlásí uživateli všechny deklarace místní proměnné, které lze převést na místní konstanty. Zvažte například následující kód:

```csharp
int x = 0;
Console.WriteLine(x);
```

Ve výše uvedeném kódu `x` je přiřazena konstantní hodnota a nikdy se nemění. To může být `const` deklarována pomocí modifikátoru:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Analýza k určení, zda proměnná může být konstanta je zapojen, vyžadující syntaktické analýzy, konstantní analýzy výrazu inicializátoru a analýzy toku dat zajistit, že proměnná je nikdy zapsána do. Platforma kompilátoru .NET poskytuje rozhraní API, která usnadňují provádění této analýzy. Prvním krokem je vytvoření nového **c# analyzátoru s projektem opravy kódu.**

- V sadě Visual Studio zvolte **Soubor > Nový > project...** a zobrazte dialogové okno Nový projekt.
- V **části Visual C# > Rozšiřitelnost**zvolte **Analyzer with code fix (.NET Standard).**
- Pojmenujte projekt**MakeConst**a klepněte na tlačítko OK.

Analyzátor se šablonou oprava kódu vytvoří tři projekty: jeden obsahuje analyzátor a opravu kódu, druhý je projekt testování částí a třetí je projekt VSIX. Výchozí projekt spuštění je projekt VSIX. Stisknutím **klávesy F5** spusťte projekt VSIX. Tím se spustí druhá instance sady Visual Studio, která načetla nový analyzátor.

> [!TIP]
> Při spuštění analyzátoru spustíte druhou kopii sady Visual Studio. Tato druhá kopie používá k ukládání nastavení jiný podregistr registru. To umožňuje odlišit vizuální nastavení ve dvou kopiích sady Visual Studio. Můžete vybrat jiný motiv pro experimentální spuštění sady Visual Studio. Kromě toho nepřecházejte nastavení nebo se přihlašujte k účtu sady Visual Studio pomocí experimentálního spuštění sady Visual Studio. To udržuje nastavení odlišné.

V druhé instanci sady Visual Studio, kterou jste právě spustili, vytvořte nový projekt aplikace konzoly Jazyka C# (projekt .NET Core nebo .NET Framework bude fungovat -- analyzátory pracují na zdrojové úrovni.) Najeďte nad token s podtržením vlnovkou a zobrazí se varovný text poskytnutý analyzátorem.

Šablona vytvoří analyzátor, který hlásí upozornění na každé deklaraci typu, kde název typu obsahuje malá písmena, jak je znázorněno na následujícím obrázku:

![Upozornění pro hlášení analyzátoru](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Šablona také poskytuje opravu kódu, která změní libovolný název typu obsahující malá písmena na všechna velká písmena. Můžete kliknout na žárovku zobrazenou s upozorněním, abyste viděli navrhované změny. Přijetí navrhovaných změn aktualizuje název typu a všechny odkazy na tento typ v řešení. Teď, když jste viděli počáteční analyzátor v akci, zavřete druhou instanci Sady Visual Studio a vraťte se do projektu analyzátoru.

Není třeba spustit druhou kopii sady Visual Studio a vytvořit nový kód pro testování každé změny v analyzátoru. Šablona také vytvoří projekt testování částí pro vás. Tento projekt obsahuje dva testy. `TestMethod1`zobrazuje typický formát testu, který analyzuje kód bez spuštění diagnostiky. `TestMethod2`zobrazuje formát testu, který spouští diagnostiku, a potom použije navrhovanou opravu kódu. Při vytváření analyzátoru a opravy kódu napíšete testy pro různé struktury kódu, abyste ověřili svou práci. Testy částí pro analyzátory jsou mnohem rychlejší než jejich interaktivní testování pomocí sady Visual Studio.

> [!TIP]
> Testy částí analyzátoru jsou skvělý nástroj, když víte, jaké konstrukce kódu by měly a neměly aktivovat analyzátor. Načítání analyzátoru v jiné kopii sady Visual Studio je skvělý nástroj k prozkoumání a hledání konstrukcí, o kterých jste možná ještě nepřemýšleli.

## <a name="create-analyzer-registrations"></a>Vytvořit registrace analyzátoru

Šablona vytvoří `DiagnosticAnalyzer` počáteční třídu v **souboru MakeConstAnalyzer.cs.** Tento počáteční analyzátor zobrazuje dvě důležité vlastnosti každého analyzátoru.

- Každý diagnostický analyzátor `[DiagnosticAnalyzer]` musí poskytnout atribut, který popisuje jazyk, ve kterém pracuje.
- Každý diagnostický analyzátor musí <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> být odvozen ze třídy.

Šablona také zobrazuje základní funkce, které jsou součástí každého analyzátoru:

1. Zaregistrujte akce. Akce představují změny kódu, které by měly aktivovat analyzátor prozkoumat kód pro porušení. Když Visual Studio zjistí úpravy kódu, které odpovídají registrované akce, volá registrovaný metodu analyzátoru.
1. Vytvořte diagnostiku. Když analyzátor zjistí porušení, vytvoří diagnostický objekt, který Visual Studio používá k upozornění uživatele porušení.

Akce se zaregistruje v <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> přepsání metody. V tomto kurzu navštívíte **syntaktické uzly, které** hledají místní deklarace, a zjistíte, které z nich mají konstantní hodnoty. Pokud deklarace může být konstantní, analyzátor vytvoří a ohlásí diagnostiku.

Prvním krokem je aktualizace registračníkonstanty `Initialize` a metody tak, aby tyto konstanty označují váš analyzátor "Make Const". Většina konstant řetězce je definována v souboru prostředků řetězce. Měli byste dodržovat tuto praxi pro snadnější lokalizaci. Otevřete soubor **Resources.resx** pro projekt analyzátoru **MakeConst.** Zobrazí se editor prostředků. Aktualizujte prostředky řetězce takto:

- Změna `AnalyzerTitle` na "Proměnná může být konstantní".
- Změna `AnalyzerMessageFormat` na "Může být konstantní".
- Změňte `AnalyzerDescription` na "Vytvořit konstantu".

Změňte také rozevírací soubor `public` **Modifikátor přístupu** na . To usnadňuje použití těchto konstant v jednotkových testech. Po dokončení by měl editor prostředků zobrazit následující obrázek:

![Aktualizovat prostředky řetězce](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Zbývající změny jsou v souboru analyzátoru. Otevřete **MakeConstAnalyzer.cs** v sadě Visual Studio. Změňte registrovanou akci z akce, která působí na symboly, na akci, která funguje na syntaxi. V `MakeConstAnalyzerAnalyzer.Initialize` metodě najděte řádek, který registruje akci na symboly:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Nahraďte jej následujícím řádkem:

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Po této změně můžete `AnalyzeSymbol` odstranit metodu. Tento analyzátor <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>zkoumá <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> , nikoli příkazy. Všimněte `AnalyzeNode` si, že má červené klikyháky pod ním. Kód, který jste právě `AnalyzeNode` přidali odkazuje na metodu, která nebyla deklarována. Deklarujte tuto metodu pomocí následujícího kódu:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Změňte `Category` na "Využití" v **MakeConstAnalyzer.cs** jak je znázorněno v následujícím kódu:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Najít místní prohlášení, která by mohla být const

Je čas napsat první verzi `AnalyzeNode` metody. Měl by hledat jednu místní `const` deklaraci, která by mohla být, ale není, jako následující kód:

```csharp
int x = 0;
Console.WriteLine(x);
```

Prvním krokem je najít místní prohlášení. Do `AnalyzeNode` **MakeConstAnalyzer.cs**přidejte následující kód :

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Toto přetypované vždy úspěšné, protože analyzátor registrovány pro změny místní deklarace a pouze místní deklarace. Žádný jiný typ uzlu nespustí `AnalyzeNode` volání vaší metody. Dále zkontrolujte deklaraci `const` pro všechny modifikátory. Pokud je najdete, okamžitě se vraťte. Následující kód hledá `const` všechny modifikátory v místní deklaraci:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Nakonec je třeba zkontrolovat, zda `const`proměnná může být . To znamená, že po inicializace není nikdy přiřazen.

Provedete sémantickou analýzu <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>pomocí . Pomocí argumentu `context` můžete určit, zda lze `const`provést deklaraci místní proměnné . Představuje <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> všechny sémantické informace v jednom zdrojovém souboru. Další informace naleznete v článku, který pokrývá [sémantické modely](../work-with-semantics.md). Budete používat k <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> provedení analýzy toku dat na příkaz místní deklarace. Potom použijete výsledky této analýzy toku dat k zajištění, že místní proměnná není zapsána s novou hodnotou nikde jinde. Volání <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metody rozšíření načíst <xref:Microsoft.CodeAnalysis.ILocalSymbol> pro proměnnou a zkontrolujte, zda <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> není obsažena s kolekcí analýzy toku dat. Na konec `AnalyzeNode` metody přidejte následující kód:

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

Právě přidaný kód zajišťuje, že proměnná není změněna, a proto může být provedena `const`. Je čas zvýšit diagnostiku. Přidejte následující kód jako `AnalyzeNode`poslední řádek v :

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Průběh můžete zkontrolovat stisknutím **klávesy F5** a spusťte analyzátor. Můžete načíst konzolovou aplikaci, kterou jste vytvořili dříve, a pak přidat následující testovací kód:

```csharp
int x = 0;
Console.WriteLine(x);
```

Měla by se zobrazit žárovka a analyzátor by měl hlásit diagnostiku. Žárovka však stále používá šablonu generovaný kód opravit a řekne vám, že může být velká písmena. V další části je vysvětleno, jak napsat opravu kódu.

## <a name="write-the-code-fix"></a>Napsat opravu kódu

Analyzátor může poskytnout jednu nebo více oprav kódu. Oprava kódu definuje úpravu, která řeší nahlášený problém. Pro analyzátor, který jste vytvořili, můžete poskytnout opravu kódu, která vloží klíčové slovo const:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Uživatel si jej vybere z uživatelského rozhraní žárovky v editoru a Visual Studio změní kód.

Otevřete **soubor MakeConstCodeFixProvider.cs** přidaný šablonou.  Tato oprava kódu je již připojena k ID diagnostiky vytvořeného diagnostickým analyzátorem, ale ještě neimplementuje správnou transformaci kódu. Nejprve byste měli odstranit některé kód šablony. Změňte řetězec nadpisu na "Vytvořit konstantu":

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Dále odstraňte `MakeUppercaseAsync` metodu. Už to neplatí.

Všichni zprostředkovatelé opravy <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>kódu jsou odvozeni z . Všechny přepsat <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> nahlásit dostupné opravy kódu. V `RegisterCodeFixesAsync`aplikace změňte hledaný typ předchůdce na <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> typ uzlu tak, aby odpovídal diagnostice:

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Dále změňte poslední řádek a zaregistrujte opravu kódu. Oprava vytvoří nový dokument, který je `const` výsledkem přidání modifikátoru do existující deklarace:

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

V kódu, který jste právě přidali na symbol `MakeConstAsync`, si všimnete červených vlnovek . Přidejte deklaraci pro `MakeConstAsync` následující kód:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Nová `MakeConstAsync` metoda transformuje <xref:Microsoft.CodeAnalysis.Document> představující zdrojový soubor uživatele na <xref:Microsoft.CodeAnalysis.Document> nový, `const` který nyní obsahuje deklaraci.

Vytvoříte nový `const` token klíčového slova vložit na přední straně prohlášení prohlášení. Buďte opatrní nejprve odebrat všechny vedoucí trivia z prvnítoken `const` prohlášení prohlášení a připojit jej k tokenu. Do metody `MakeConstAsync` přidejte následující kód:

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Dále přidejte `const` token do deklarace pomocí následujícího kódu:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Dále naformátujte novou deklaraci tak, aby odpovídala pravidlům formátování jazyka C#. Formátování změn tak, aby odpovídaly existujícímu kódu, vytvoří lepší prostředí. Přidejte následující příkaz ihned za existující kód:

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Pro tento kód je vyžadován nový obor názvů. Do horní `using` části souboru přidejte následující příkaz:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Posledním krokem je, aby vaše úpravy. Tento proces má tři kroky:

1. Získejte popisovač existujícího dokumentu.
1. Vytvořte nový dokument nahrazením existující deklarace s novou deklarací.
1. Vraťte nový dokument.

Na konec `MakeConstAsync` metody přidejte následující kód:

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Oprava kódu je připravena k vyzkoušení.  Stisknutím klávesy F5 spusťte projekt analyzátoru v druhé instanci sady Visual Studio. V druhé instanci Sady Visual Studio vytvořte nový projekt aplikace konzoly Jazyka C# a přidejte několik deklarací místních proměnných inicializovaných s konstantními hodnotami do metody Main. Uvidíte, že jsou hlášeny jako varování, jak je uvedeno níže.

![Může const varování](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Udělal jsi velký pokrok. Existují klikyháky pod prohlášení, které `const`mohou být provedeny . Ale je tu ještě práce. Tato práce citlivý- `const` li tebe přidat `i`až `j` k `k`the declarations začíná na . then a finally . Pokud však přidáte `const` modifikátor v jiném `k`pořadí, počínaje písmenem , analyzátor vytvoří chyby: `k` nelze `const`deklarovat , `i` pokud a `j` nejsou již `const`obě . Musíte provést další analýzu, abyste zajistili, že zvládnete různé způsoby, jak mohou být proměnné deklarovány a inicializovány.

## <a name="build-data-driven-tests"></a>Sestavení testů řízených daty

Analyzátor a kód opravit práci na jednoduchý případ jednoho prohlášení, které mohou být provedeny const. Existuje mnoho možných prohlášení prohlášení, kde tato implementace dělá chyby. Tyto případy vyřešíte pomocí knihovny testování částí napsané šablonou. Je to mnohem rychlejší než opakované otevření druhé kopie sady Visual Studio.

Otevřete soubor **MakeConstUnitTests.cs** v projektu testování částí. Šablona vytvořila dva testy, které následují dva běžné vzory pro analyzátor a test jednotky oprava kódu. `TestMethod1`zobrazí vzor pro test, který zajišťuje, že analyzátor nehlásí diagnostiku, když by neměl. `TestMethod2`zobrazuje vzor pro nahlášení diagnostiky a spuštění opravy kódu.

Kód pro téměř každý test pro analyzátor následuje jeden z těchto dvou vzorů. Pro první krok můžete přepracovat tyto testy jako testy řízené daty. Potom bude snadné vytvořit nové testy přidáním nové řetězce konstanty představují různé testovací vstupy.

Z důvodu efektivity je prvním krokem refaktoring dvou testů do testů řízených daty. Potom stačí definovat několik konstant řetězce pro každý nový test. Při refaktoringu přejmenujte obě metody na lepší názvy. Nahraďte `TestMethod1` tímto testem, který zajistí, že nebude vyvolána žádná diagnostika:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Můžete vytvořit nový řádek dat pro tento test definováním libovolný fragment kódu, který by neměl způsobit diagnostiku aktivovat upozornění. Toto `VerifyCSharpDiagnostic` přetížení průchodů, pokud neexistují žádné diagnostiky spuštěna pro fragment zdrojového kódu.

Dále nahraďte `TestMethod2` tímto testem, který zajistí, že je vyvolána diagnostika a oprava kódu použitá pro fragment zdrojového kódu:

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

Předchozí kód také provedl několik změn v kódu, který vytváří očekávaný výsledek diagnostiky. Používá veřejné konstanty registrované `MakeConst` v analyzátoru. Kromě toho používá dvě konstanty řetězce pro vstup a pevný zdroj. Do `UnitTest` třídy přidejte následující konstanty řetězce:

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Spusťte tyto dva testy, abyste se ujistili, že projdou. V sadě Visual Studio otevřete **Průzkumníka testů** výběrem **možnosti Testovat** > **Průzkumníka testů systému****Windows** > .  Stisknutím tlačítka **Spustit vše** odkaz.

## <a name="create-tests-for-valid-declarations"></a>Vytvořit testy pro platné deklarace

Obecně platí, že analyzátory by měly ukončit co nejrychleji a dělat minimální práci. Visual Studio volá registrované analyzátory jako uživatel ueviduje kód. Reakce je klíčovým požadavkem. Existuje několik testovacích případů pro kód, který by neměl vyvolat diagnostiku. Analyzátor již zpracovává jeden z těchto testů, případ, kdy je proměnná přiřazena po inicializování. Přidejte do testů následující řetězcovou konstantu, která představuje toto případ:

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Potom přidejte datový řádek pro tento test, jak je znázorněno ve fragmentu níže:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Tento test projde také. Dále přidejte konstanty pro podmínky, které jste ještě nezpracovali:

- Prohlášení, která `const`jsou již , protože jsou již const:

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Deklarace, které nemají inicializátor, protože neexistuje žádná hodnota pro použití:

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Deklarace, kde inicializátor není konstanta, protože nemohou být konstanty v době kompilace:

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

Může být ještě složitější, protože C# umožňuje více deklarací jako jeden příkaz. Zvažte následující konstantu řetězce testovacího případu:

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Proměnná `i` může být konstantní, `j` ale proměnná nemůže. Proto toto prohlášení nelze provést const prohlášení. Přidejte `DataRow` deklarace pro všechny tyto testy:

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

Spusťte testy znovu a uvidíte, že tyto nové testovací případy se nezdaří.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Aktualizace analyzátoru ignorovat správné deklarace

Potřebujete některá vylepšení metody analyzátoru `AnalyzeNode` k odfiltrování kódu, který odpovídá těmto podmínkám. Všechny jsou související podmínky, takže podobné změny opraví všechny tyto podmínky. Proveďte následující `AnalyzeNode`změny :

- Vaše sémantická analýza zkoumala jednu deklaraci proměnné. Tento kód musí být `foreach` ve smyčce, která zkoumá všechny proměnné deklarované ve stejném příkazu.
- Každá deklarovaná proměnná musí mít inicializátor.
- Každá deklarovaná proměnná inicializátor musí být konstanta v čase kompilace.

Ve `AnalyzeNode` své metodě nahraďte původní sémantickou analýzu:

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

První `foreach` smyčka zkoumá každou deklaraci proměnné pomocí syntaktické analýzy. První kontrola zaručuje, že proměnná má inicializátor. Druhá kontrola zaručuje, že inicializátor je konstanta. Druhá smyčka má původní sémantickou analýzu. Sémantické kontroly jsou v samostatné smyčce, protože má větší vliv na výkon. Spusťte testy znovu, a měli byste vidět všechny projít.

## <a name="add-the-final-polish"></a>Přidejte konečný lesk

Už jste téměř hotovi. Existuje několik dalších podmínek pro váš analyzátor zvládnout. Visual Studio volá analyzátory, zatímco uživatel píše kód. Často se stává, že váš analyzátor bude volán pro kód, který se nekompiluje. Metoda diagnostického analyzátoru `AnalyzeNode` nekontroluje, zda je konstantní hodnota konvertibilní na typ proměnné. Takže aktuální implementace bude šťastně převést nesprávné deklarace, jako je int i = "abc"' na místní konstantu. Přidejte konstantu zdrojového řetězce pro tuto podmínku:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Kromě toho nejsou správně zpracovány typy odkazů. Jedinou konstantní hodnotou povolenou `null`pro typ odkazu <xref:System.String?displayProperty=nameWithType>je , s výjimkou tohoto případu , který umožňuje řetězcové literály. Jinými slovy, `const string s = "abc"` je `const object s = "abc"` legální, ale není. Tento fragment kódu tuto podmínku ověří:

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Chcete-li být důkladný, musíte přidat další test, abyste se ujistili, že můžete vytvořit konstantní deklaraci pro řetězec. Následující úryvek definuje kód, který vyvolává diagnostiku, i kód po použití opravy:

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Nakonec pokud je proměnná `var` deklarována pomocí klíčového slova, `const var` oprava kódu nesprávná věc a generuje deklaraci, která není podporována jazykem Jazyka C#. Chcete-li tuto chybu opravit, `var` oprava kódu musí nahradit klíčové slovo s názvem odvozeného typu:

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Tyto změny aktualizovat deklarace řádků dat pro oba testy. Následující kód ukazuje tyto testy se všemi atributy řádku dat:

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Naštěstí všechny výše uvedené chyby mohou být řešeny pomocí stejných technik, které jste se právě naučili.

Chcete-li opravit první chybu, **nejprve** otevřete DiagnosticAnalyzer.cs a vyhledejte foreach smyčky, kde jsou kontrolovány každý z inicializátory místní deklarace, aby bylo zajištěno, že jsou přiřazeny s konstantní mise. Bezprostředně _před_ první foreach `context.SemanticModel.GetTypeInfo()` smyčky, volání načíst podrobné informace o deklarovaný typ místní deklarace:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Potom ve `foreach` smyčce zkontrolujte každý inicializátor, abyste se ujistili, že je konvertibilní na typ proměnné. Přidejte následující kontrolu po zajištění, že inicializátor je konstanta:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Další změna navazuje na poslední. Před uzavírací složené závorky první smyčky foreach, přidejte následující kód pro kontrolu typu místní deklarace, pokud je konstanta řetězec nebo null.

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

Musíte napsat trochu více kódu ve vašem zprostředkovateli opravy kódu nahradit var ' klíčové slovo se správným názvem typu. Vraťte se do **CodeFixProvider.cs**. Kód, který přidáte, provede následující kroky:

- Zkontrolujte, zda `var` je deklarace deklarace a zda je:
- Vytvořte nový typ pro odvozený typ.
- Ujistěte se, že deklarace typu není alias. Pokud ano, je legální `const var`prohlásit .
- Ujistěte `var` se, že v tomto programu není název typu. (Pokud ano, `const var` je legální).
- Zjednodušení celého názvu typu

To zní jako hodně kódu. Není. Nahraďte řádek, který deklaruje a inicializuje `newLocal` s následujícím kódem. Jde bezprostředně po inicializaci `newModifiers`:

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Chcete-li použít typ, `using` <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> budete muset přidat jeden příkaz:

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Spusťte testy a všechny by měly projít. Pogratulujte si spuštěním hotového analyzátoru. Stisknutím kombinace kláves Ctrl+F5 spusťte projekt analyzátoru ve druhé instanci sady Visual Studio s načteným rozšířením Roslyn Preview.

- V druhé instanci Sady Visual Studio vytvořte `int x = "abc";` nový projekt aplikace konzoly Jazyka C# a přidejte do metody Main. Díky první opravě chyby by nemělo být hlášeno žádné upozornění pro tuto deklaraci místní proměnné (i když je chyba kompilátoru podle očekávání).
- Dále přidejte `object s = "abc";` do hlavní metody. Z důvodu druhé opravy chyby by měla být hlášena žádná upozornění.
- Nakonec přidejte další místní `var` proměnnou, která používá klíčové slovo. Uvidíte, že je hlášeno upozornění a vlevo se zobrazí návrh.
- Přesuňte stříšku editoru přes vlnité podtržení a stiskněte kombinaci kláves Ctrl+. zobrazíte navrhovanou opravu kódu. Po výběru opravy kódu si všimněte, že klíčové slovo var je nyní správně zpracováno.

Nakonec přidejte následující kód:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Po těchto změnách získáte červené vlnovky pouze na první dvě proměnné. Přidejte `const` `i` do `j`obou a a dostanete `k` nové upozornění, `const`protože nyní může být .

Blahopřejeme! Vytvořili jste první rozšíření platformy kompilátoru .NET, které provádí průběžnou analýzu kódu za účelem zjištění problému a poskytuje rychlou opravu k jeho opravě. Cestou jste se naučili mnoho rozhraní API kódu, které jsou součástí rozhraní .NET Compiler Platform SDK (Roslyn API). Svou práci můžete zkontrolovat podle [dokončené ukázky](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) v našem ukázkovém úložišti GitHub.

## <a name="other-resources"></a>Další prostředky

- [Začínáme se syntaktickou analýzou](../get-started/syntax-analysis.md)
- [Začínáme se sémantickou analýzou](../get-started/semantic-analysis.md)
