---
title: Úprava obsahu řetězce – Průvodce C#
description: Projděte si příklady několika postupů pro úpravu stávajícího obsahu řetězce v jazyce C#, který vrací nový objekt String.
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: ecce8857befc66353deea341d81f8c6e4313b951
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86473965"
---
# <a name="how-to-modify-string-contents-in-c"></a>Postup úpravy obsahu řetězce v jazyce C\#

Tento článek ukazuje několik postupů, jak vytvořit `string` úpravu existující `string` . Všechny techniky ukázaly, že vrátí výsledek úprav jako nový `string` objekt. Chcete-li Ukázat, že původní a upravený řetězec jsou odlišné instance, příklady uloží výsledek do nové proměnné. Můžete si prohlédnout původní `string` a nové, upravené `string` při spuštění každého příkladu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

V tomto článku je znázorněno několik postupů. Můžete nahradit existující text. Můžete vyhledat vzory a nahradit shodný text jiným textem. Řetězec lze považovat za sekvenci znaků. Můžete také použít praktické metody, které odstraňují prázdné znaky. Vyberte techniky, které nejlépe vyhovují vašemu scénáři.

## <a name="replace-text"></a>Nahradit text

Následující kód vytvoří nový řetězec nahrazením stávajícího textu náhradou.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet1":::

Předchozí kód ukazuje tuto *neproměnlivou* vlastnost řetězců. V předchozím příkladu se můžete podívat, že se původní řetězec `source` nemění. <xref:System.String.Replace%2A?displayProperty=nameWithType>Metoda vytvoří nový `string` obsahující úpravy.

<xref:System.String.Replace%2A>Metoda může nahradit buď řetězce, nebo jeden znak. V obou případech se nahradí všechny výskyty hledaného textu.  Následující příklad nahradí všechny ' ' znaky ' ' \_ :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet2":::

Zdrojový řetězec je nezměněný a je vrácen nový řetězec s náhradou.

## <a name="trim-white-space"></a>Oříznout prázdné znaky

Pomocí <xref:System.String.Trim%2A?displayProperty=nameWithType> metod, a můžete <xref:System.String.TrimStart%2A?displayProperty=nameWithType> <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> Odebrat všechny úvodní nebo koncové prázdné znaky.  Následující kód ukazuje příklad každého z nich. Zdrojový řetězec se nemění; Tyto metody vrátí nový řetězec se změněným obsahem.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet3":::

## <a name="remove-text"></a>Odebrat text

Můžete odebrat text z řetězce pomocí <xref:System.String.Remove%2A?displayProperty=nameWithType> metody. Tato metoda odebere počet znaků, které začínají na specifickém indexu. Následující příklad ukazuje, jak použít <xref:System.String.IndexOf%2A?displayProperty=nameWithType> následováno <xref:System.String.Remove%2A> k odebrání textu z řetězce:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet4":::

## <a name="replace-matching-patterns"></a>Nahradit vyhovující vzorce

[Regulární výrazy](../../standard/base-types/regular-expressions.md) můžete použít k nahrazení textu, který odpovídá vzorům, s novým textem, případně definovaným vzorem. Následující příklad používá <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídu k nalezení vzoru ve zdrojovém řetězci a jeho nahrazení se správnými velkými písmeny. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType>Metoda přebírá funkci, která poskytuje logiku náhrady jako jeden z jejích argumentů. V tomto příkladu je tato funkce `LocalReplaceMatchCase` **místní funkcí** deklarovanou uvnitř ukázkové metody. `LocalReplaceMatchCase`používá <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídu k sestavení řetězce pro nahrazení se správnými velkými písmeny.

Regulární výrazy jsou nejužitečnější pro vyhledávání a nahrazování textu, který následuje vzor, spíše než známý text. Další informace najdete v tématu [jak hledat řetězce](search-strings.md). Vzor hledání "the\s" vyhledá slovo "a" následovaný prázdným znakem. Tato část vzoru zajišťuje, že se neshoduje s "ve zdrojovém řetězci". Další informace o prvcích jazyka regulárních výrazů najdete v tématu [Jazyk regulárních výrazů – rychlé reference](../../standard/base-types/regular-expression-language-quick-reference.md).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet5":::

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>Metoda vrací neměnné řetězce s obsahem <xref:System.Text.StringBuilder> objektu.

## <a name="modifying-individual-characters"></a>Změna jednotlivých znaků

Můžete vytvořit pole znaků z řetězce, upravit obsah pole a pak vytvořit nový řetězec ze změněného obsahu pole.

Následující příklad ukazuje, jak nahradit sadu znaků v řetězci. Nejprve pomocí <xref:System.String.ToCharArray?displayProperty=nameWithType> metody vytvoří pole znaků. Používá <xref:System.String.IndexOf%2A> metodu k vyhledání počátečního indexu slova "Fox". Následující tři znaky jsou nahrazeny jiným slovem. Nakonec je nový řetězec vytvořen z aktualizovaného pole znaků.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet6":::

## <a name="programmatically-build-up-string-content"></a>Programové sestavení obsahu řetězce

Vzhledem k tomu, že řetězce jsou neměnné, předchozí příklady všechny vytvoří dočasné řetězce nebo znaková pole. Ve scénářích s vysokým výkonem může být žádoucí zabránit tomuto přidělení haldy. .NET Core poskytuje <xref:System.String.Create%2A?displayProperty=nameWithType> metodu, která umožňuje programově vyplnit obsah znaku v řetězci prostřednictvím zpětného volání a vyhnout se dostřednímu přidělení dočasného řetězce.

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet7":::

Můžete upravit řetězec v pevném bloku s nebezpečným kódem, ale **důrazně** nedoporučujeme upravovat obsah řetězce po vytvoření řetězce. Tím dojde k nepředvídatelným účelům. Například pokud někdo interně předává řetězec, který má stejný obsah jako váš, získá kopii a neočekává, že upravujete řetězec.

## <a name="see-also"></a>Viz také

- [.NET Framework regulární výrazy](../../standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)
