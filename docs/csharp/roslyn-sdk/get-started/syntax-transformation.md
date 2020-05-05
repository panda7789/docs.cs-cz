---
title: Začínáme s transformací syntaxe (rozhraní API Roslyn)
description: Úvod do procházení, dotazování a procházení stromů syntaxe.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 232fe5fcba35f152dbc3f00b2f2c092b5df0dd35
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794790"
---
# <a name="get-started-with-syntax-transformation"></a>Začínáme s transformací syntaxe

V tomto kurzu se seznámíte s koncepty a technikami, které jsme prozkoumali v části [Začínáme s analýzou syntaxe](syntax-analysis.md) a [Začínáme s nástroji pro rychlé zprovoznění sémantických analýz](semantic-analysis.md) . Pokud jste to ještě neudělali, měli byste před zahájením tohoto postupu dokončit tyto rychlé starty.

V tomto rychlém startu prozkoumáte techniky vytváření a transformování stromů syntaxe. V kombinaci s technikami, které jste se naučili v předchozích rychlých startech, vytvoříte první refaktoring příkazového řádku.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Neměnnosti a platforma .NET Compiler

**Neměnnosti** je základní principem platformy .NET Compiler. Neměnné datové struktury nelze po vytvoření změnit. Neměnné datové struktury je možné bezpečně sdílet a analyzovat přes víc příjemců současně. Nehrozí nebezpečí, že jeden příjemce ovlivňuje jiné nepředvídatelné způsoby. Analyzátor nepotřebuje zámky nebo jiné míry souběžnosti. Toto pravidlo se vztahuje na stromy syntaxe, kompilace, symboly, sémantické modely a na všechny ostatní datové struktury, ke kterým dojde. Místo úprav existujících struktur vytvoří rozhraní API nové objekty založené na zadaných rozdílech na staré. Tento koncept použijete pro stromy syntaxe pro vytvoření nových stromů pomocí transformací.

## <a name="create-and-transform-trees"></a>Vytváření a transformace stromů

Zvolíte jednu ze dvou strategií pro transformaci syntaxe. **Metody továrního** využití se nejlépe používají při hledání konkrétních uzlů k nahrazení nebo určitých umístění, kam chcete vložit nový kód. Opakované **zápisy** jsou nejvhodnější, pokud chcete skenovat celý projekt vzorů kódu, které chcete nahradit.

### <a name="create-nodes-with-factory-methods"></a>Vytváření uzlů s metodami pro vytváření objektů

První transformace syntaxe ukazuje metody továrny. Chystáte se nahradit `using System.Collections;` příkaz `using System.Collections.Generic;` příkazem. Tento příklad ukazuje, jak vytvořit <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> objekty pomocí metod <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> Factory. Pro každý typ **uzlu**, **tokenu**nebo **minihry** existuje výrobní metoda, která vytvoří instanci tohoto typu. Struktury syntaxe můžete vytvářet hierarchicky sestavování uzlů v hierarchickém uspořádání. Pak převedete existující program tak, aby nahradil stávající uzly nově vytvořeným stromem.

Spusťte Visual Studio a vytvořte nový projekt **Nástroje pro analýzu kódu** v jazyce C#. V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt** a zobrazte tak dialogové okno Nový projekt. V části**rozšiřitelnost** v jazyce **Visual C#** > vyberte **Nástroj pro analýzu**samostatného kódu. Tento rychlý Start má dva ukázkové projekty, takže si pojmenujte řešení **SyntaxTransformationQuickStart**a pojmenujte projekt **ConstructionCS**. Klikněte na tlačítko **OK**.

Tento projekt používá metody <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> třídy k sestavení <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> představující `System.Collections.Generic` obor názvů.

Do horní části `Program.cs` souboru přidejte následující direktivy using, abyste importovali metody továrny <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> třídy a metody, <xref:System.Console> abyste je mohli použít později bez jejich zařazení:

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Vytvoříte **uzly syntaxe názvu** pro sestavení stromu, který představuje `using System.Collections.Generic;` příkaz. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>je základní třídou pro čtyři typy názvů, které se zobrazují v jazyce C#. Tyto čtyři typy názvů vytvoříte společně, abyste mohli vytvořit libovolný název, který se může zobrazit v jazyce C#:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, který představuje jednoduché názvy s jedním identifikátorem, jako `System` jsou a `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, který představuje obecný typ nebo název metody, například `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, který představuje kvalifikovaný název formuláře `<left-name>.<right-identifier-or-generic-name>` , například. `System.IO`
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, který představuje název pomocí externího aliasu sestavení jako `LibraryV2::Foo`.

Použijte <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> metodu k vytvoření <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> uzlu. Do `Main` metody přidejte následující kód v `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Předchozí kód vytvoří <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> objekt a přiřadí jej proměnné `name`. Mnoho z rozhraní API Roslyn vrací základní třídy, aby bylo snazší pracovat se souvisejícími typy. Proměnnou `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>a, lze znovu použít při sestavování <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nepoužívejte odvození typu při sestavování ukázky. Tento krok budete automatizovat v tomto projektu.

Vytvořili jste název. Nyní je čas sestavit více uzlů do stromu vytvořením <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nový strom `name` používá jako levou stranu názvu a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> nový pro `Collections` obor názvů jako pravou stranu. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> Přidejte následující kód do `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Spusťte kód znovu a podívejte se na výsledky. Vytváříte strom uzlů, které představují kód. Budete pokračovat v <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> tomto modelu a vytvoříte pro obor názvů `System.Collections.Generic`. Přidejte následující kód do `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Spusťte program znovu a podívejte se, že jste sestavili strom pro kód, který chcete přidat.

### <a name="create-a-modified-tree"></a>Vytvořit upravený strom

Vytvořili jste malý strom syntaxe, který obsahuje jeden příkaz. Rozhraní API pro vytvoření nových uzlů jsou pravá volba pro vytváření jednoduchých příkazů nebo jiných malých bloků kódu. Chcete-li však vytvořit větší bloky kódu, měli byste použít metody, které nahradí uzly nebo vloží uzly do existujícího stromu. Nezapomeňte, že stromy syntaxe jsou neměnné. **Rozhraní API syntaxe** neposkytuje žádný mechanismus pro úpravu stávajícího stromu syntaxe po konstrukci. Místo toho poskytuje metody, které vytváří nové stromy založené na změnách stávajících. `With*`metody jsou definovány v konkrétních třídách, které <xref:Microsoft.CodeAnalysis.SyntaxNode> jsou odvozeny z nebo v metodách rozšíření deklarovaných ve <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> třídě. Tyto metody vytvoří nový uzel pomocí změn v podřízených vlastnostech existujícího uzlu. Kromě toho lze <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metodu rozšíření použít k nahrazení podřízeného uzlu v podstromu. Tato metoda také aktualizuje nadřazenou položku tak, aby odkazovala na nově vytvořený podřízený objekt, a tento proces se opakuje v celém stromu – jedná se o proces, který je známý jako _opakované rozmístění_ stromu.

Dalším krokem je vytvoření stromu, který představuje celý (malý) program, a pak ho upraví. Do začátku `Program` třídy přidejte následující kód:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Vzorový kód používá `System.Collections` obor názvů a nikoli `System.Collections.Generic` obor názvů.

Dále přidejte následující kód do dolní části `Main` metody pro analýzu textu a vytvoření stromu:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Tento příklad používá <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> metodu k nahrazení názvu v <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzlu jedním vytvořeným v předchozím kódu.

Vytvořte nový <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzel pomocí <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> metody pro aktualizaci `System.Collections` názvu s názvem, který jste vytvořili v předchozím kódu. Do dolní části `Main` metody přidejte následující kód:

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Spusťte program a pečlivě si prohlédněte výstup. `newusing` Nedošlo k umístění do kořenového stromu. Původní strom se nezměnil.

Přidejte následující kód pomocí metody <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> rozšíření pro vytvoření nového stromu. Nový strom je výsledkem nahrazení stávajícího importu aktualizovaným `newUsing` uzlem. Tomuto novému stromu přiřadíte existující `root` proměnnou:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Spusťte program znovu. Tentokrát strom nyní správně naimportuje `System.Collections.Generic` obor názvů.

### <a name="transform-trees-using-syntaxrewriters"></a>Transformovat stromy pomocí`SyntaxRewriters`

Metody `With*` a <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> poskytují pohodlný způsob, jak transformovat jednotlivé větve stromu syntaxe. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Třída provádí více transformací stromu syntaxe. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Třída je podtřídou třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Aplikuje transformaci na konkrétní typ <xref:Microsoft.CodeAnalysis.SyntaxNode>. Můžete použít transformace na více typů <xref:Microsoft.CodeAnalysis.SyntaxNode> objektů kdekoli, kde se zobrazí ve stromové struktuře syntaxe. Druhý projekt v tomto rychlém startu vytvoří refaktoring příkazového řádku, který odebere explicitní typy v deklaracích místních proměnných kdekoli, kde by bylo možné použít odvození typu.

Vytvoří nový projekt **Nástroje pro analýzu samostatného kódu** v jazyce C#. V aplikaci Visual Studio klikněte pravým tlačítkem `SyntaxTransformationQuickStart` myši na uzel řešení. Vyberte možnost **Přidat** > **Nový projekt** a zobrazte tak **dialogové okno Nový projekt**. V části**rozšiřitelnost**v jazyce **Visual C#** > vyberte **Nástroj pro analýzu**samostatného kódu. Pojmenujte `TransformationCS` projekt a klikněte na tlačítko OK.

Prvním krokem je vytvoření třídy, která je odvozena z <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> k provedení transformací. Přidejte do projektu nový soubor třídy. V aplikaci Visual Studio vyberte **projekt** > **Přidat třídu...**. V dialogovém okně **Přidat novou položku** zadejte `TypeInferenceRewriter.cs` název souboru.

Do `TypeInferenceRewriter.cs` souboru přidejte následující direktivy using:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Dále zajistěte `TypeInferenceRewriter` , aby třída <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> rozšířila třídu:

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Přidejte následující kód pro deklaraci soukromého pole jen pro čtení pro uložení <xref:Microsoft.CodeAnalysis.SemanticModel> a inicializaci v konstruktoru. Toto pole budete potřebovat později, abyste zjistili, kde lze použít odvození typu:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Přepsat <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metodu:

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Řada rozhraní API Roslyn deklaruje návratové typy, které jsou základními třídami skutečných běhových typů. V mnoha scénářích může být jeden druh uzlu nahrazen jiným typem uzlu zcela nebo dokonce odebrán. V tomto příkladu <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda vrací <xref:Microsoft.CodeAnalysis.SyntaxNode>místo odvozeného typu. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> Tento korektor vrátí nový <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> uzel založený na existujícím typu.

Tento rychlý Start zpracovává deklarace místních proměnných. Můžete ji zvětšit na jiné deklarace, jako jsou `foreach` cykly, `for` smyčky, výrazy LINQ a výrazy lambda. Kromě toho bude tento korektor transformovat jenom deklarace nejjednoduššího tvaru:

```csharp
Type variable = expression;
```

Pokud chcete prozkoumat vlastní průzkum, zvažte rozšíření dokončené ukázky pro tyto typy deklarací proměnných:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Do těla `VisitLocalDeclarationStatement` metody přidejte následující kód, který přeskočí přepis těchto forem deklarací:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metoda označuje, že žádné přepisy neprobíhá vrácením `node` parametru unmodified. Pokud žádný z těchto `if` výrazů není true, uzel představuje možnou deklaraci s inicializací. Přidejte tyto příkazy pro extrakci názvu typu zadaného v deklaraci a vytvoření vazby pomocí <xref:Microsoft.CodeAnalysis.SemanticModel> pole pro získání symbolu typu:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Nyní přidejte tento příkaz k vytvoření vazby na výraz inicializátoru:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Nakonec přidejte následující `if` příkaz, který nahradí existující název typu `var` klíčovým slovem, pokud typ výrazu inicializátoru odpovídá zadanému typu:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Podmíněný požadavek je vyžadován, protože deklarace může vypřetypovat výraz inicializátoru na základní třídu nebo rozhraní. Pokud je to požadováno, typy na levé a pravé straně přiřazení se neshodují. Odebrání explicitního typu v těchto případech způsobí změnu sémantiky programu. `var`je zadána jako identifikátor namísto klíčového slova, protože `var` je kontextové klíčové slovo. Úvodní a koncové minihry (prázdné znaky) jsou předány z starého názvu typu do `var` klíčového slova pro zachování vertikálního prázdného místa a odsazení. Je jednodušší použít `ReplaceNode` spíše než `With*` k transformaci, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> protože název typu je ve skutečnosti podřízeným příkazem deklarace.

Dokončili jste `TypeInferenceRewriter`. Nyní se vraťte do `Program.cs` souboru a dokončete příklad. Vytvoří test <xref:Microsoft.CodeAnalysis.Compilation> a získá <xref:Microsoft.CodeAnalysis.SemanticModel> z něj. Použijte ho <xref:Microsoft.CodeAnalysis.SemanticModel> k vyzkoušení `TypeInferenceRewriter`. Tento krok provedete jako poslední. Do té doby deklarujeme zástupnou proměnnou představující vaši kompilaci testů:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po pozastavení by se měla zobrazit chybová vlnovka, která hlásí, že žádná `CreateTestCompilation` metoda neexistuje. Stisknutím **kombinace kláves CTRL + tečka** otevřete žárovku a potom stiskněte klávesu ENTER pro vyvolání příkazu **vygenerovat metodu stub** . Tento příkaz vytvoří pro `CreateTestCompilation` metodu ve `Program` třídě zástupnou proceduru metody. Později se vrátíte k vyplnění této metody:

![C# generuje metodu z použití](./media/syntax-transformation/generate-from-usage.png)

Napište následující kód k iterování každého <xref:Microsoft.CodeAnalysis.SyntaxTree> v testu. <xref:Microsoft.CodeAnalysis.Compilation> Pro každou z nich inicializujte novou `TypeInferenceRewriter` pomocí <xref:Microsoft.CodeAnalysis.SemanticModel> pro tuto stromovou strukturu:

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

V rámci `foreach` příkazu, který jste vytvořili, přidejte následující kód, který provede transformaci na každém zdrojovém stromu. Tento kód podmíněně zapisuje novou transformované stromové struktury, pokud byly provedeny nějaké úpravy. Váš přepis by měl změnit pouze strom, pokud nalezne jeden nebo více deklarací místních proměnných, které by mohly být zjednodušeny pomocí odvození typu:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

V `File.WriteAllText` kódu by se měly zobrazit vlnovky. Vyberte žárovku a přidejte potřebný `using System.IO;` příkaz.

Skoro jste hotovi! Zbývá o jeden krok vlevo: vytváření testu <xref:Microsoft.CodeAnalysis.Compilation>. Vzhledem k tomu, že jste nepoužívali odvození typu v rámci tohoto rychlého startu, by se vytvořil dokonalý testovací případ. Vytvoření kompilace ze souboru projektu C# je mimo rámec tohoto návodu. Ať už se vám postupuje podle pokynů, buďte opatrní. Obsah metody `CreateTestCompilation` nahraďte následujícím kódem. Vytvoří kompilaci testů, který prochází podle projektu popsaného v tomto rychlém startu:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Mezi prsty a spusťte projekt. V aplikaci Visual Studio vyberte **ladit** > **Spustit ladění**. Měli byste být vyzváni v aplikaci Visual Studio, že se změnily soubory v projektu. Chcete-li znovu načíst změněné soubory, klikněte na tlačítko**Ano všem**. Prohlédněte si je a sledujte své supery. Všimněte si, že množství čisticího kódu vypadá bez všech těchto explicitních a redundantních specifikátorů typu.

Blahopřejeme! Použili jste **rozhraní API kompilátoru** k zápisu vlastního faktoru, který prohledává všechny soubory v projektu C# pro určité syntaktické vzory, analyzuje sémantiku zdrojového kódu, který odpovídá těmto vzorům, a transformuje ho. Teď jste oficiálně refaktoring autora!
