---
title: Postup úpravy obsahu řetězce – C# Průvodce
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: ecedd9a9027aa925c753f8e187d611b19d3db991
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543258"
---
# <a name="how-to-modify-string-contents-in-c"></a>Postup úpravy obsahu řetězce v jazyce C\#

Tento článek ukazuje několik postupů, jak vytvořit `string` úpravou stávajícího `string`. Všechny techniky ukázaly, že vrátí výsledek úprav jako nový objekt `string`. Pokud to chcete jasně ukázat, příklady všechny ukládají výsledek do nové proměnné. Pak můžete prošetřit původní `string` i `string`, které se při spuštění každého příkladu vyplývají z úprav.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

V tomto článku je znázorněno několik postupů. Můžete nahradit existující text. Můžete vyhledat vzory a nahradit shodný text jiným textem. Řetězec lze považovat za sekvenci znaků. Můžete také použít praktické metody, které odstraňují prázdné znaky. Měli byste zvolit techniky, které nejlépe vyhovují vašemu scénáři.

## <a name="replace-text"></a>Nahradit text

Následující kód vytvoří nový řetězec nahrazením stávajícího textu náhradou.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Předchozí kód ukazuje tuto *neproměnlivou* vlastnost řetězců. V předchozím příkladu můžete vidět, že původní řetězec, `source`, se nezmění. Metoda <xref:System.String.Replace%2A?displayProperty=nameWithType> vytvoří nové `string` obsahující úpravy.

Metoda <xref:System.String.Replace%2A> může nahradit buď řetězce, nebo jeden znak. V obou případech se nahradí všechny výskyty hledaného textu.  Následující příklad nahrazuje všechny znaky ' ' ' s '\_':

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Zdrojový řetězec je nezměněný a je vrácen nový řetězec s náhradou.

## <a name="trim-white-space"></a>Oříznout prázdné znaky

Pomocí metod <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>a <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> můžete odebrat všechny úvodní a koncové prázdné znaky.  Následující kód ukazuje příklad každého z nich. Zdrojový řetězec se nemění; Tyto metody vrátí nový řetězec se změněným obsahem.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Odebrat text

Text z řetězce můžete odebrat pomocí metody <xref:System.String.Remove%2A?displayProperty=nameWithType>. Tato metoda odebere počet znaků, které začínají na specifickém indexu. Následující příklad ukazuje, jak použít <xref:System.String.IndexOf%2A?displayProperty=nameWithType> následovaných <xref:System.String.Remove%2A> k odebrání textu z řetězce:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Nahradit vyhovující vzorce

[Regulární výrazy](../../standard/base-types/regular-expressions.md) můžete použít k nahrazení textu, který odpovídá vzorům, s novým textem, případně definovaným vzorem. Následující příklad používá třídu <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> k nalezení vzoru ve zdrojovém řetězci a jeho nahrazení se správnými velkými písmeny. Metoda <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> přebírá funkci, která poskytuje logiku náhrady jako jeden z jejích argumentů. V tomto příkladu je tato funkce `LocalReplaceMatchCase` **lokální funkci** deklarovanou uvnitř ukázkové metody. `LocalReplaceMatchCase` používá třídu <xref:System.Text.StringBuilder?displayProperty=nameWithType> k sestavení řetězce pro nahrazení se správnými velkými písmeny.

Regulární výrazy jsou nejužitečnější pro vyhledávání a nahrazování textu, který následuje vzor, spíše než známý text. Další podrobnosti najdete v tématu [jak hledat řetězce](search-strings.md) . Vzor hledání "the\s" vyhledá slovo "a" následovaný prázdným znakem. Tato část vzoru zajišťuje, že se neshoduje s "ve zdrojovém řetězci". Další informace o prvcích jazyka regulárních výrazů najdete v tématu [Jazyk regulárních výrazů – rychlé reference](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

Metoda <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> vrací neměnné řetězce s obsahem v objektu <xref:System.Text.StringBuilder>.

## <a name="modifying-individual-characters"></a>Změna jednotlivých znaků

Můžete vytvořit pole znaků z řetězce, upravit obsah pole a pak vytvořit nový řetězec ze změněného obsahu pole.

Následující příklad ukazuje, jak nahradit sadu znaků v řetězci. Nejprve používá metodu <xref:System.String.ToCharArray?displayProperty=nameWithName> k vytvoření pole znaků. Používá metodu <xref:System.String.IndexOf%2A> k vyhledání počátečního indexu slova "Fox". Následující tři znaky jsou nahrazeny jiným slovem. Nakonec je nový řetězec vytvořen z aktualizovaného pole znaků.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Programové sestavení obsahu řetězce

Vzhledem k tomu, že řetězce jsou neměnné, předchozí příklady všechny vytvoří dočasné řetězce nebo znaková pole. Ve scénářích s vysokým výkonem může být žádoucí zabránit tomuto přidělení haldy. .NET Core poskytuje metodu <xref:System.String.Create%2A?displayProperty=nameWithType>, která umožňuje programově vyplnit obsah znaku v řetězci prostřednictvím zpětného volání a vyhnout se dostřednímu přidělení dočasného řetězce.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Můžete upravit řetězec v pevném bloku s nebezpečným kódem, ale **důrazně** nedoporučujeme upravovat obsah řetězce po vytvoření řetězce. Tím dojde k nepředvídatelným účelům. Například pokud někdo interně interně předává řetězec, který má stejný obsah jako váš, bude mít kopii a neočekává se, že upravujete svůj řetězec vůbec.

Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také:

- [.NET Framework regulární výrazy](../../standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)
