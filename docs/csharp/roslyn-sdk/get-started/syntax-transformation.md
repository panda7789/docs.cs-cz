---
title: Začínáme s transformace syntaxe (Roslyn rozhraní API)
description: Úvod k procházení, dotazování a proti stromy syntaxe.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 04053645b91e8f74e890340fb9bba66a4efdce0c
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231629"
---
# <a name="get-started-with-syntax-transformation"></a>Začínáme s syntaxe transformace

V tomto kurzu vychází koncepty a techniky prozkoumali v [začít pracovat s syntaxe analysis](syntax-analysis.md) a [začít pracovat s sémantického analysis](semantic-analysis.md) – elementy quickstart. Pokud jste to ještě neudělali, musíte provést před zahájením této jeden těchto rychlých průvodců.

V tento rychlý start prozkoumejte techniky pro vytváření a transformace stromy syntaxe. V kombinaci s postupy, které jste se naučili v předchozí – elementy QuickStart můžete vytvořit vaše první příkazového řádku refaktoring!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Neměnitelnosti a platformě .NET kompilátoru

**Neměnitelnosti** základní principem kompilátoru platformy .NET je. Neměnné datové struktury nelze změnit po vytváří. Neměnné datové struktury můžete bezpečně sdílet a analyzovat více příjemců současně. Nehrozí nebezpečí, že jednoho příjemce ovlivňuje jiné nepředvídatelně. Vaše analyzátor nepotřebuje zámky nebo jiných opatření souběžnosti. Toto pravidlo platí pro syntaxi stromy, kompilace, symbolů, sémantických modelů a každé další datová struktura, na které narazíte. Místo úprava existující struktury, rozhraní API vytvářet nové objekty, které jsou založené na zadaný rozdíly, o staré. Tento koncept použijete syntaxi stromů k vytvoření nových stromů použití transformací.

## <a name="create-and-transform-trees"></a>Vytvoření a transformace stromů

Vyberte jednu ze dvou strategií pro syntaxi transformace. **Metody vytváření** jsou nejvhodnější, pokud chcete vyhledat konkrétní uzlů nahradit nebo konkrétní umístění, kam chcete vložit nový kód. **Programy** se nejlíp, když chcete prohledat celý projekt pro vzory kódu, které má být nahrazen.

### <a name="create-nodes-with-factory-methods"></a>Vytvoření uzly s metodami pro vytváření

První transformace syntaxe ukazuje metodami pro vytváření. Chcete nahradit `using System.Collections;` příkaz s `using System.Collections.Generic;` příkaz. Tento příklad ukazuje, jak vytvořit <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> objekty pomocí <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metodami pro vytváření. Pro každý typ z **uzlu**, **tokenu**, nebo **trivia** je metoda factory, která vytvoří instanci daného typu. Při vytváření stromů syntaxe skládání uzly hierarchicky způsobem zdola nahoru. Potom budete transformace existující program nahrazujete stávající uzly s novou větev, které jste vytvořili.

Spuštění sady Visual Studio a vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu. V sadě Visual Studio, vyberte **soubor** > **nový* > **projektu** zobrazíte dialogové okno Nový projekt. V části **Visual C#** > **rozšiřitelnost** zvolte **samostatný nástroj pro analýzu kódu**. Tento rychlý start má dva projekty příklad, takže název řešení **SyntaxTransformationQuickStart**a název projektu **ConstructionCS**. Click **OK**.

Používá tento projekt <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metody pro vytvoření třídy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> představující `System.Collections.Generic` oboru názvů.

Přidejte následující using – direktiva do horní části `Program.cs` soubor k importu metody vytváření <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> třídy a metody <xref:System.Console> tak, aby je mohli používat později bez kvalifikace je:

[!code-csharp[import the SyntaxFactory class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Vytvoříte **název syntaxe uzly** k vytvoření stromové struktury, která představuje `using System.Collections.Generic;` příkaz. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> je základní třída pro čtyři typy názvů, které se zobrazují v jazyce C#. Můžete vytvořit tyto čtyři typy názvy dohromady a vytvoří libovolný název, který se může zobrazit v jazyce C#:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, která představuje jednoduchý jeden identifikátor názvy jako `System` a `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, která představuje obecný typ nebo metoda název, jako `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, která představuje kvalifikovaný název ve tvaru `<left-name>.<right-identifier-or-generic-name>` například `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, která představuje název pomocí sestavení extern alias takové `LibraryV2::Foo`.

Můžete použít <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> metodu pro vytvoření <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> uzlu. Přidejte následující kód ve vaší `Main` metoda v `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Předchozí kód vytvoří <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> objektu a přiřadí ji k proměnné `name`. Mnoho Roslyn rozhraní API vrátí základní třídy, aby bylo snazší pro práci s souvisejících typů. Proměnná `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, lze opětovně použít během vytváření <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nepoužívejte odvození typu, jak sestavit ukázku. Tento krok v tomto projektu budete automatizovat.

Název jste vytvořili. Nyní je čas vytvořit více uzlů do stromu podle budovy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Novou větev používá `name` jako nalevo od názvu a novou <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> pro `Collections` oboru názvů jako pravé straně <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Přidejte následující kód, který `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Znovu spustit kód a zobrazte si výsledky. Umožňuje vytvářet stromu uzly, který představuje kód. Tento vzor k vytvoření budete pokračovat <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> pro obor názvů `System.Collections.Generic`. Přidejte následující kód, který `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Spusťte program zjistíte, že jste sestavení stromu pro kódu k přidání.

### <a name="create-a-modified-tree"></a>Vytvoření upravené stromové struktury

Když jste sestavili malé syntaxe stromové struktury, která obsahuje jeden příkaz. Rozhraní API pro vytvoření nové uzly jsou správná volba pro vytvoření jedné příkazy nebo jiné bloky malý kód. Však vytvořit větší bloky kódu, byste měli použít metody, které nahradí uzly nebo vložit uzlů do stávající strom. Mějte na paměti, že syntaxe stromy jsou neměnné. **Syntaxe API** neposkytuje žádný mechanismus pro úpravy stávající strom syntaxe po konstrukce. Namísto toho poskytuje metody, které vytvářejí nové stromy na základě změn existující. `With*` metody jsou definovány v konkrétní třídy, které jsou odvozeny od <xref:Microsoft.CodeAnalysis.SyntaxNode> nebo v rozšiřující metody, které jsou deklarované v <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> třídy. Tyto metody vytvořte nový uzel použitím změny vlastnosti podřízené stávající uzel. Kromě toho <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metoda rozšíření lze použít k nahrazení podřízené uzlu v podstrom. Tato metoda také aktualizuje nadřazené tak, aby odkazovaly na nově vytvořený podřízené a opakuje tento proces se celý strom - tento proces se označuje jako _re spining_ stromu.

Dalším krokem je vytvoření stromové struktury, která představuje celou (malý) program a upravit ho. Přidejte následující kód do začátku `Program` třídy:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Příklad kódu používá `System.Collections` obor názvů a ne `System.Collections.Generic` oboru názvů.

V dalším kroku přidejte následující kód k dolnímu okraji `Main` metoda analyzovat text a vytvoření stromové struktury:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Tento příklad používá <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> metody lze nahradit název v <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzlu s jedním vytvořená v předchozím kódu.

Vytvořte novou <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> uzlu pomocí <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> metoda aktualizace `System.Collections` název s názvem, který jste vytvořili v předchozí kód. Přidejte následující kód k dolnímu okraji `Main` metoda:

[!code-csharp[create a new subtree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Spusťte program a pečlivě si prohlédněte výstup. `newusing` Nebyla umístěna ve stromové struktuře kořenové. Původní stromu nebyl změněn.

Přidejte následující kód pomocí <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> rozšíření metodu pro vytvoření nové větve. Novou větev je výsledkem nahraďte existující import aktualizovaný `newUsing` uzlu. Tento nový strom přiřadit stávající `root` proměnné:

[!code-csharp[create a new root tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Spusťte program znovu. Tentokrát stromu nyní správně importuje `System.Collections.Generic` oboru názvů.

### <a name="transform-trees-using-syntaxrewriters"></a>Transformace pomocí stromové struktury `SyntaxRewriters`

`With*` a <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metody poskytují pohodlný způsob, jak transformace jednotlivých větví stromu syntaxe. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Třída provádí více transformací stromu syntaxe. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Třída je podtřídou třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Transformace se vztahuje na určitý typ <xref:Microsoft.CodeAnalysis.SyntaxNode>. Transformace můžete použít pro více typů <xref:Microsoft.CodeAnalysis.SyntaxNode> objekty kdykoliv se objeví ve stromu syntaxe. Druhý projekt v tento rychlý start vytvoří příkazového řádku refaktoring, která odebere explicitní typy v místní deklarace proměnných, které by bylo možné použít kdekoli, který odvození typu.

Vytvoření nového jazyka C# **samostatný nástroj pro analýzu kódu** projektu. V sadě Visual Studio, klikněte pravým tlačítkem myši `SyntaxTransformationQuickStart` uzel řešení. Zvolte **přidat** > **nový projekt** zobrazíte **dialogové okno Nový projekt**. V části **Visual C#** > **rozšiřitelnost**, zvolte **samostatný nástroj pro analýzu kódu**. Název projektu `TransformationCS` a klikněte na tlačítko OK.

Prvním krokem je vytvoření třídu odvozenou z <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> k provádění vaší transformací. Přidáte nový soubor třídu do projektu. V sadě Visual Studio, vyberte **projektu** > **přidat třídu...** . V **přidat novou položku** typ dialogu `TypeInferenceRewriter.cs` jako název souboru.

Přidejte následující direktivy pro použití `TypeInferenceRewriter.cs` souboru:

[!code-csharp[add necessary usings](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Dále vytvořte `TypeInferenceRewriter` rozšíření třídy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> – třída:

[!code-csharp[add base class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Přidejte následující kód k deklaraci soukromé pole jen pro čtení k uložení <xref:Microsoft.CodeAnalysis.SemanticModel> a provést jeho inicializaci v konstruktoru. Budete potřebovat později na Chcete-li určit, kde lze použít odvození typu:

[!code-csharp[initialize members](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Přepsání <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda:

```C#
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Mnoho rozhraní API Roslyn deklarovat návratový typů, které jsou základní třídy typů skutečné runtime vrátila. n mnoho scénářů, jeden druh uzlu mohou být zcela - nahrazuje jiný druh uzlu nebo i odebrat. V tomto příkladu <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda vrátí <xref:Microsoft.CodeAnalysis.SyntaxNode>, místo odvozené typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Vrátí novou tento RW <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> uzlu podle stávající.

Tento rychlý start zpracovává místní deklarace proměnných. Ji můžete rozšířit do jiných deklarace, jako `foreach` smyčky, `for` smyčky, LINQ – výrazy a výrazy lambda. Kromě toho tato RW transformuje jenom deklarace nejjednodušší forma:

```csharp
Type variable = expression;
```

Pokud chcete prozkoumat, vezměte v úvahu rozšíření bylo dokončeno ukázka pro tyto typy deklarace proměnných:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Přidejte následující kód k tělu `VisitLocalDeclarationStatement` metoda tak, aby přeskočil přepisování tyto formuláře deklarace:

[!code-csharp[exclude other declarations](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metoda určuje, že žádné přepisování probíhá vrácením `node` parametr ponechat beze změny. Pokud žádná z nich `if` výrazy jsou splněny, představuje možné deklarace s inicializací uzel. Přidejte tyto příkazy k extrakci název typu, který je zadaný v deklaraci a navázat jej pomocí <xref:Microsoft.CodeAnalysis.SemanticModel> pole, které chcete získat symbol typu:

[!code-csharp[extract type name](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Nyní přidejte tento příkaz k vytvoření vazby inicializátoru výraz:

[!code-csharp[bind initializer](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Nakonec přidejte následující `if` příkaz, který má nahradit existující název typu s `var` – klíčové slovo, pokud typ výrazu inicializátoru odpovídá zadaný typ:

[!code-csharp[ReplaceNode](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Replace the initializer node")]

Zásad správy není nutná, protože deklaraci může přetypovat inicializátoru výraz, který se základní třídy nebo rozhraní. V případě potřeby, typy na levé a pravé straně přiřazení se neshodují. Odebírání explicitního typu v těchto případech změní sémantiku programu. `var` je zadán jako identifikátor, nikoli klíčové slovo, protože `var` je kontextové klíčové slovo. Úvodní a koncové trivia (prázdné) přenášených z původní název typu k `var` – klíčové slovo zachování svislé prázdné znaky a odsazení. Je jednodušší použít `ReplaceNode` místo `With*` k transformaci <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> vzhledem k tomu, že název typu je ve skutečnosti pod podřízená příkazu deklarace.

Když jste dokončení `TypeInferenceRewriter`. Nyní vraťte se do vaší `Program.cs` až se dokončí příklad souboru. Vytvoření testu <xref:Microsoft.CodeAnalysis.Compilation> a získat <xref:Microsoft.CodeAnalysis.SemanticModel> z něj. Použít <xref:Microsoft.CodeAnalysis.SemanticModel> pokusit vaší `TypeInferenceRewriter`. Tento krok můžete to udělat poslední. Do té doby deklarujte proměnnou zástupný symbol představující vaše testovací kompilace:

[!code-csharp[DeclareCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po pozastavení chvilku, měli byste vidět vlnovku chyba objeví, které žádné `CreateTestCompilation` metoda existuje. Stiskněte klávesu **Ctrl + tečka** otevřít žárovky a stiskněte klávesu Enter pro vyvolání **generovat se zakázaným inzerováním metoda** příkaz. Tento příkaz vytvoří metoda zástupnou proceduru pro `CreateTestCompilation` metoda v `Program` třídy. Můžete budete se vraťte k později vyplňte takto:

![Metoda C# generování před využitím](./media/syntax-transformation/generate-from-usage.png)

Uveďte následující kód, který iteraci každé <xref:Microsoft.CodeAnalysis.SyntaxTree> v testu <xref:Microsoft.CodeAnalysis.Compilation>. U každé z nich, inicializujte nový `TypeInferenceRewriter` s <xref:Microsoft.CodeAnalysis.SemanticModel> pro stromové struktuře:

[!code-csharp[IterateTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Uvnitř `foreach` příkaz jste vytvořili, přidejte následující kód k provedení transformace v každém stromu zdroje. Tento kód stromu nové transformovaných podmíněně zapíše, pokud byly provedeny veškeré úpravy. Vaše RW měli změnit, jenom stromu pokud zjistí jeden nebo více místní proměnné deklarace, které může zjednodušit pomocí odvození typu:

[!code-csharp[TransformTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Měli byste vidět podtržení vlnovkou pod `File.WriteAllText` kódu. Vyberte žárovky a přidejte nezbytné `using System.IO;` příkaz.

Téměř Hotovo! Je jednou vlevo krok: vytvoření testu <xref:Microsoft.CodeAnalysis.Compilation>. Vzhledem k tomu, že nebyly byla používáte odvození typu vůbec během tento rychlý start, by ho udělali ideální testovacího případu. Vytvoření kompilace ze souboru projektu C# bohužel je nad rámec tohoto návodu. Naštěstí, pokud jste se podle pokynů pečlivě, není naděje ale. Nahraďte obsah `CreateTestCompilation` metoda následujícím kódem. Vytvoří kompilace test, který shodou odpovídá projektu popsané v této rychlý start:

[!code-csharp[CreateTestCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Mezi prsty a spusťte projekt. V sadě Visual Studio, vyberte **ladění** > **spustit ladění**. Musí se vás Visual Studio, že se změnily soubory v projektu. Klikněte na tlačítko "**Ano všem**" načtením změněné soubory. Zkontrolujte, aby sledovat vaše awesomeness. Všimněte si, kolik čisticí proces kód vypadá bez všechny tyto specifikátory explicitní a redundantní typu.

Blahopřejeme! Jste použili **rozhraní API kompilátoru** zápis vlastní refaktoring, která hledá všechny soubory v projektu C# pro určité vzory syntaktické analyzuje sémantika zdrojový kód, který odpovídá tyto vzorce a převede jej. Nyní jste Autor oficiálně refaktoring!