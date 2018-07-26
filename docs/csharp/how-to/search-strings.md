---
title: 'Postupy: vyhledávání řetězců (Průvodce v C#)'
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: d1e132093cc59c7b41a3f7d5b522fca2e224f779
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961216"
---
# <a name="how-to-search-strings"></a>Postupy: vyhledávání řetězců

Dva hlavní strategie můžete použít k vyhledání textu v řetězci. Metody <xref:System.String> tříd – hledání pro určitý text. Regulárních výrazů vyhledávat vzory v textu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

[Řetězec](../language-reference/keywords/string.md) typu, což je alias pro <xref:System.String?displayProperty=nameWithType> třídy, nabízí celou řadu užitečných metod pro vyhledání obsah řetězce. Mezi nimi jsou <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Třída poskytuje bohaté slovník pro vyhledávání vzorů v textu. V tomto článku se dozvíte těchto technik a jak zvolit nejlepší metody pro vaše potřeby.

## <a name="does-a-string-contain-text"></a>Obsahuje řetězec textu?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> a <xref:System.String.EndsWith%2A?displayProperty=nameWithType> metody hledaný řetězec pro určitý text. Následující příklad ukazuje, každý z těchto metod a variantu, která používá malá a velká písmena hledání:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Předchozí příklad ukazuje důležitý bod pro použití těchto metod. Hledání jsou **malá a velká písmena** ve výchozím nastavení. Můžete použít <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> hodnotu výčtu k určení vyhledávání malá a velká písmena.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Pokud nastane hledané kombinaci textu v řetězci?

<xref:System.String.IndexOf%2A> a <xref:System.String.LastIndexOf%2A> metody také hledání textu v řetězci. Tyto metody vrací umístění textu je žádána. Pokud se text nenajde, vrátí `-1`. Následující příklad ukazuje vyhledejte první a poslední výskyty slova "metody" a zobrazí text mezi.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Vyhledání konkrétní text pomocí regulárních výrazů

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Třídy lze použít k vyhledání řetězce. Tato hledání můžou být složitosti od jednoduché složité textových vzorů.

Následující příklad kódu vyhledá pro slovo "the" nebo "jejich" ve větě, ignorování případu. Statická metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provede vyhledávání. Je jí řetězec hledání a vzor hledání. V takovém případě třetí argument určuje hledat bez tohoto rozlišování. Další informace naleznete v tématu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Vzor hledání popisuje text, který hledáte. Následující tabulka popisuje každý prvek vzor hledání. (Následující tabulka používá jedné `\` musí být uvozena jako `\\` v řetězci jazyka C#).

| vzor  | Význam     |
| -------- |-------------|
| the      | shodovat s textem "the" |
| (eir)?   | porovnání 0 a 1 výskyt "eir" |
| \s       | Porovná prázdný znak    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string` Metody jsou obvykle lepší možnosti, pokud chcete vyhledat přesný řetězec. Regulární výrazy jsou lépe při vyhledávání pro některé vzor je zdrojový řetězec.

## <a name="does-a-string-follow-a-pattern"></a>Řetězec se řídí vzorem?

Následující kód používá regulárních výrazů pro ověření formátu každý řetězec v poli. Vyžaduje ověření, že každý řetězec mít formát _služba ._protokol telefonní čísla, ve kterém jsou tří skupin číslic oddělených spojovníky, první dvě skupiny obsahují tři číslice a třetí skupina obsahuje čtyři číslice. Vzor hledání použit regulární výraz `^\\d{3}-\\d{3}-\\d{4}$`. Další informace najdete v tématu [jazyk regulárních výrazů – Stručná referenční příručka](../../standard/base-types/regular-expression-language-quick-reference.md).

| vzor  | Význam                             |
| -------- |-------------------------------------|
| ^        | odpovídá začátku řetězce |
| \d{3}    | odpovídá přesně 3 znaky číslice  |
| -        | odpovídá "-" znaků           |
| \d{3}    | odpovídá přesně 3 znaky číslice  |
| -        | odpovídá "-" znaků           |
| \d{4}    | odpovídá přesně 4 znaky číslice  |
| $        | odpovídá konci řetězce       |


[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Tento vzor hledání jednoduchého odpovídá mnoho platné řetězce. Regulární výrazy jsou lepší chcete vyhledat nebo ověřit proti vzor, spíše než jeden řetězec textu.

Tyto ukázky můžete zkusit pohledem na kód v našich [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také  

 [Průvodce programováním v jazyce C#](../programming-guide/index.md)  
 [Řetězce](../programming-guide/strings/index.md)  
 [LINQ a řetězce](../programming-guide/concepts/linq/linq-and-strings.md)   
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>     
 [Regulárních výrazech .NET Frameworku](../../standard/base-types/regular-expressions.md)   
 [Jazyk regulárních výrazů – Stručná referenční příručka](../../standard/base-types/regular-expression-language-quick-reference.md)   
 [Osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md)  
