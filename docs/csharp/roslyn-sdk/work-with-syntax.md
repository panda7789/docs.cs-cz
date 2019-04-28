---
title: Použití syntaxe modelu sada SDK platformy kompilátoru .NET
description: V tomto přehledu pochopení typů, které používáte k pochopení a manipulaci s uzlů syntaxe.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: a48d48168dffdb439c984f5b4209019514b3b970
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706595"
---
# <a name="work-with-syntax"></a>Práce se syntaxí

**Stromu syntaxe** je základní datová struktura vystavené kompilátoru rozhraní API. Tyto stromů představují lexikální nebo syntaktické struktury zdrojového kódu. Dvě důležité funkce slouží:

1. Povolit nástroje – například integrované vývojové prostředí, kódu doplňků, analytické nástroje a refaktoringy – naleznete v tématu a zpracovávat syntaktické konstrukce zdrojový kód v projektu uživatele.
2. K povolení nástrojů – například refaktoringů a integrované vývojové prostředí – Pokud chcete vytvořit, upravit a změna uspořádání zdrojový kód přirozeným způsobem, bez nutnosti použití s přímým přístupem textových úprav. Vytváření a manipulaci s stromové struktury, nástroje snadno vytvořit a uspořádat zdrojový kód.

## <a name="syntax-trees"></a>Syntaxe stromů

Syntaxi struktury jsou primární struktura používaná pro kompilaci, analýzy kódu, vazbu, refaktoring, funkce integrovaného vývojového prostředí a generování kódu. Žádná část zdrojového kódu je pochopitelné i bez ji nejdřív se identifikovat a rozdělená na jeden z mnoha prvků dobře známé strukturální jazyka. 

Syntaxi struktury mají tři klíčové atributy. První atribut je, že syntaxe stromů obsahovat všechny informace o zdroji v plnou věrností. To znamená, že obsahuje stromu syntaxe. Každá část informace nacházející se v zdrojový text, každý gramatické konstrukce, každý lexikální token a všechno ostatní mezi, včetně mezer, komentáře a direktivy preprocesoru. Například každý literál uvedených ve zdroji je reprezentován přesně tak, jak byl zadán. Stromové struktury syntaxe také představovat chyby ve zdrojovém kódu, pokud program je neúplná nebo poškozená představující chybí nebo přeskočené tokeny ve stromu syntaxe.  

To umožňuje druhý atribut stromu syntaxe. Strom syntaxe získané z analyzátor můžete vytvořit přesný text, který se získá analýzou z. Z libovolného uzlu syntaxi je možné získat textovou reprezentaci podstromě kořenovým adresářem v tomto uzlu. To znamená, že syntaxe stromů může sloužit jako způsob, jak vytvořit a upravit zdrojový text. Vytvořením větve, které máte již vytvořen odpovídající text a úpravou stromu syntaxe vytváření větve mimo změny na stávající strom, musíte upravit efektivně text. 

Třetí atribut stromu syntaxe je, že jsou neměnné a bezpečné pro vlákna.  To znamená, že po získání stromu je snímek aktuálního stavu kódu a nikdy nemění. To umožňuje více uživatelům interakci s stejném stromu syntaxe ve stejnou dobu v různých vláknech bez uzamčení nebo duplicity. Protože stromy jsou neměnné a provádět žádné úpravy přímo do stromu, metody pro vytváření objektů pomáhají vytvářet a upravovat tak, že vytvoříte další snímky stromu stromu syntaxe. Stromy jsou efektivní tak, jak jsou opakovaně používat podřízených uzlů, tak novou verzi můžete znovu sestavit rychle a s malou paměť navíc.

Strom syntaxe je doslova stromové struktury dat, kde není konečný konstrukční prvky nadřazené další prvky. Každý stromu syntaxe se skládá z uzlů, tokenů a triviální prvek.  

## <a name="syntax-nodes"></a>Syntaxe uzly

Syntaxe uzly jsou jedním z primárních prvků stromu syntaxe. Tyto uzly představují syntaktické konstrukce, jako je například prohlášení, příkazy, klauzule a výrazy. Každou kategorii syntaxe uzly představuje samostatnou třídu odvozenou z <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Sadu tříd uzel není rozšiřitelný. 

Všechny uzly syntaxe jsou není konečný uzlů ve stromu syntaxe, což znamená, že vždy mají ostatní uzly a tokeny jako podřízené objekty. Jako podřízený objekt jiného uzlu, každý uzel nemá nadřazený uzel, který je přístupný prostřednictvím <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> vlastnost. Protože jsou neměnné uzly a stromové struktury, nadřazený uzel se nikdy nemění. Kořen stromu má hodnotu null nadřazený prvek.  

Každý uzel má <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metodu, která vrátí seznam podřízených uzlů v pořadí podle jejich umístění ve zdrojovém textu. Tento seznam neobsahuje tokeny. Každý uzel má také metody prozkoumat, jako potomci, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>, nebo <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> – které představují seznam uzlů, tokeny nebo triviální prvek, který neexistuje v podstromě root k uzlu.  

Kromě toho každý uzel podtřídy syntaxe zpřístupňuje stejné děti prostřednictvím vlastnosti se silnými typy. Například <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> uzel třída má tři další vlastnosti specifické pro binární operátory: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>a typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> je <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Některé uzly syntaxe mít volitelné podřízené objekty. Například <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> má volitelnou <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Pokud podřízený není k dispozici, vlastnost vrací hodnotu null. 

## <a name="syntax-tokens"></a>Syntaxe tokenů

Syntaxe tokeny jsou terminály gramatiku jazyka představující nejmenší syntaktické fragmenty kódu. Jsou to nikdy nadřazených položek jinými uzly nebo tokeny. Syntaxe tokenů obsahovat klíčová slova, identifikátory, literály a interpunkční znaménka. 

Pro účely efektivitu <xref:Microsoft.CodeAnalysis.SyntaxToken> typ je typ hodnoty modulu CLR. Na rozdíl od syntaxe uzly, existuje tedy pouze jednu strukturu pro všechny druhy tokenů s využitím kombinace vlastnosti, které mají význam v závislosti na druhu token, který je reprezentované.

Například token literál celého čísla reprezentuje číselnou hodnotu. Kromě textu nezpracovaná zdrojová token rozsahy literál má token <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> vlastnost, která vám říká přesné dekódovat celočíselnou hodnotu. Tato vlastnost je zadán jako <xref:System.Object> vzhledem k tomu může být jedna z mnoha primitivní typy.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Vlastnost zjistíte stejné informace jako <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> vlastností, ale tato vlastnost je vždy typu <xref:System.String>. Identifikátor v C# zdrojový text může obsahovat řídicí znaky Unicode, ale syntaxe řídicí sekvence, samotný není považováno za součást název identifikátoru. Ano, i když nezpracovaný text předané token, který zahrnuje řídicí sekvence <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> vlastnost nepodporuje. Místo toho zahrnuje identifikované řídicí znaky Unicode. Například, pokud je zdrojový text obsahuje identifikátor zapsán jako `\u03C0`, pak bude <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> vrátí vlastnost pro tento token `π`.

## <a name="syntax-trivia"></a>Triviální prvek syntaxe

Triviální prvek syntaxe představují části zdrojového textu, které jsou do značné míry nevýznamné pro normální porozumění kódu, jako je například prázdné znaky, komentáře a direktivy preprocesoru. Triviální prvek jako syntaxe tokenů jsou typy hodnot. Jedné <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> typ se používá k popisu všech typů triviální prvek.

Protože triviální prvek nejsou součástí syntaxe jazyka běžné a může vyskytovat kdekoli mezi všechny dvěma tokeny, nejsou zahrnuty ve stromu syntaxe jako podřízený uzel. Zatím protože jsou tak důležité při implementaci funkce, jako je Refaktoring a zachovat plnou věrností s textem zdrojového, existují v rámci stromu syntaxe.

Triviální prvek se zpřístupní po kontrole token <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> nebo <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> kolekce. Pokud je zdrojový text analyzován, jsou spojeny s tokeny pořadí triviální prvek. Obecně platí vlastní token jakékoli triviální prvek za ním na stejném řádku až do další token. Žádné triviální prvek za tento řádek je přidružen následující token. Počáteční triviální prvek získá první token ve zdrojovém souboru, a poslední sekvence triviální prvek v souboru je skládaný na token souboru, který jinak má nulovou šířku.

Na rozdíl od syntaxe uzly a tokeny nemají syntaxi triviální prvek nadřazené položky. Zatím, protože jsou součástí stromu a každá je přidružen jeden token, můžete získat token, který je přidružen k použití <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> vlastnost.

## <a name="spans"></a>Rozpětí

Každý uzel, tokenem nebo triviální prvek ví jeho pozice v rámci zdrojového textu a počet znaků, které se skládá. Umístění textu je vyjádřena jako 32bitové celé číslo nulovým základem je `char` indexu. A <xref:Microsoft.CodeAnalysis.Text.TextSpan> objekt je počáteční pozice a počet znaků, obě vyjádřena jako celá čísla. Pokud <xref:Microsoft.CodeAnalysis.Text.TextSpan> má nulovou délku, odkazuje na umístění mezi dvěma znaky.

Každý uzel má dvě <xref:Microsoft.CodeAnalysis.Text.TextSpan> vlastnosti: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> a <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>. 

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> Vlastností je text rozpětí od samého začátku prvním tokenem v podstromě uzlu za účelem posledním tokenem. Tomuto rozpětí nezahrnuje žádné počáteční ani koncové triviální prvek.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> Rozpětí textu, který zahrnuje normální rozpětí uzlu funkce a v rozsahu žádné počáteční ani koncové triviální prvek je vlastnost.

Příklad: 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Příkaz uzel uvnitř bloku má rozpětí indikován jeden svislé čáry (|). Obsahuje znaky `throw new Exception("Not right.");`. Úplný rozsah je indikován double svislé čáry (|). Zahrnuje stejné znaky jako rozsah a související s triviální prvek úvodní a koncové znaky.

## <a name="kinds"></a>Typy

Každý uzel, tokenem nebo triviální prvek má <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> vlastnost typu <xref:System.Int32?displayProperty=nameWithType>, který identifikuje syntaxe elementu reprezentovaného. Tuto hodnotu lze převést na výčet konkrétní jazyk; Každý jazyk C# nebo VB, má jediný `SyntaxKind` výčet (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> a <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>v uvedeném pořadí), který obsahuje všechny možné uzlů, tokenů a triviální prvek prvky v gramatice. Tento převod může probíhat automaticky díky přístupu <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> metody rozšíření.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> Vlastnost umožňuje snadno odstraňování mnohoznačností syntaxe typy uzlů, které sdílejí stejný uzel třídy. Tokeny a triviální prvek tato vlastnost je jediný způsob, jak rozlišovat jeden typ prvku z jiného. 

Například jeden <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> třída má <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jako podřízené objekty. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> Vlastnost rozlišuje, zda se jedná <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>, nebo <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> druh uzlu syntaxe.

## <a name="errors"></a>Chyby

I v případě, že zdrojový text obsahuje chyby syntaxe, je přístupný úplnou syntaxi strom, který je odbavovaná ke zdroji. Když analyzátor narazí na kód, který není v souladu s definovanou syntaxe jazyka, používá jednu z dvě techniky k vytvoření stromu syntaxe.

Nejprve Pokud analyzátor očekává, že konkrétní druh tokenu, ale nebyl nalezen, můžou vložit chybí token do stromu syntaxe. v umístění, byl očekáván token. Chybí token představuje skutečný token, který byl očekáván, ale má prázdný značka span a jeho <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> vrátí vlastnost `true`.

Za druhé analyzátor může přeskočit tokeny, dokud nenalezne kde ho můžete pokračovat s analýzou. V tomto případě bylo přeskočeno tokeny jsou připojené jako uzel triviální prvek s druh <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
