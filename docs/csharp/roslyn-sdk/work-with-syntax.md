---
title: Použití modelu syntaxe platformy kompilátoru .NET
description: Tento přehled poskytuje pochopení typů, které slouží k pochopení a manipulaci s uzly syntaxe.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: fc1b1f5ae5ec985425c8d6aec49ef7f830ea9162
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740470"
---
# <a name="work-with-syntax"></a>Práce se syntaxí

**Strom syntaxe** je základní datová struktura vystavená rozhraními API kompilátoru. Tyto stromy představují lexikální a syntaktickou strukturu zdrojového kódu. Slouží dvěma důležitým účelům:

1. Chcete-li povolit nástroje – například ide, doplňky, nástroje pro analýzu kódu a refaktoringy – pro zobrazení a zpracování syntaktické struktury zdrojového kódu v projektu uživatele.
2. Chcete-li povolit nástroje – například refaktoringy a ide – k vytvoření, úpravě a změně uspořádání zdrojového kódu přirozeným způsobem bez použití přímých úprav textu. Vytvořením a manipulací se stromy mohou nástroje snadno vytvářet a měnit uspořádání zdrojového kódu.

## <a name="syntax-trees"></a>Stromy syntaxe

Stromy syntaxe jsou primární struktura používaná pro kompilaci, analýzu kódu, vazbu, refaktoring, funkce IDE a generování kódu. Žádná část zdrojového kódu není pochopena, aniž by byla nejprve identifikována a rozdělena do jednoho z mnoha známých prvků strukturálního jazyka.

Stromy syntaxe mají tři klíčové atributy. První atribut je, že stromy syntaxe obsahovat všechny zdrojové informace v plné věrnosti. To znamená, že strom syntaxe obsahuje každou část informací, která se nachází ve zdrojovém textu, každé gramatické konstrukci, každém lexikálním tokenu a všem ostatním mezi nimi, včetně prázdného místa, komentářů a direktiv preprocesoru. Například každý literál uvedený ve zdroji je reprezentován přesně tak, jak byl zadán. Stromy syntaxe také představují chyby ve zdrojovém kódu, když je program neúplný nebo poškozený tím, že představuje přeskočené nebo chybějící tokeny ve stromu syntaxe.

To umožňuje druhý atribut stromy syntaxe. Strom syntaxe získaný z analyzátoru může vytvořit přesný text, ze kterého byl analyzován. Z libovolného syntaktického uzlu je možné získat textovou reprezentaci podstromu zakořeněnou v tomto uzlu. To znamená, že stromy syntaxe lze použít jako způsob, jak vytvořit a upravit zdrojový text. Vytvořením stromu, který jste implicitně vytvořili ekvivalentní text, a úpravou stromu syntaxe, vytvořením nového stromu ze změn existujícího stromu jste efektivně upravili text.

Třetí atribut stromy syntaxe je, že jsou neměnné a bezpečné pro přístup z více vláken.  To znamená, že po získání stromu je snímek aktuálního stavu kódu a nikdy se nezmění. To umožňuje více uživatelům pracovat se stejným stromem syntaxe současně v různých vláknech bez uzamčení nebo duplikace. Vzhledem k tomu, že stromy jsou neměnné a žádné změny lze provést přímo do stromu, metody výroby pomáhají vytvářet a upravovat stromy syntaxe vytvořením další snímky stromu. Stromy jsou efektivní ve způsobu, jakým znovu používají základní uzly, takže nová verze může být rychle znovu sestavena a s malou extra pamětí.

Strom syntaxe je doslova stromová datová struktura, kde neterminální strukturální prvky nadřazené jiným prvkům. Každý strom syntaxe se skládá z uzlů, tokenů a trivia.

## <a name="syntax-nodes"></a>Syntaktické uzly

Syntaktické uzly jsou jedním z primárních prvků stromů syntaxe. Tyto uzly představují syntaktické konstrukce, jako jsou deklarace, příkazy, klauzule a výrazy. Každá kategorie syntaktických uzlů je reprezentována <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>samostatnou třídou odvozenou z . Sada tříd uzlu není rozšiřitelná.

Všechny syntaktické uzly jsou mimo terminálové uzly ve stromu syntaxe, což znamená, že mají vždy jiné uzly a tokeny jako podřízené. Jako podřízený jiný uzel má každý uzel nadřazený uzel, <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> ke kterému lze přistupovat prostřednictvím vlastnosti. Vzhledem k tomu, že uzly a stromy jsou neměnné, nadřazený uzel se nikdy nezmění. Kořen stromu má nadřazenou hodnotu null.

Každý uzel má <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metodu, která vrací seznam podřízených uzlů v sekvenčním pořadí na základě jejich umístění ve zdrojovém textu. Tento seznam neobsahuje tokeny. Každý uzel má také metody pro zkoumání <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>Descendants, například , , nebo <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> - které představují seznam všech uzlů, tokenů nebo trivia, které existují v dílčím stromu zakořeněné tímto uzlem.

Kromě toho každý podtřída uzlu syntaxe zpřístupňuje všechny stejné podřízené položky prostřednictvím vlastností silného typu. Například třída <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> uzlu má tři další vlastnosti <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>specifické <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>pro <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>binární operátory: , , a . Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>a typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> je <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Některé syntaktické uzly mají volitelné podřízené. Například má <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> volitelné <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Pokud dítě není k dispozici, vlastnost vrátí null.

## <a name="syntax-tokens"></a>Syntaktické tokeny

Syntaktické tokeny jsou terminály jazykové gramatiky, které představují nejmenší syntaktické fragmenty kódu. Nikdy nejsou rodiče jiných uzlů nebo tokenů. Syntaktické tokeny se skládají z klíčových slov, identifikátorů, literál a interpunkce.

Pro účely účinnosti <xref:Microsoft.CodeAnalysis.SyntaxToken> je typ typu CLR. Proto na rozdíl od syntaktických uzlů existuje pouze jedna struktura pro všechny druhy tokenů se kombinací vlastností, které mají význam v závislosti na druhu tokenu, který je reprezentován.

Například symbol literálu celého čísla představuje číselnou hodnotu. Kromě nezpracovaného zdrojového textu, který token zahrnuje, <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> má literáltoken vlastnost, která vám sdělí přesnou dekódovanou celočíselnou hodnotu. Tato vlastnost je <xref:System.Object> zadána jako proto, že může být jedním z mnoha primitivních typů.

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> vám sdělí stejné <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> informace jako vlastnost; Tato vlastnost je však <xref:System.String>vždy zadánjako . Identifikátor ve zdrojovém textu jazyka C# může obsahovat řídicí znaky Unicode, ale syntaxe samotné sekvence escape není považována za součást názvu identifikátoru. Takže i když nezpracovaný text rozložený tokenem zahrnuje <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> řídicí sekvenci, vlastnost není. Místo toho obsahuje znaky Unicode identifikované escape. Pokud například zdrojový text obsahuje identifikátor `\u03C0`napsaný <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> jako , vrátí `π`se vlastnost tohoto tokenu .

## <a name="syntax-trivia"></a>Syntaxe trivia

Syntaxe trivia představují části zdrojového textu, které jsou do značné míry nevýznamné pro normální pochopení kódu, jako je například prázdné místo, komentáře a direktivy preprocesoru. Stejně jako syntaktické tokeny jsou trivia typy hodnot. Jediný <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> typ se používá k popisu všech druhů trivia.

Vzhledem k tomu, že trivia nejsou součástí syntaxe normálního jazyka a mohou se objevit kdekoli mezi libovolnými dvěma tokeny, nejsou zahrnuty do stromu syntaxe jako podřízený uzel. Přesto, protože jsou důležité při implementaci funkce, jako je refaktoring a zachovat plnou věrnost se zdrojovým textem, existují jako součást stromu syntaxe.

K trivia můžete získat přístup kontrolou <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> tokenu nebo kolekce. Při analýzě zdrojového textu jsou sekvence trivia spojeny s tokeny. Obecně platí, že token vlastní všechny trivia po něm na stejném řádku až do dalšího tokenu. Všechny trivia po tomto řádku je spojena s následujícím tokenem. První token ve zdrojovém souboru získá všechny počáteční drobnosti a poslední sekvence trivia v souboru je připevněna na token konce souboru, který má jinak nulovou šířku.

Na rozdíl od syntaktických uzlů a tokenů nemají syntaxe trivia rodiče. Přesto, protože jsou součástí stromu a každý je spojen s jedním tokenem, můžete <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> získat přístup k tokenu, ke který je přidružen pomocí vlastnosti.

## <a name="spans"></a>Rozpětí

Každý uzel, token nebo trivia zná své postavení ve zdrojovém textu a počet znaků, ze kterých se skládá. Pozice textu je reprezentována jako 32bitové celé číslo, `char` což je index založený na nule. Objekt <xref:Microsoft.CodeAnalysis.Text.TextSpan> je počáteční pozice a počet znaků, které jsou reprezentovány jako celá čísla. Pokud <xref:Microsoft.CodeAnalysis.Text.TextSpan> má nulovou délku, odkazuje na umístění mezi dvěma znaky.

Každý uzel má <xref:Microsoft.CodeAnalysis.Text.TextSpan> dvě <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A>vlastnosti: a .

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> je rozsah textu od začátku prvního tokenu v podstromu uzlu až do konce posledního tokenu. Toto rozpětí nezahrnuje žádné vedoucí nebo koncové maličkosti.

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A> je rozsah textu, který zahrnuje normální rozsah uzlu, plus rozpětí všech úvodních nebo koncových trivia.

Například:

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Uzel příkazu uvnitř bloku má rozpětí označené jednotlivými svislými pruhy (|). Obsahuje znaky `throw new Exception("Not right.");`. Celé rozpětí je indikováno dvojitými svislými pruhy (||). Obsahuje stejné znaky jako rozpětí a znaky spojené s úvodní a koncové trivia.

## <a name="kinds"></a>Druhů

Každý uzel, token nebo trivia <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> má vlastnost <xref:System.Int32?displayProperty=nameWithType>typu , která identifikuje přesný syntaktický prvek reprezentované. Tato hodnota může být přetypována do výčtu specifického pro jazyk. Každý jazyk, C# nebo Visual `SyntaxKind` Basic, má<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>jeden výčet ( a , v uvedeném pořadí), který obsahuje seznam všech možných uzlů, tokenů a trivia prvky v gramatické. Tento převod lze provést automaticky <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A?displayProperty=nameWithType> pomocí <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind%2A?displayProperty=nameWithType> přístupu k metodám nebo rozšíření.

Vlastnost <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> umožňuje snadnou rozdvojení typů uzlů syntaxe, které sdílejí stejnou třídu uzlu. Pro tokeny a trivia tato vlastnost je jediný způsob, jak odlišit jeden typ prvku od jiného.

<xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> Například jedna třída <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>má <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> , a jako děti. Vlastnost <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A> rozlišuje, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression> <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>zda <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> se jedná o uzel , , nebo druh syntaxe.

## <a name="errors"></a>chyby

I v případě, že zdrojový text obsahuje syntaktické chyby, je vystaven úplný strom syntaxe, který je ke zdroji round-trippable. Když analyzátor narazí na kód, který neodpovídá definované syntaxi jazyka, použije jednu ze dvou technik k vytvoření stromu syntaxe.

Za prvé, pokud analyzátor očekává určitý druh tokenu, ale nenajde ho, může vložit chybějící token do stromu syntaxe v umístění, které byl token očekáván. Chybějící token představuje skutečný token, který byl očekáván, ale <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> má `true`prázdné rozpětí a jeho vlastnost vrátí .

Za druhé analyzátor může přeskočit tokeny, dokud nenajde jeden, kde může pokračovat v analýzách. V tomto případě jsou přeskočené tokeny připojeny jako uzel <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>trivia s druhem .
