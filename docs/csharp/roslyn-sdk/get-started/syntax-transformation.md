---
title: Začínáme s transformací syntaxe (Roslyn API)
description: Úvod do procházení, dotazování a chůze syntaxe stromy.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 5045dca839daba1070b34720e72cc9c4f7b94828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240607"
---
# <a name="get-started-with-syntax-transformation"></a>Začínáme s syntaktickou transformací

Tento kurz vychází z konceptů a technik prozkoumávaných v části [Začínáme s analýzou syntaxe](syntax-analysis.md) a Začínáme s rychlými starty [sémantické analýzy.](semantic-analysis.md) Pokud jste tak dosud neučinili, měli byste dokončit tyto rychlé starty před zahájením tohoto.

V tomto rychlém startu můžete prozkoumat techniky pro vytváření a transformaci stromů syntaxe. V kombinaci s technikami, které jste se naučili v předchozích rychlých startech, vytvoříte svůj první refaktoring příkazového řádku!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Neměnnost a platforma kompilátoru .NET

**Neměnnost** je základní princip platformy kompilátoru .NET. Neměnné datové struktury nelze po vytvoření změnit. Neměnné datové struktury mohou být bezpečně sdíleny a analyzovány více příjemci současně. Neexistuje žádné nebezpečí, že jeden spotřebitel ovlivňuje jiný nepředvídatelným způsobem. Analyzátor nepotřebuje zámky nebo jiné míry souběžnosti. Toto pravidlo platí pro stromy syntaxe, kompilace, symboly, sémantické modely a všechny ostatní datové struktury, se kterými se setkáte. Namísto úpravexistujících struktur vytvářejí api nové objekty na základě zadaných rozdílů se starými. Tento koncept použijete na stromy syntaxe k vytvoření nových stromů pomocí transformací.

## <a name="create-and-transform-trees"></a>Vytváření a transformace stromů

Můžete zvolit jednu ze dvou strategií pro transformace syntaxe. **Metody výroby** se nejlépe používají při hledání konkrétních uzlů, které chcete nahradit, nebo konkrétních umístění, kam chcete vložit nový kód. **Rewriters** jsou nejlepší, když chcete skenovat celý projekt pro vzory kódu, které chcete nahradit.

### <a name="create-nodes-with-factory-methods"></a>Vytvoření uzlů pomocí metod výroby

První syntaktické transformace ukazuje metody výroby. Nahradíte prohlášení `using System.Collections;` prohlášením. `using System.Collections.Generic;` Tento příklad ukazuje, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> jak vytvářet objekty pomocí <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metod výroby. Pro každý druh **uzlu**, **tokenu**nebo **trivia** je metoda factory, která vytvoří instanci tohoto typu. Stromy syntaxe vytvoříte hierarchicky vytvářením uzlů způsobem zdola nahoru. Potom transformujete existující program, který nahradí existující uzly novým stromem, který jste vytvořili.

Spusťte Visual Studio a vytvořte nový projekt **nástroje pro analýzu samostatného kódu** jazyka C#. V Sadě Visual Studio zvolte **Soubor** > **nový** > **projekt,** abyste zobrazili dialogové okno Nový projekt. V **části Visual C#** > **Rozšiřitelnost** zvolte **nástroj pro analýzu samostatného kódu**. Tento rychlý start má dva ukázkové projekty, proto pojmenujte řešení **SyntaxTransformationQuickStart**a pojmenujte projekt **ConstructionCS**. Klikněte na tlačítko **OK**.

Tento projekt <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> používá metody třídy k vytvoření <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> reprezentující obor `System.Collections.Generic` názvů.

Přidejte následující pomocí směrnice na `Program.cs` začátek souboru importovat metody <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> výroby <xref:System.Console> třídy a metody tak, aby je můžete použít později bez jejich kvalifikace:

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Vytvoříte **syntaxe uzlů názvu** k vytvoření stromu, který představuje `using System.Collections.Generic;` příkaz. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>je základní třída pro čtyři typy názvů, které se zobrazují v c#. Tyto čtyři typy názvů vytvoříte společně a vytvoříte libovolný název, který se může zobrazit v jazyce C#:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, který představuje jednoduché `System` názvy s jedním identifikátorem jako a `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, který představuje obecný typ nebo `List<int>`název metody, například .
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, který představuje kvalifikovaný název `<left-name>.<right-identifier-or-generic-name>` formuláře, například `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, který představuje název pomocí sestavení extern alias takové `LibraryV2::Foo`.

Metoda se <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> používá k <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> vytvoření uzlu. Přidejte do `Main` metody následující `Program.cs`kód v aplikaci :

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Předchozí kód vytvoří <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> objekt a přiřadí jej `name`proměnné . Mnoho roslyn api vrátit základní třídy, aby bylo snazší pracovat s související typy. Proměnnou `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>a , lze znovu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>použít při vytváření . Při vytváření ukázky nepoužívejte odvození typu. Budete automatizovat tento krok v tomto projektu.

Vytvořiljsi jméno. Nyní je čas vybudovat více uzlů do stromu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>tím, že staví . Nový strom `name` používá jako vlevo od názvu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> a `Collections` nový pro obor názvů <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>jako pravé straně . Do této části `program.cs`přidejte následující kód:

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Spusťte kód znovu a podívejte se na výsledky. Vytváříte strom uzlů, který představuje kód. Budete pokračovat v tomto vzoru <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> k vytvoření `System.Collections.Generic`pro obor názvů . Do této části `Program.cs`přidejte následující kód:

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Spusťte program znovu vidět, že jste vytvořili strom pro kód přidat.

### <a name="create-a-modified-tree"></a>Vytvoření upraveného stromu

Vytvořili jste malý strom syntaxe, který obsahuje jeden příkaz. Api pro vytvoření nových uzlů jsou správnou volbou pro vytvoření jednoho příkazu nebo jiných bloků malých kódů. Chcete-li však vytvořit větší bloky kódu, měli byste použít metody, které nahrazují uzly nebo vkládají uzly do existujícího stromu. Nezapomeňte, že stromy syntaxe jsou neměnné. Syntaxe **ROZHRANÍ API** neposkytuje žádný mechanismus pro úpravu existující ho stromu syntaxe po konstrukci. Místo toho poskytuje metody, které vytvářejí nové stromy na základě změn stávajících. `With*`metody jsou definovány v <xref:Microsoft.CodeAnalysis.SyntaxNode> konkrétních třídách, <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> které jsou odvozeny z metod rozšíření nebo v rozšiřujících metodách deklarovaných ve třídě. Tyto metody vytvoří nový uzel použitím změn na podřízené vlastnosti existujícího uzlu. Kromě toho <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metodu rozšíření lze nahradit potomkový uzel v podstromu. Tato metoda také aktualizuje nadřazený odkaz na nově vytvořené podřízené a opakuje tento proces až celý strom - proces známý jako _re-spinning_ stromu.

Dalším krokem je vytvoření stromu, který představuje celý (malý) program a pak jej upravit. Na začátek třídy `Program` přidejte následující kód:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Ukázkový kód `System.Collections` používá obor názvů `System.Collections.Generic` a nikoli obor názvů.

Dále přidejte následující kód na `Main` konec metody, abyste oddělili text a vytvořili strom:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Tento příklad <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> používá metodu k <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> nahrazení názvu v uzlu názvem vytvořeným v předchozím kódu.

Vytvořte <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> nový uzel <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> pomocí metody `System.Collections` k aktualizaci názvu s názvem, který jste vytvořili v předchozím kódu. Přidejte následující kód na `Main` konec metody:

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Spusťte program a pozorně se podívejte na výstup. Nebyl `newusing` aumístěn do kořenového stromu. Původní strom nebyl změněn.

Přidejte následující kód <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> pomocí metody rozšíření k vytvoření nového stromu. Nový strom je výsledkem nahrazení existujícího importu aktualizovaným `newUsing` uzlem. Tento nový strom přiřadíte existující `root` proměnné:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Spusťte program znovu. Tentokrát strom správně importuje `System.Collections.Generic` obor názvů.

### <a name="transform-trees-using-syntaxrewriters"></a>Transformace stromů pomocí`SyntaxRewriters`

Metody `With*` <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> a poskytují pohodlné prostředky k transformaci jednotlivých větví syntaktického stromu. Třída <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> provádí více transformací ve stromu syntaxe. Třída <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> je podtřídou <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. Použije <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> transformace na konkrétní typ <xref:Microsoft.CodeAnalysis.SyntaxNode>. Transformace můžete aplikovat na více <xref:Microsoft.CodeAnalysis.SyntaxNode> typů objektů všude tam, kde se zobrazují ve stromu syntaxe. Druhý projekt v tomto rychlém startu vytvoří refaktoring příkazového řádku, který odebere explicitní typy v deklaracích místních proměnných kdekoli, kde by mohl být použit odvození typu.

Vytvořte nový projekt **nástroje pro analýzu samostatného kódu** jazyka C#. V sadě Visual Studio `SyntaxTransformationQuickStart` klikněte pravým tlačítkem myši na uzel řešení. Zvolte **Přidat** > **nový projekt,** chcete-li zobrazit **dialogové okno Nový projekt**. V **části Visual C#** > **Rozšiřitelnost**zvolte **Nástroj pro analýzu samostatného kódu**. Pojmenujte `TransformationCS` projekt a klikněte na OK.

Prvním krokem je vytvořit třídu, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> která je odvozena od provádět transformace. Přidejte do projektu nový soubor třídy. V Visual Studiu zvolte **Project** > **Add Class...**. V dialogovém okně `TypeInferenceRewriter.cs` Přidat novou **položku** jako název souboru.

Do souboru přidejte `TypeInferenceRewriter.cs` následující příkazy pomocí direktiv:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Dále proveďte `TypeInferenceRewriter` třídu <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> rozšířit třídu:

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Přidejte následující kód deklarovat soukromé pole <xref:Microsoft.CodeAnalysis.SemanticModel> jen pro čtení držet a inicializovat v konstruktoru. Toto pole budete později potřebovat k určení, kde lze použít odvození typu:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Přepsat metodu: <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)>

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Mnoho roslyn ských api deklarovat návratové typy, které jsou základní třídy skutečné typy runtime vrácena. V mnoha scénářích může být jeden druh uzlu zcela nahrazen jiným druhem uzlu nebo dokonce odebrán. V tomto příkladu <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda <xref:Microsoft.CodeAnalysis.SyntaxNode>vrátí , namísto <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>odvozeného typu . Tento vypalovačka vrátí nový <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> uzel na základě existujícího uzlu.

Tento rychlý start zpracovává deklarace místní proměnné. Můžete rozšířit na další deklarace, `foreach` jako `for` jsou smyčky, smyčky, výrazy LINQ a lambda výrazy. Kromě toho tento vypalovačka transformuje pouze deklarace nejjednodušší formy:

```csharp
Type variable = expression;
```

Pokud chcete prozkoumat na vlastní pěst, zvažte rozšíření dokončené ukázky pro tyto typy deklarací proměnných:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Přidejte následující kód do `VisitLocalDeclarationStatement` těla metody přeskočit přepisování těchto forem deklarací:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metoda označuje, že žádné přepsání `node` probíhá vrácením parametru nezměněno. Pokud ani jeden `if` z těchto výrazů jsou pravdivé, uzel představuje možné prohlášení s inicializace. Přidejte tyto příkazy k extrahování názvu typu <xref:Microsoft.CodeAnalysis.SemanticModel> zadaného v deklaraci a svázání pomocí pole k získání symbolu typu:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Nyní přidejte tento příkaz svázat výraz inicializátoru:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Nakonec přidejte `if` následující příkaz, který nahradí `var` existující název typu klíčovým slovem, pokud typ výrazu inicializátoru odpovídá zadanému typu:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Podmínka je vyžadována, protože deklarace může přetypovat výraz inicializátoru do základní třídy nebo rozhraní. Pokud je to žádoucí, typy na levé a pravé straně přiřazení se neshodují. Odebrání explicitního typu v těchto případech by změnilo sémantiku programu. `var`je určen jako identifikátor, nikoli `var` klíčové slovo, protože je kontextové klíčové slovo. Úvodní a koncové drobnosti (prázdné místo) jsou převedeny ze `var` starého názvu typu na klíčové slovo zachovat svislé prázdné místo a odsazení. Je jednodušší použít `ReplaceNode` spíše `With*` než <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> transformovat, protože název typu je ve skutečnosti vnouče prohlášení prohlášení.

Dokončili jste `TypeInferenceRewriter`. Nyní se `Program.cs` vraťte do souboru a dokončete příklad. Vytvořte <xref:Microsoft.CodeAnalysis.Compilation> test a <xref:Microsoft.CodeAnalysis.SemanticModel> získat z něj. Použijte <xref:Microsoft.CodeAnalysis.SemanticModel> to vyzkoušet `TypeInferenceRewriter`. Tento krok uděláte jako poslední. Mezitím deklarujte zástupnou proměnnou představující testovací kompilaci:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po pozastavení chvíli, měli byste vidět chyba vlnovku se zobrazí hlášení, že neexistuje žádná `CreateTestCompilation` metoda. Stisknutím **kláves Ctrl+Period** otevřete žárovku a stisknutím klávesy Enter vyvoláte příkaz **Generovat se zakázaným inzerováním metody.** Tento příkaz vygeneruje zástupný `CreateTestCompilation` kód `Program` metody pro metodu ve třídě. Vrátíte se k vyplnění této metody později:

![C# Generovat metodu z použití](./media/syntax-transformation/generate-from-usage.png)

Napište následující kód iterát <xref:Microsoft.CodeAnalysis.SyntaxTree> přes <xref:Microsoft.CodeAnalysis.Compilation>každý v testu . Pro každý z nich inicializovat nový `TypeInferenceRewriter` s for tento <xref:Microsoft.CodeAnalysis.SemanticModel> strom:

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Uvnitř `foreach` příkazu, který jste vytvořili, přidejte následující kód k provedení transformace v každém zdrojovém stromu. Tento kód podmíněně zapíše nový transformovaný strom, pokud byly provedeny nějaké úpravy. Vypisovač by měl změnit strom pouze v případě, že narazí na jednu nebo více deklarací místních proměnných, které by mohly být zjednodušeny pomocí odvození typu:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Měli byste vidět klikyháky pod kódem. `File.WriteAllText` Vyberte žárovku a přidejte potřebný `using System.IO;` příkaz.

Už jsi skoro hotov! Je tu jednou krok vlevo: <xref:Microsoft.CodeAnalysis.Compilation>vytvoření testu . Vzhledem k tomu, že jste během tohoto rychlého startu vůbec nepoužívali odvození typu, bylo by to perfektní testovací případ. Bohužel vytvoření kompilace ze souboru projektu Jazyka C# je nad rámec tohoto návodu. Ale naštěstí, pokud jste byli pečlivě podle pokynů, je tu naděje. Obsah metody `CreateTestCompilation` nahraďte následujícím kódem. Vytvoří testovací kompilaci, která shodou okolností odpovídá projektu popsanému v tomto rychlém startu:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Zkřížit prsty a spustit projekt. V sadě Visual Studio zvolte **Ladění** > **ladění startování**. Měli byste být vyzváni Visual Studio, že soubory v projektu byly změněny. Klepnutím na tlačítko **"Ano všem"** znovu načtěte upravené soubory. Prozkoumejte je, abyste pozorovali vaši úžasnost. Všimněte si, kolik čistší kód vypadá bez všech těchto explicitní a redundantní specifikátory typu.

Blahopřejeme! Použili jste **kompilátor uapik** k napsání vlastní refaktoring, který prohledává všechny soubory v projektu C# pro určité syntaktické vzory, analyzuje sémantiku zdrojového kódu, který odpovídá tyto vzory a transformuje ji. Teď jsi oficiálně refaktorující autor!
