---
title: Použití syntaxe modelu SDK pro platformu .NET kompilátoru
description: Tento přehled poskytuje představu o typy, které slouží k pochopení a manipulaci s uzly syntaxe.
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 09d07e6257ad7d32d75328a8c1850888b4d0b937
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="work-with-syntax"></a>Práce s syntaxe

**Stromu syntaxe** je základní datová struktura vystavené kompilátoru rozhraní API. Tyto stromy představují lexikální a syntaktická strukturu zdrojového kódu. Představují důležité dva účely:

1. Povolit nástroje – například IDE, doplňky, nástrojů pro analýzu a kódu refaktoring - zobrazit a zpracovat syntaktické strukturu zdrojového kódu v projektu uživatele.
2. K povolení nástrojů – například refaktoring a IDE - Pokud chcete vytvořit, upravit a změna uspořádání zdrojového kódu přirozené způsobem bez nutnosti použití přímé textových úprav. Vytváření a manipulace s stromy, nástroje můžete snadno vytvořit a změna uspořádání zdrojového kódu.

## <a name="syntax-trees"></a>Syntaxe stromů

Syntaxe stromy jsou primární struktura používá pro kompilaci, analýza kódu, vazbu, refaktoring, funkce IDE a generování kódu. Žádná z částí zdrojový kód odhalíte bez nejprve se identifikovat a rozdělené do jednoho z mnoha dobře známé strukturální jazykové elementy. 

Syntaxe stromy mít tři klíčové atributy. První atribut je v úplné věrnosti obsahovat všechny informace o zdroji stromy syntaxe. To znamená, že ke stromu syntaxe obsahuje každá část informace o nacházejí v zdrojový text, každý gramaticky konstrukce, každý lexikální token a všem ostatním v mezi, včetně prázdný znak, komentáře a preprocesor – direktivy. Například každý literál uvedeno ve zdroji je reprezentována přesně tak, jak byl zadán. Stromy syntaxe také představovat chyby ve zdrojovém kódu, když program je neúplný nebo nesprávně představující chybí nebo přeskočené tokeny ve stromu syntaxe.  

To umožňuje druhý atribut stromy syntaxe. Text, který se získá analýzou z přesně může vytvářet získané z analyzátor stromu syntaxe. Z libovolného uzlu syntaxe je možné získat textovou reprezentaci, dílčí stromu kořenem v tomto uzlu. To znamená, že syntaxe stromy lze použít jako způsob, jak vytvořit a upravit zdrojový text. Vytvořením stromu, které máte nepřímo vytvořit ekvivalentní text a úpravou stromu syntaxe vytváření novou větev změny mimo na stávající strom upravíte efektivně text. 

Třetí atribut syntaxe stromů je, že jsou neměnné a bezpečné pro přístup z více vláken.  To znamená, že po získání stromu je snímek aktuálního stavu kódu a nikdy se změní. To umožňuje více uživatelům interakci s stejném stromu syntaxe ve stejnou dobu v různých vláknech bez zamknutí nebo duplicita. Protože stromy jsou neměnné a žádné úpravy můžete provedeny přímo do stromu, metodami pro vytváření pomoci vytvořit a upravit tak, že vytvoříte další snímky stromu syntaxe stromy. Stromy jsou efektivní ve způsobu, jakým se opakovaně základní uzly, tak novou verzi může být znovu sestavit rychlých a s malým množstvím paměť navíc.

Stromu syntaxe je oznámena stromová struktura dat, kde není konečný strukturální elementy nadřazených další prvky. Každý stromu syntaxe se skládá z uzlů, tokeny a trivia.  

## <a name="syntax-nodes"></a>Syntaxe uzly

Syntaxe uzly jsou jedním z primární elementy stromy syntaxe. Tyto uzly představují syntaktické konstrukce, jako je například deklarace, příkazy, výrazy a klauzule. Každou kategorii uzly syntaxe je reprezentována samostatné třídy odvozené od <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Sada tříd uzlu není rozšiřitelný. 

Není konečný uzly ve stromu syntaxe, což znamená, že vždy mají ostatní uzly a tokeny jako podřízené objekty jsou všechny uzly syntaxe. Jako podřízený jiného uzlu, každý uzel má nadřazený uzel, který se dá dostat <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> vlastnost. Vzhledem k tomu, že jsou neměnné uzly a stromy, změní se nikdy nadřazeného uzlu. Kořen stromu má hodnotu null. nadřazený.  

Každý uzel má <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metoda, která vrátí seznam podřízené uzly v postupném pořadí podle jejich pozice v textu zdroje. Tento seznam neobsahuje tokeny. Každý uzel má také metody prozkoumat následníky, jako například <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>, nebo <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> – které představují seznam uzlů, tokeny nebo trivia, který neexistuje ve stromové struktuře dílčí root uzlu.  

Kromě toho každý uzel podtřídami syntaxe zpřístupňuje stejné podřízené objekty prostřednictvím vlastnosti silného typu. Například <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> uzlu třída má tři další vlastnosti, které jsou specifické pro binární operátory: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> je <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>a typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> je <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Některé uzly syntaxe mít volitelné podřízené položky. Například <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> má volitelný <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Pokud podřízená není k dispozici, vrátí hodnotu null vlastnosti. 

## <a name="syntax-tokens"></a>Syntaxe tokenů

Syntaxe tokeny jsou terminály gramatika jazyka, která reprezentuje nejmenší syntaktické fragmenty kódu. Nikdy jsou rodičů jiných uzlů nebo tokenů. Syntaxe tokenů obsahovat klíčová slova, identifikátory, literály a interpunkce. 

Pro účely efektivitu <xref:Microsoft.CodeAnalysis.SyntaxToken> typ je typ CLR hodnotu. Na rozdíl od syntaxe uzly neexistuje tedy pouze jeden struktury pro všechny typy tokenů se smíšenými vlastnosti, které mají význam v závislosti na druhu token, který je reprezentované.

Například token literálu celé číslo reprezentuje číselnou hodnotu. Kromě nezpracovaná zdrojový text tokenu rozsahy literálu token má <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> vlastnost, která zjistíte přesný dekódovat celočíselnou hodnotu. Tato vlastnost je zadán jako <xref:System.Object> vzhledem k tomu může být jeden z mnoha primitivní typy.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Vlastnost zjistíte stejné informace, jako <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> vlastnost; ale tato vlastnost je vždy typu <xref:System.String>. Identifikátor v C# zdrojový text může zahrnovat řídicí znaky Unicode, ale syntaxe řídicí sekvence samotné není považovány za součást název identifikátoru. Ano, i když nezpracovaný text předané token nezahrnuje řídicí sekvence <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> vlastnost neexistuje. Místo toho zahrnuje identifikovaný řídicí znaky Unicode. Pokud zdrojový text obsahuje identifikátor zapisují jako například `\u03C0`, pak se <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> vlastnost pro tento token vrátí `π`.

## <a name="syntax-trivia"></a>Syntaxe trivia

Syntaxe trivia představují části textu zdroje, které jsou z velké části zanedbatelné pro normální pochopení kódu, například prázdný znak, komentáře a preprocesor – direktivy. Podobně jako syntaxe tokenů trivia jsou typy hodnot. Jedné <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> typ se používá k popisu nejrůznějších druhy trivia.

Protože trivia nejsou součástí normálního jazykové syntaxe a může vyskytovat kdekoli mezi dvěma tokenů, nejsou zahrnuty ve stromu syntaxe jako podřízený uzel. Ještě protože jsou důležité při implementaci funkce jako Refaktoring a udržovat úplné věrnosti textem zdroje, existují v rámci stromu syntaxe.

Dostanete trivia zkontrolováním token <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> nebo <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> kolekce. Pokud je zdrojový text analyzovat, jsou spojeny s tokeny pořadí trivia. Obecně platí token vlastní žádné trivia za ním na stejném řádku až na další token. Všechny trivia po daného řádku je přidružen následující token. Získá počáteční trivia prvního tokenu ve zdrojovém souboru, a poslední pořadí trivia v souboru je standardní na token end souboru, který jinak má nulové šířku.

Na rozdíl od syntaxe uzly a tokeny nemají syntaxe trivia nadřazené položky. Ještě, protože jsou součástí stromové struktuře a každé je přidružen jeden token, můžete získat token je spojené s použitím <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> vlastnost.

## <a name="spans"></a>Rozpětí

Každý uzel, token nebo trivia zná pozici v rámci zdrojový text a počet znaků, které obsahuje. Na pozici textu je reprezentován jako 32bitové celé číslo nulovým základem je `char` index. A <xref:Microsoft.CodeAnalysis.Text.TextSpan> objekt počáteční pozice a počet znaků, obě vyjádřena jako celá čísla. Pokud <xref:Microsoft.CodeAnalysis.Text.TextSpan> má nulové délky, odkazuje na umístění mezi dva znaky.

Každý uzel má dva <xref:Microsoft.CodeAnalysis.Text.TextSpan> vlastnosti: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> a <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>. 

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> Vlastnost je text období od začátku prvního tokenu v uzlu stromu dílčí na konec posledního token. Toto rozpětí nezahrnuje žádné trivia začátku nebo na konci.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> Vlastnost je značka span textu, která zahrnuje normální rozpětí uzlu plus rozpětí žádné trivia začátku nebo na konci.

Příklad: 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Příkaz uzel uvnitř bloku má rozpětí indikován jeden svislé čáry (|). Obsahuje znaky `throw new Exception("Not right.");`. Úplná značka span je indikován dvojité svislé čáry (|). Obsahuje stejné znaky jako rozpětí a přidružené trivia úvodní a koncové znaky.

## <a name="kinds"></a>Typy

Má každý uzel, token nebo trivia <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> vlastnost typu <xref:System.Int32?displayProperty=nameWithType>, identifikující reprezentované element Přesná syntaxe. Tato hodnota může být převeden na konkrétní jazyk výčet; Každý jazyk C# nebo VB, má jeden `SyntaxKind` – výčet (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> a <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>, v uvedeném pořadí), jsou uvedeny všechny možné uzlů, tokeny a trivia prvky v gramatice. Tento převod je možné provést automaticky přímým přístupem <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> nebo <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> rozšiřující metody.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> Vlastnost umožňuje snadno rozlišení více tras syntaxe uzlu typů, které sdílejí stejnou třídu uzlu. Pro tokeny a trivia tato vlastnost je jediný způsob, jak z jiné rozlišení jeden typ elementu. 

Například jeden <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> třída má <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jako podřízené objekty. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> Vlastnost odlišuje toho, jestli je <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>, nebo <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> druh uzlu syntaxe.

## <a name="errors"></a>Chyby

I v případě, že zdrojový text obsahuje syntaktické chyby, je vystaven úplnou syntaxí stromové struktury, která je odbavovaná ke zdroji. Pokud analyzátor nalezne kód, který není v souladu s definovanou syntaxe jazyka, používá jednu z dvě techniky k vytvoření stromu syntaxe.

První Pokud analyzátor očekává konkrétní typ tokenu, ale nebyl nalezen, může vložit chybějící token do stromu syntaxe v umístění, aby byl očekáván token. Představuje skutečný token, který byl očekáván token chybí, ale má prázdný span a jeho <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> vlastnost vrátí `true`.

Analyzátor, druhý může přeskočit tokeny, dokud nenalezne kde může pokračovat, analýze. V takovém případě jsou přeskočené tokeny připojené jako uzel trivia s druh <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
