---
title: Jak upravit obsah řetězce - Průvodce C#
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: f31fa94501ac2120e22e229dfc11babb8b8cc0f3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242852"
---
# <a name="how-to-modify-string-contents-in-c"></a>Jak upravit obsah řetězce v C\#

Tento článek ukazuje několik technik `string` k výrobě `string`úpravou existující . Všechny techniky demonstroval vrátit výsledek změny jako `string` nový objekt. Chcete-li jasně demonstrovat to, všechny příklady uložit výsledek v nové proměnné. Potom můžete prozkoumat `string` původní `string` a vyplývající z změny při spuštění každého příkladu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

V tomto článku je demonstrováno několik technik. Můžete nahradit existující text. Můžete hledat vzorky a nahradit odpovídající text jiným textem. Řetězec můžete považovat za posloupnost znaků. Můžete také použít metody pohodlí, které odstraňují prázdné znaky. Měli byste zvolit techniky, které nejvíce odpovídají vašemu scénáři.

## <a name="replace-text"></a>Nahrazení textu

Následující kód vytvoří nový řetězec nahrazením existujícího textu náhradou.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Předchozí kód demonstruje tuto *neměnnou* vlastnost řetězců. V předchozím příkladu se zobrazí, že `source`původní řetězec , , není změněn. Metoda <xref:System.String.Replace%2A?displayProperty=nameWithType> vytvoří nový `string` obsahující změny.

Metoda <xref:System.String.Replace%2A> může nahradit řetězce nebo jednotlivé znaky. V obou případech se nahradí každý výskyt hletého textu.  Následující příklad nahradí všechny znaky '\_' znakem ' ::

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Zdrojový řetězec je beze změny a nový řetězec je vrácena s nahrazení.

## <a name="trim-white-space"></a>Oříznutí prázdného místa

Můžete použít <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>a <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> metody k odebrání všech úvodních nebo koncových mezer.  Následující kód ukazuje příklad každého z nich. Zdrojový řetězec se nezmění; Tyto metody vrátí nový řetězec s upraveným obsahem.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Odebrání textu

Pomocí metody můžete z řetězce <xref:System.String.Remove%2A?displayProperty=nameWithType> odebrat text. Tato metoda odebere počet znaků začínajících na určitý index. Následující příklad ukazuje, <xref:System.String.IndexOf%2A?displayProperty=nameWithType> jak <xref:System.String.Remove%2A> používat následovaný k odebrání textu z řetězce:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Nahradit odpovídající vzorky

[Regulární výrazy](../../standard/base-types/regular-expressions.md) můžete použít k nahrazení vzorů shody textu novým textem, případně definovaným vzorkem. Následující příklad používá <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídu k nalezení vzoru ve zdrojovém řetězci a jeho nahrazení správnými velkými písmeny. Metoda <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> přebírá funkci, která poskytuje logiku nahrazení jako jeden z jeho argumentů. V tomto příkladu `LocalReplaceMatchCase` je tato funkce **místní funkcí** deklarovanou uvnitř ukázkové metody. `LocalReplaceMatchCase`používá <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídu k sestavení náhradního řetězce s vlastními velkými písmeny.

Regulární výrazy jsou nejužitečnější pro vyhledávání a nahrazování textu, který následuje za vzorkem, spíše než známý text. Další podrobnosti naleznete v tématu [Jak hledat řetězce.](search-strings.md) Vyhledávací vzor, "\s" hledá slovo "the" následovaný znakem prázdnémezery. Tato část vzoru zajišťuje, že neodpovídá "tam" ve zdrojovém řetězci. Další informace o prvcích jazyka regulárních výrazů naleznete v [tématu Jazyk regulárních výrazů – stručný přehled](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

Metoda <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> vrátí neměnný řetězec s obsahem v objektu. <xref:System.Text.StringBuilder>

## <a name="modifying-individual-characters"></a>Úprava jednotlivých znaků

Můžete vytvořit pole znaků z řetězce, upravit obsah pole a pak vytvořit nový řetězec z upraveného obsahu pole.

Následující příklad ukazuje, jak nahradit sadu znaků v řetězci. Nejprve používá <xref:System.String.ToCharArray?displayProperty=nameWithType> metodu k vytvoření pole znaků. Používá metodu <xref:System.String.IndexOf%2A> k nalezení počátečního indexu slova "liška". Další tři znaky jsou nahrazeny jiným slovem. Nakonec je z aktualizovaného pole znaků vytvořen nový řetězec.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Programově vytvářet obsah řetězce

Vzhledem k tomu, že řetězce jsou neměnné, všechny předchozí příklady vytvářejí dočasné řetězce nebo pole znaků. Ve scénářích s vysokým výkonem může být žádoucí vyhnout se těmto přidělení haldy. .NET Core <xref:System.String.Create%2A?displayProperty=nameWithType> poskytuje metodu, která umožňuje programově vyplnit obsah znaku řetězce prostřednictvím zpětného volání a zároveň se vyhnout zprostředkující mašle dočasné řetězce.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Řetězec v pevném bloku s nebezpečným kódem můžete upravit, ale **důrazně** se nedoporučuje upravovat obsah řetězce po vytvoření řetězce. Tím se věci rozbijí nepředvídatelným způsobem. Například pokud někdo internuje řetězec, který má stejný obsah jako vy, dostanou vaši kopii a nebude očekávat, že jste upravovali jeho řetězec vůbec.

Tyto ukázky můžete vyzkoušet tak, že se podíváte na kód v našem [úložišti GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako zip soubor](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

- [.NET Framework – regulární výrazy](../../standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)
