---
title: 'Postupy: Změna obsahu řetězce – průvodce v C#'
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 99102fe90f5f675235e2993b7dd99f59214862d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-string-contents-in-c"></a>Postupy: Změna obsahu řetězce v jazyce C# #

Tento článek ukazuje několik postupů k vytvoření `string` úpravou existující `string`. Všechny techniky ukázán vrátit výsledek změny jako novou `string` objektu. Všechny příklady jasně ukazuje to uložit výsledek nové proměnné. Poté můžete prozkoumat oba původní `string` a `string` vyplývající z úpravy při spuštění každého příkladu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Existuje několik postupů popsaných v tomto článku. Můžete nahradit existující text. Můžete vyhledat a nahradí odpovídající text jiným textem. Řetězec lze považovat posloupnost znaků. Můžete také použít usnadňující metody, které odebrání mezer. Měli byste vybrat techniky, které nejvíce odpovídají váš scénář.

## <a name="replace-text"></a>Nahraďte text

Následující kód vytvoří nový řetězec tak, že nahradíte existující text se nenahrazuje.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Předchozí kód ukazuje to *neměnné* vlastnost řetězců. Zobrazí se v předchozím příkladu, původní řetězec `source`, se nemění. <xref:System.String.Replace%2A?displayProperty=nameWithType> Metoda vytvoří novou `string` obsahující změny.

<xref:System.String.Replace%2A> Metoda můžete nahradit, řetězce nebo jednotlivé znaky. V obou případech se nahradí všechny výskyty hledané kombinaci textu.  Následující příklad nahradí všechny ' 'znaků a obsahující'\_':

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Zdrojový řetězec je beze změny a vrátí se nový řetězec nahrazení.

## <a name="trim-white-space"></a>Trim mezer

Můžete použít <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>, a <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> metody k odebrání všech začínat ani končit mezerou prázdné.  Následující kód ukazuje příklad jednotlivých. Zdrojový řetězec nezmění; Tyto metody vrací nový řetězec s změněný obsah.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Odeberte text

Text můžete odebrat z řetězce pomocí <xref:System.String.Remove%2A?displayProperty=nameWithType> metoda. Tato metoda odebere počet znaků počínaje konkrétním indexem. Následující příklad ukazuje, jak používat <xref:System.String.IndexOf%2A?displayProperty=nameWithType> následuje <xref:System.String.Remove%2A> text odebrat z řetězce:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Nahraďte vzory pro porovnávání

Můžete použít [regulární výrazy](../../standard/base-types/regular-expressions.md) nahradit text porovnávání vzorů pomocí nového textu, které by mohly mít definované vzor. Následující příklad používá <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třída nalézt vzor v zdrojový řetězec a nahraďte ji metodou správné použití velkých písmen. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> Metoda přebírá funkce, která poskytuje logiku nahrazení jako jeden z jeho argumenty. V tomto příkladu, že funkce `LocalReplaceMatchCase` je **místní funkce** deklarované uvnitř metody ukázky. `LocalReplaceMatchCase` používá <xref:System.Text.StringBuilder?displayProperty=nameWithType> třída k sestavení náhradní řetězec s správné použití velkých písmen.

Regulární výrazy jsou zvláště užitečné pro vyhledávání a nahrazování textu, který pracuje podle vzoru, nikoli Well-Known text. V tématu [postupy: vyhledávání řetězců](search-strings.md) další podrobnosti. Vzor hledání "the\s" vyhledá slovo "na" následované prázdným znakem. Tuto část vzorce zajistí, že se neshoduje "existuje" v řetězci zdroje. Další informace o prvků jazyka regulárních výrazů v tématu [jazyk regulárních výrazů – Stručná referenční příručka](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> Vrátí metoda neměnné řetězec s obsah <xref:System.Text.StringBuilder> objektu.

## <a name="modifying-individual-characters"></a>Úprava jednotlivých znaků

Můžete vytvořit pole znaků z řetězce, změnit obsah pole a pak vytvořte nový řetězec z změněný obsah pole.

Následující příklad ukazuje, jak nahradit sadu znaků v řetězci. První, použije <xref:System.String.ToCharArray?displayProperty=nameWithName> metodu pro vytvoření pole znaků. Použije <xref:System.String.IndexOf%2A> metody k vyhledání počáteční index je slovo "už." Následující tři znaky jsou nahrazena různá slova. Nakonec nový řetězec sestavený z pole aktualizované znak.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>Nezabezpečený změny na řetězec

Pomocí **unsafe** kódu, můžete upravit řetězec "místo" po jeho vytvoření. Nezabezpečený kód obchází mnoho funkcí rozhraní .NET navržená k minimalizaci určitých typů chyb v kódu. Budete muset použít nezabezpečený kód upravit řetězec na místě, protože třída řetězec je navržena jako **neměnné** typu. Po vytvoření, jeho hodnota se nezmění. Nezabezpečený kód by se obešla tuto vlastnost tak, že přístup k a úprava množství paměti používané `string` bez použití normální `string` metody.
V následujícím příkladu se poskytuje pro tyto výjimečných případech, ve které chcete upravit řetězec na místě pomocí nezabezpečený kód. Tento příklad ukazuje způsob použití `fixed` – klíčové slovo. `fixed` – Klíčové slovo zabraňuje přesunutí objekt řetězce v paměti, zatímco kód přistupuje k paměti pomocí unsafe ukazatele uvolňování paměti (GC). Také ukazuje jeden možný vedlejším účinkem nebezpečné operace s řetězci která je výsledkem způsob kompilátor jazyka C# interně ukládá řetězce (učně). Obecně byste neměli používat tato technika, pokud to není nezbytně nutné. Další informace najdete v článcích na [unsafe](../language-reference/keywords/unsafe.md) a [pevné](../language-reference/keywords/fixed-statement.md). Referenční dokumentace rozhraní API pro <xref:System.String.Intern%2A> zahrnuje informace na interning řetězec.

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Tyto ukázky můžete zkusit prohlížením kódu v našem [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

[Regulární výrazy rozhraní .NET framework](../../standard/base-types/regular-expressions.md)  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)  
