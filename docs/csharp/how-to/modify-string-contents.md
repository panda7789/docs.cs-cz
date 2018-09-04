---
title: 'Postupy: Změna obsahu řetězce – průvodce v C#'
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 23d52a52291b3d5c36fc2ed0f299ab82aa5ffabd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558837"
---
# <a name="how-to-modify-string-contents-in-c"></a>Postupy: Změna obsahu řetězce v jazyce C\#

Tento článek ukazuje řadu technik k vytvoření `string` změnou existující `string`. Všechny metody vrátí výsledek změny jako nový jsme vám ukázali `string` objektu. Všechny příklady jasně ukazuje to, uloží výsledek v nové proměnné. Poté můžete prozkoumat původní `string` a `string` vyplývající z změny, když spustíte každý příklad.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Existuje několik technik naznačených v tomto článku. Můžete nahradit existující text. Můžete vyhledat a nahradit odpovídající text jiným textem. Řetězec lze považovat jako posloupnost znaků. Můžete také použít vhodné metody, které odebrat prázdné znaky. Měli byste zvolit techniky, které nejvíce odpovídají vašemu scénáři.

## <a name="replace-text"></a>Nahradit text

Následující kód vytvoří nový řetězec tak, že nahradíte existující text s náhradou.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Předchozí kód ukazuje to *neměnné* vlastnosti řetězců. Zobrazí se v předchozím příkladu, který původní řetězec `source`, se nezmění. <xref:System.String.Replace%2A?displayProperty=nameWithType> Metoda vytvoří nový `string` obsahující změny.

<xref:System.String.Replace%2A> Metody lze nahradit řetězce nebo jednotlivé znaky. V obou případech se nahradí všechny výskyty hledané kombinaci textu.  Následující příklad nahradí všechny ' "znaků a obsahující"\_":

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Zdrojový řetězec se nezmění a vrátí nový řetězec se nahrazení.

## <a name="trim-white-space"></a>Trim prázdný znak

Můžete použít <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>, a <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> metody odebere všechny úvodní a koncové prázdné znaky.  Následující kód ukazuje příklad každého. Zdrojový řetězec nemění; Tyto metody vrátí nový řetězec s upravený obsah.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Odeberte text

Text lze odebrat z řetězce pomocí <xref:System.String.Remove%2A?displayProperty=nameWithType> metody. Tato metoda odebere počet znaků počínaje konkrétním indexem. Následující příklad ukazuje, jak používat <xref:System.String.IndexOf%2A?displayProperty=nameWithType> následovaný <xref:System.String.Remove%2A> text odebrat z řetězce:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Nahraďte vzory pro porovnávání

Můžete použít [regulární výrazy](../../standard/base-types/regular-expressions.md) nahradit text porovnávání vzorů novým textem, může být definované vzorem. V následujícím příkladu <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídy pro vzor hledání zdrojový řetězec a nahraďte ji metodou správné malá a velká písmena. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> Metoda má funkci, která poskytuje logiku nahrazení jako jeden z jejích argumentů. V tomto příkladu, tuto funkci `LocalReplaceMatchCase` je **lokální funkce** deklarované uvnitř ukázka metody. `LocalReplaceMatchCase` používá <xref:System.Text.StringBuilder?displayProperty=nameWithType> třída pro sestavení řetězci pro nahrazení se správné malá a velká písmena.

Regulární výrazy jsou nejužitečnější při hledání a nahrazování textu, který následuje vzor, nikoli textové. Zobrazit [postupy: vyhledávání řetězců](search-strings.md) další podrobnosti. Vzor hledání "the\s" hledá slovo "the" následované prázdným znakem. Tuto část vzorce zajistíte, že se pravděpodobně neshoduje s "není" ve zdrojovém řetězci. Další informace o prvky jazyka regulárních výrazů, naleznete v tématu [jazyk regulárních výrazů – Stručná referenční příručka](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> Vrátí metoda neměnné řetězec s obsahem v <xref:System.Text.StringBuilder> objektu.

## <a name="modifying-individual-characters"></a>Úprava jednotlivých znaků

Můžete vytvořit pole znaků z řetězce, upravovat obsah pole a poté vytvořit nový řetězec z změněný obsah pole.

Následující příklad ukazuje, jak nahradit sady znaků v řetězci. Nejprve, použije <xref:System.String.ToCharArray?displayProperty=nameWithName> metodu pro vytvoření pole znaků. Používá <xref:System.String.IndexOf%2A> metody k vyhledání počáteční index slovo "fox." Následující tři znaky jsou nahrazena různá slova. Nakonec je vytvořen nový řetězec z pole aktualizované znaků.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>Nezabezpečený změny na řetězec

Pomocí **nebezpečné** kódu, můžete upravit řetězec "místo" po jejím vytvoření. Nezabezpečený kód vynechá řadu funkcí .NET určená k minimalizaci určité typy chyb v kódu. Je třeba použít nezabezpečený kód upravit řetězec na místě, protože třída string je navržena jako **neměnné** typu. Po jeho vytvoření, jeho hodnota se nezmění. Nezabezpečený kód neodpovídá této vlastnosti přístupu a úpravou paměť používanou `string` bez použití normální `string` metody.
Následující příklad je k dispozici pro těchto výjimečných případech, ve které chcete upravit řetězce v místě použití nezabezpečeného kódu. Tento příklad ukazuje způsob použití `fixed` – klíčové slovo. `fixed` – Klíčové slovo zabraňuje systému uvolňování paměti (GC) získat přechodem na objekt řetězce v paměti, zatímco kód přistupuje k paměťově pomocí nebezpečné ukazatele. Ukazuje také jeden možný vedlejším účinkem nebezpečné operace s řetězci, který je výsledkem způsobu, jakým kompilátor jazyka C# interně uchovává řetězce (učně). Obecně byste neměli používat tuto techniku, pokud to není nezbytně nutné. Další informace najdete v článcích na [nebezpečné](../language-reference/keywords/unsafe.md) a [oprava](../language-reference/keywords/fixed-statement.md). Referenční dokumentace rozhraní API pro <xref:System.String.Intern%2A> obsahuje informace o interning řetězce.

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Tyto ukázky můžete zkusit pohledem na kód v našich [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také:

- [Regulárních výrazech .NET Frameworku](../../standard/base-types/regular-expressions.md)  
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)  
