---
title: Použití modelu syntaxe .NET Compiler Platform SDK
description: Tento přehled poskytuje pochopení typů, které používáte pro pochopení a manipulaci se syntaxmi uzlů.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 940d2756ef7735ee96d38d0286f99fadf7b81dc6
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774104"
---
# <a name="work-with-syntax"></a>Práce se syntaxí

**Strom syntaxe** je základní struktura dat vystavená rozhraními API kompilátoru. Tyto stromy reprezentují lexikální a syntaktickou strukturu zdrojového kódu. Slouží k tomu dva důležité účely:

1. Pro povolení nástrojů, jako je IDE, doplňky, nástroje pro analýzu kódu a Refaktoring – pro zobrazení a zpracování syntaktické struktury zdrojového kódu v projektu uživatele.
2. Aby bylo možné povolit nástroje, jako je refaktoring a integrované vývojové prostředí (IDE) pro vytváření, úpravy a změny uspořádání zdrojového kódu, bez použití přímých úprav textu. Díky vytváření stromů a manipulaci s nimi můžou nástroje snadno vytvořit a změnit uspořádání zdrojového kódu.

## <a name="syntax-trees"></a>Stromy syntaxe

Stromy syntaxe jsou primární strukturou, která se používá pro kompilaci, analýzu kódu, vázání, refaktoring, funkce rozhraní IDE a generování kódu. Žádná část zdrojového kódu není chápána bez toho, aby byla identifikována a zařazena do jedné z mnoha dobře známých prvků strukturálního jazyka.

Stromy syntaxe mají tři klíčové atributy. Prvním atributem je, že stromy syntaxe uchovávají všechny informace o zdroji v plné přesnosti. To znamená, že strom syntaxe obsahuje všechny informace, které byly nalezeny ve zdrojovém textu, každé gramatické konstrukce, každý lexikální token a vše ostatní v rámci, včetně prázdných znaků, komentářů a direktiv preprocesoru. Například každý literál uvedený ve zdroji je reprezentován přesně tak, jak byl zadán. Stromy syntaxe také představují chyby ve zdrojovém kódu, pokud je program neúplný nebo poškozený pomocí reprezentace nebo chybějících tokenů ve stromu syntaxe.

To umožňuje druhý atribut stromové struktury syntaxe. Strom syntaxe získaný z analyzátoru může vytvořit přesný text, ze kterého byl analyzován. Z libovolného uzlu syntaxe je možné získat textovou reprezentaci podstromu root v tomto uzlu. To znamená, že stromy syntaxe lze použít jako způsob, jak vytvořit a upravit zdrojový text. Vytvořením stromu, který máte v důsledku vytvoření ekvivalentního textu, a úpravou stromu syntaxe tak, aby se nový strom nezměnil v existujícím stromu, byl text efektivně upravován.

Třetí atribut stromové struktury syntaxe je, že jsou neměnné a jsou bezpečné pro přístup z více vláken.  To znamená, že po získání stromu se jedná o snímek aktuálního stavu kódu a nikdy se nemění. To umožňuje více uživatelům pracovat se stejným stromem syntaxe ve stejnou dobu v různých vláknech bez uzamčení nebo duplikace. Vzhledem k tomu, že stromy jsou neměnné a nelze provádět změny přímo ve stromu, metody továrny pomohou vytvořit a upravit stromy syntaxe vytvořením dalších snímků stromu. Stromy jsou efektivní způsobem, jakým znovu používají podkladové uzly, takže je možné novou verzi znovu sestavit rychle a s trochu dodatečnou pamětí.

Strom syntaxe je doslova stromovou strukturou dat, kde neterminálové strukturální prvky nadřazené jiné prvky. Každý strom syntaxe je tvořen uzly, tokeny a minihry.

## <a name="syntax-nodes"></a>Uzly syntaxe

Uzly syntaxe jsou jedním z primárních prvků stromové struktury syntaxe. Tyto uzly reprezentují syntaktické konstrukce, jako jsou deklarace, příkazy, klauzule a výrazy. Jednotlivé kategorie uzlů syntaxe jsou reprezentovány samostatnou třídou odvozenou z <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Sada tříd uzlů není rozšiřitelná.

Všechny uzly syntaxe jsou uzly bez terminálů ve stromu syntaxe, což znamená, že mají vždy jiné uzly a tokeny jako podřízené objekty. Jako podřízený uzel jiného uzlu má každý uzel nadřazený uzel, ke kterému lze přistupovat prostřednictvím vlastnosti <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType>. Vzhledem k tomu, že uzly a stromy jsou neměnné, nadřazený uzel se nikdy nemění. Kořen stromu má nadřazený prvek s hodnotou null.

Každý uzel má <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metodu, která vrátí seznam podřízených uzlů v sekvenčním pořadí na základě jejich pozice ve zdrojovém textu. Tento seznam neobsahuje tokeny. Každý uzel obsahuje také metody pro prohlédnutí následníků, jako jsou <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A> nebo <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A>, které reprezentují seznam všech uzlů, tokenů nebo minihryů, které existují v podstromu, který je v tomto uzlu rootem.

Kromě toho každá podtřída uzlu syntaxe zveřejňuje všechny stejné podřízené objekty prostřednictvím vlastností silného typu. Například třída Node <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> obsahuje tři další vlastnosti, které jsou specifické pro binární operátory: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax> a typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> je <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Některé uzly syntaxe mají volitelné podřízené objekty. Například <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> má volitelný <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Pokud podřízená položka není k dispozici, vlastnost vrátí hodnotu null.

## <a name="syntax-tokens"></a>Syntaktické tokeny

Tokeny syntaxe jsou terminály jazykové gramatiky, které představují nejmenší syntaktické fragmenty kódu. Nejsou nikdy nadřazenými členy jiných uzlů nebo tokenů. Tokeny syntaxe se skládají z klíčových slov, identifikátorů, literálů a interpunkce.

Pro účely efektivity je typ <xref:Microsoft.CodeAnalysis.SyntaxToken> typ hodnoty CLR. Proto na rozdíl od uzlů syntaxe existuje pouze jedna struktura pro všechny druhy tokenů se směsí vlastností, které mají význam v závislosti na druhu tokenu, který je reprezentován.

Například celočíselný literálový token představuje číselnou hodnotu. Kromě nezpracovaného zdrojového textu, který token pokrývá, má literální token vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.Value>, která poskytuje přesné dekódování celočíselné hodnoty. Tato vlastnost je zapsána jako <xref:System.Object>, protože může být jedním z mnoha primitivních typů.

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> oznamuje stejné informace jako vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.Value>; Tato vlastnost je však vždy zadána jako <xref:System.String>. Identifikátor ve C# zdrojovém textu může obsahovat řídicí znaky Unicode, ale syntaxe samotné sekvence escape není považována za součást názvu identifikátoru. I když nezpracovaný text, který je předaný tokenem, zahrnuje řídicí sekvenci, vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> ne. Místo toho obsahuje znaky Unicode identifikované řídicím znakem. Pokud například zdrojový text obsahuje identifikátor napsaný jako `\u03C0`, pak vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> pro tento token vrátí `π`.

## <a name="syntax-trivia"></a>Minihry syntaxe

Syntaxe minihry představuje části zdrojového textu, které jsou převážně nevýznamné pro normální porozumění kódu, jako jsou prázdné znaky, komentáře a direktivy preprocesoru. Podobně jako tokeny syntaxe jsou minihry typy hodnot. Typ Single <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> slouží k popisu všech druhů minihry.

Vzhledem k tomu, že minihry nejsou součástí normální syntaxe jazyka a mohou se vyskytovat kdekoli mezi dvěma tokeny, nejsou zahrnuty ve stromové struktuře syntaxe jako podřízený uzel uzlu. Vzhledem k tomu, že jsou důležité při implementaci funkce, jako je refaktoring a udržování plné přesnosti se zdrojovým textem, existují v rámci stromu syntaxe.

K minihry se dostanete tak, že zkontrolujete kolekce <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> nebo <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType>y tokenu. Při analýze zdrojového textu jsou sekvence minihry přidruženy k tokenům. Obecně platí, že token vlastní minihry po stejném řádku až na další token. Všechny minihry po tomto řádku jsou přidruženy k následujícímu tokenu. První token ve zdrojovém souboru získá všechny počáteční minihry a poslední sekvence minihry v souboru se rozsměruje na token konce souboru, který má v opačném případě nulovou šířku.

Na rozdíl od syntaktických uzlů a tokenů syntaxe minihry neobsahuje rodiče. Vzhledem k tomu, že jsou součástí stromu a každá z nich je přidružena k jednomu tokenu, můžete získat přístup k tokenu, ke kterému je přidruženo, pomocí vlastnosti <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType>.

## <a name="spans"></a>Přes

Každý uzel, token nebo minihry ví svou polohu v rámci zdrojového textu a počtu znaků, ze kterých se skládá. Pozice textu je reprezentována jako 32ová celá čísla, což je index `char` založený na nule. Objekt <xref:Microsoft.CodeAnalysis.Text.TextSpan> je počáteční pozice a počet znaků, který je reprezentován jako celé číslo. Pokud má <xref:Microsoft.CodeAnalysis.Text.TextSpan> nulovou délku, odkazuje na umístění mezi dvěma znaky.

Každý uzel má dvě <xref:Microsoft.CodeAnalysis.Text.TextSpan> vlastnosti: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> a <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>.

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> je textový rozsah od začátku prvního tokenu v podstromu uzlu na konec posledního tokenu. Tento rozsah neobsahuje žádné počáteční ani koncové minihryy.

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> je textový rozsah, který zahrnuje normální rozpětí uzlu, a rozpětí všech úvodních a koncových minihry.

Příklad:

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Uzel příkazu uvnitř bloku má rozpětí vyznačené jednotlivými svislými pruhy (|). Obsahuje znaky `throw new Exception("Not right.");`. Celý rozsah je určen dvojitými svislými pruhy (| |). Obsahuje stejné znaky jako rozsah a znaky spojené s úvodním a koncovým minihry.

## <a name="kinds"></a>Druzí

Každý uzel, token nebo minihry má vlastnost <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> typu <xref:System.Int32?displayProperty=nameWithType>, která identifikuje přesný reprezentovaný prvek syntaxe. Tuto hodnotu lze přetypovat na výčet specifický pro jazyk; každý jazyk C# nebo VB má jeden `SyntaxKind` výčet (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> a <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>), který obsahuje seznam všech možných uzlů, tokenů a minihry prvků v gramatice. Tento převod lze provést automaticky přístupem k metodám rozšíření <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType>.

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> umožňuje snadnou nejednoznačnost typů uzlů syntaxe, které sdílejí stejnou třídu Node. Pro tokeny a minihry je tato vlastnost jediným způsobem, jak odlišit jeden typ prvku od jiného.

Například jedna třída <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> má <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jako podřízené objekty. Vlastnost <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> rozlišuje, zda se jedná o <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression> nebo <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> druh uzlu syntaxe.

## <a name="errors"></a>Vyskytl

I v případě, že zdrojový text obsahuje syntaktické chyby, je zveřejněn úplný strom syntaxe, který je k dispozici jako kulatý trippable do zdroje. Když analyzátor nalezne kód, který není v souladu s definovanou syntaxí jazyka, používá jeden ze dvou postupů pro vytvoření stromu syntaxe.

Za prvé, pokud analyzátor očekává určitý druh tokenu, ale nenalezne jej, může vložit chybějící token do stromu syntaxe v umístění, ve kterém byl token očekáván. Chybějící token představuje skutečný token, který se očekával, ale má prázdný rozsah a jeho vlastnost <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> vrací `true`.

Za druhé, analyzátor může přeskočit tokeny, dokud nenalezne ten, kde může pokračovat v analýze. V tomto případě jsou vynechané tokeny připojené jako minihry uzel s typem <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
