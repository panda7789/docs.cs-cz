---
title: Začínáme s syntaxe transformace (rozhraní Roslyn API)
description: Úvod do procházení, dotazování a procházení stromu syntaxe.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: c372b1ba1e08a7d3b57ceea0d4449d03e55a39cf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195707"
---
# <a name="get-started-with-syntax-transformation"></a>Začínáme s syntaxe transformace

Tento kurz vychází koncepty a techniky prozkoumali v [vám umožní začít analýza syntaxe](syntax-analysis.md) a [začít pracovat s sémantické analýzy](semantic-analysis.md) šablon rychlý start. Pokud jste tak dosud neučinili, by se měla dokončit tyto rychlé starty před zahájením tohoto objektu.

V tomto rychlém startu si projít techniky pro vytváření a transformace stromu syntaxe. V kombinaci s postupy, které jste se naučili v předchozích rychlých startů vytvoření vaší první příkazového řádku refaktoring!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Neměnnost a platformě .NET compiler platform

**Neměnnost** je základním principem .NET compiler platform. Neměnné datové struktury nelze změnit po jejich vytvoření. Neměnné datové struktury lze bezpečně sdílet a zároveň analyzují několik příjemců. Nehrozí nebezpečí, že tento jednoho příjemce má vliv na jiné nepředvídatelnými způsoby. Vaše analyzátor nemusí zámků nebo jiné míry souběžnosti. Toto pravidlo platí pro stromy syntaxe, kompilace, symboly, sémantickým modelům a každý další datová struktura, na které narazíte. Místo úpravy existujících struktur, rozhraní API vytvořit nové objekty podle zadaného rozdíly, staré. Tento koncept použijete na stromové struktury syntaxe pro vytvoření nové stromové struktury pomocí transformace.

## <a name="create-and-transform-trees"></a>Vytváření a transformace stromů

Zvolte jednu ze dvou strategií pro syntaxe transformace. **Metody pro vytváření objektů** jsou nejlepší použít při hledáte konkrétním uzlům nahradit, nebo konkrétní umístění, kam chcete vložit nový kód. **Programy** jsou nejlépe, když chcete ve vyhledávání celý projekt vzorky kódu, které mají být nahrazeny.

### <a name="create-nodes-with-factory-methods"></a>Vytvoření uzly pomocí metody pro vytváření objektů

První transformace syntaxe ukazuje metody pro vytváření objektů. Chystáte se nahradit `using System.Collections;` příkazem `using System.Collections.Generic;` příkazu. Tento příklad ukazuje, jak vytvořit <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> objektů pomocí <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metody pro vytváření objektů. Pro každý typ z **uzel**, **token**, nebo **triviální prvek** je metoda factory, který vytvoří instanci daného typu. Při vytváření stromu syntaxe vytváření uzly hierarchicky způsobem zdola nahoru. Potom budete transformace existující program nahrazujete stávající uzly s větve, které jste vytvořili.

Spusťte sadu Visual Studio a vytvořte nový C# **samostatný nástroj pro analýzu kódu** projektu. V sadě Visual Studio, zvolte **souboru** > **nový* > **projektu** zobrazíte dialogové okno Nový projekt. V části **Visual C#** > **rozšiřitelnost** zvolte **samostatný nástroj pro analýzu kódu**. V tomto rychlém startu má dva vzorové projekty, takže název řešení **SyntaxTransformationQuickStart**a název projektu **ConstructionCS**. Klikněte na tlačítko **OK**.

Tento projekt používá <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metody k vytvoření třídy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> představující `System.Collections.Generic` oboru názvů.

Přidejte následující použití direktivy k hornímu okraji `Program.cs` soubor k importu metod pro vytváření objektů <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> třídy a metody <xref:System.Console> tak, aby je mohli použít později bez kvalifikování:

[!code-csharp[import the SyntaxFactory class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Vytvoříte **název uzly syntaxe** k sestavení stromu, který představuje `using System.Collections.Generic;` příkazu. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> je základní třídou pro čtyři typy názvů, které se zobrazují v jazyce C#. Můžete vytvořit tyto čtyři typy názvů dohromady a vytvoří libovolný název, který se může objevit v jazyce C#:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, která představuje jednoduchý jeden identifikátor názvy jako `System` a `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, která představuje obecný typ nebo metoda název například `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, která představuje úplný název ve tvaru `<left-name>.<right-identifier-or-generic-name>` například `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, která představuje název sestavení extern alias takové použití `LibraryV2::Foo`.

Můžete použít <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> metodu pro vytvoření <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> uzlu. Přidejte následující kód do vašeho `Main` metoda ve `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Předchozí kód vytvoří <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> objektu a přiřadí ji do proměnné `name`. Mnohé z rozhraní Roslyn API vrátí základní třídy, aby bylo snazší pro práci s souvisejících typů. Proměnná `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, lze opětovně použít během vytváření <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nepoužívejte odvození typu proměnné, jak sestavit ukázku. Tento krok v tomto projektu budete automatizovat.

Vytvořili jste název. Nyní je čas vytvářet více uzlů do stromu podle budovy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Pomocí nového stromu `name` jako nalevo od názvu a nový <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> pro `Collections` oboru názvů jako pravá strana <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Přidejte následující kód, který `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Spusťte kód znovu a zobrazit výsledky. Strom uzlů, který představuje kód vytváříte. Tento model k sestavení bude pokračovat <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> pro obor názvů `System.Collections.Generic`. Přidejte následující kód, který `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Spusťte program znovu, abyste viděli, že jste při vytváření stromu pro kód pro přidání.

### <a name="create-a-modified-tree"></a>Vytvořte upravenou stromu

Začlenění stromu syntaxe. malé, který obsahuje jeden příkaz. Rozhraní API k vytvoření nové uzly jsou správná volba pro vytvoření jednotlivé příkazy nebo jiných malých blocích kódu. Ale pokud chcete sestavit větší bloky kódu, byste měli použít metody, které nahradí uzly nebo vložit uzlů do stávající strom. Mějte na paměti, že jsou neměnné stromu syntaxe. **Syntaxe API** neposkytuje žádný mechanismus pro úpravu existující stromu syntaxe. Po vytvoření. Místo toho poskytuje metody, které vytvářejí nové stromové struktury podle změn do existující aplikace. `With*` metody jsou definované v konkrétních tříd, které jsou odvozeny z <xref:Microsoft.CodeAnalysis.SyntaxNode> nebo v rozšiřující metody deklarované v <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> třídy. Tyto metody vytvoří nový uzel s použitím změn na stávající uzel podřízené vlastnosti. Kromě toho <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metody rozšíření lze použít k nahrazení potomka uzlu v podstrom. Tato metoda také aktualizuje nadřazené tak, aby odkazoval na nově vytvořený podřízenou položku a opakuje tento postup se celý strom - tento proces se označuje jako _re spining_ stromu.

Dalším krokem je vytvoření stromu, který představuje celou (malé) program a potom ho změnit. Přidejte následující kód do začátku `Program` třídy:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Příklad kódu používá `System.Collections` obor názvů, ne `System.Collections.Generic` oboru názvů.

V dalším kroku přidejte následující kód k dolnímu okraji `Main` metodu pro analýzu textu a vytvoření stromu:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

V tomto příkladu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> metody lze nahradit název v <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzlu s jedním vytvořený v předchozím kódu.

Vytvořte nový <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> pomocí uzlu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> způsob aktualizace `System.Collections` název s názvem, který jste vytvořili v předchozím kódu. Přidejte následující kód k dolnímu okraji `Main` metody:

[!code-csharp[create a new subtree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Spusťte program a podívejte se důkladně na výstupu. `newusing` Nebyl umístěn ve stromové struktuře root. Původní stromu nebylo změněno.

Přidejte následující kód s využitím <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metodu rozšíření k vytvoření nové větve. Nové stromové struktury je výsledek nahrazení stávající import aktualizované `newUsing` uzlu. Přiřazení této větve ke stávající `root` proměnné:

[!code-csharp[create a new root tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Spusťte program znovu. Tentokrát stromu nyní správně importuje `System.Collections.Generic` oboru názvů.

### <a name="transform-trees-using-syntaxrewriters"></a>Transformace stromů pomocí `SyntaxRewriters`

`With*` a <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metody poskytují pohodlný způsob, jak transformovat jednotlivých větvích stromu syntaxe. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Třída provádí více transformací ve stromu syntaxe. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Třída je podtřídou třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Platí pro konkrétní typ transformace <xref:Microsoft.CodeAnalysis.SyntaxNode>. Transformace můžete aplikovat více typů <xref:Microsoft.CodeAnalysis.SyntaxNode> objekty bez ohledu na to jsou uvedeny ve stromu syntaxe. Druhý projekt v tomto rychlém startu se vytvoří příkazového řádku refaktoring, který odebere explicitní typy v místní deklarace proměnných, které by bylo možné použít kdekoli, který odvození typu.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu. V sadě Visual Studio, klikněte pravým tlačítkem myši `SyntaxTransformationQuickStart` uzel řešení. Zvolte **přidat** > **nový projekt** zobrazíte **dialogu Nový projekt**. V části **Visual C#** > **rozšiřitelnost**, zvolte **samostatný nástroj pro analýzu kódu**. Pojmenujte svůj projekt `TransformationCS` a klikněte na tlačítko OK.

Prvním krokem je vytvoření třídy, která je odvozena z <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> provádět transformaci. Přidejte nový soubor třídy do projektu. V sadě Visual Studio, zvolte **projektu** > **přidat třídu...** . V **přidat novou položku** typ dialogu `TypeInferenceRewriter.cs` jako název souboru.

Přidejte následující direktivy using `TypeInferenceRewriter.cs` souboru:

[!code-csharp[add necessary usings](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Dále zkontrolujte, `TypeInferenceRewriter` rozšíření třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> třídy:

[!code-csharp[add base class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Přidejte následující kód, chcete-li deklarovat soukromé pole jen pro čtení pro uložení <xref:Microsoft.CodeAnalysis.SemanticModel> a inicializace v konstruktoru. Budete potřebovat toto pole později k určení, kde lze použít odvození typu proměnné:

[!code-csharp[initialize members](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Přepsat <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metody:

```C#
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Mnohé z rozhraní Roslyn API deklarovat návratové typy, které jsou základní třídy skutečné typy modulu runtime vrátila. n mnoho scénářů, jeden druh uzlu může být zcela - nahrazuje jiný druh uzlu nebo dokonce odebrat. V tomto příkladu <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda vrátí hodnotu <xref:Microsoft.CodeAnalysis.SyntaxNode>, namísto odvozeným typem tohoto <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Vrátí nový tento RW <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> uzel je založené na existující.

V tomto rychlém startu zpracovává deklarace místních proměnných. Můžete rozšířit ji do jiné deklarace, jako `foreach` smyčky, `for` smyčky, LINQ – výrazy a výrazy lambda. Kromě toho tento RW bude pouze transformace deklarací v nejjednodušší podobě:

```csharp
Type variable = expression;
```

Pokud budete chtít vyzkoušet sami, zvažte jeho rozšíření dokončení vzorku pro tyto typy deklarace proměnných:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Přidejte následující kód do těla `VisitLocalDeclarationStatement` metoda vynechá přepisování tyto formy deklarací:

[!code-csharp[exclude other declarations](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metoda označuje, že žádné přepisování probíhá tak, že vrací `node` parametr bez jakýchkoli úprav. Pokud ani jeden z nich `if` výrazy jsou splněny, představuje možné deklaraci inicializace uzel. Přidat tyto příkazy extrahovat název typu zadaného v deklaraci a vytvořit vazbu pomocí <xref:Microsoft.CodeAnalysis.SemanticModel> pole, které chcete získat typ symbolu:

[!code-csharp[extract type name](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Teď přidejte tento příkaz k vytvoření vazby inicializačního výrazu:

[!code-csharp[bind initializer](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Nakonec přidejte následující `if` příkaz Nahradit existující název typu se `var` – klíčové slovo, pokud zadaný typ odpovídá typu inicializačního výrazu:

[!code-csharp[ReplaceNode](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Replace the initializer node")]

Podmíněným totiž deklarace může hlasovat inicializačního výrazu na základní třídu nebo rozhraní. V případě potřeby, typy na levé a pravé straně přiřazení se neshodují. Odebrání explicitního typu v těchto případech by změnila sémantiku programu. `var` je zadán jako identifikátor místo klíčového slova, protože `var` je kontextové klíčové slovo. Úvodní a Koncové triviální prvek (prázdné znaky) jsou přenášena starý název typu má `var` – klíčové slovo k udržovat prázdné znaky svislé a odsazení. Je jednodušší použít `ReplaceNode` spíše než `With*` k transformaci <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> vzhledem k tomu, že název typu je ve skutečnosti podřízený příkazu deklarace.

Když jste dokončení `TypeInferenceRewriter`. Nyní vraťte se na vaše `Program.cs` souboru k dokončení příkladu. Vytvoření testu <xref:Microsoft.CodeAnalysis.Compilation> a získat <xref:Microsoft.CodeAnalysis.SemanticModel> z něj. Použít <xref:Microsoft.CodeAnalysis.SemanticModel> vyzkoušet vaše `TypeInferenceRewriter`. V tomto kroku budete používat poslední. Do té doby deklarujte proměnnou zástupný symbol představující váš test kompilace:

[!code-csharp[DeclareCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po pozastavení chvilku, měli byste vidět k chybě vlnovku zobrazovat sestavy, které žádný `CreateTestCompilation` metody existuje. Stisknutím klávesy **Ctrl + tečka** otevřít žárovku a potom stiskněte klávesu Enter k vyvolání **generovat Pahýl metody** příkazu. Tento příkaz bude generovat pahýl metody pro `CreateTestCompilation` metodu `Program` třídy. Budete přejdete zpět tak, aby vyplnil v této metodě později:

![Metoda jazyka C# generovat z využití](./media/syntax-transformation/generate-from-usage.png)

Zadejte následující kód k iteraci přes každý <xref:Microsoft.CodeAnalysis.SyntaxTree> v testu <xref:Microsoft.CodeAnalysis.Compilation>. U každé z nich, inicializovat nový `TypeInferenceRewriter` s <xref:Microsoft.CodeAnalysis.SemanticModel> pro stromové struktuře:

[!code-csharp[IterateTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Uvnitř `foreach` prohlášení, které jste vytvořili, přidejte následující kód k provedení transformace na každou stromu zdrojového kódu. Tento kód transformovaný větve podmíněně zapíše, pokud byly provedeny žádné změny. Vaše RW by měl změnit pouze stromu, pokud dojde nejmíň jeden místní deklarace proměnných, které by se dá zjednodušit pomocí odvození typu proměnné:

[!code-csharp[TransformTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Měli byste vidět podtržené vlnovkou `File.WriteAllText` kódu. Vyberte žárovku a přidejte nezbytné `using System.IO;` příkazu.

Téměř Hotovo! Je jednou krok vlevo: vytvoření testu <xref:Microsoft.CodeAnalysis.Compilation>. Vzhledem k tomu, že jste ještě používali odvození typu vůbec během tohoto rychlého startu, ji byste nastavit ideální testovacího případu. Bohužel vytvoření kompilaci ze souboru projektu C# je nad rámec tohoto návodu. Ale naštěstí Pokud jste postupovali podle pokynů pečlivě, je naděje. Nahraďte obsah `CreateTestCompilation` metodu s následujícím kódem. Vytvoří testovací kompilaci, která odpovídá shodou projektu je popsáno v tomto rychlém startu:

[!code-csharp[CreateTestCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Různé prsty a spuštění projektu. V sadě Visual Studio, zvolte **ladění** > **spustit ladění**. By měl být výzva pomocí sady Visual Studio, které se změnily soubory v projektu. Klikněte na tlačítko "**Ano všem**" znovu načíst upravené soubory. Prozkoumejte, je sledovat vaše úžasných funkcí. Všimněte si, kolik srozumitelnější kód vypadá bez všech těchto specifikátorech typu. explicitní a redundantní.

Blahopřejeme! Využili jste **rozhraní API kompilátoru** psát vlastní refaktoring, který vyhledá všechny soubory v projektu C# pro některé syntaktické vzorce analyzuje sémantiku zdrojový kód, který odpovídá tyto vzory a převede jej. Nyní jste oficiálně refaktoring Autor!