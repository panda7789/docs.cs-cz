---
title: 'Postupy: vyhledávání řetězců (Průvodce C#)'
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: d1e132093cc59c7b41a3f7d5b522fca2e224f779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-search-strings"></a>Postupy: vyhledávání řetězců

Dva hlavní strategie můžete použít k vyhledání textu v řetězcích. Metody <xref:System.String> hledání třídy pro zadaný text. Regulární výrazy k vyhledávání vzorků v textu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

[Řetězec](../language-reference/keywords/string.md) typu, který je alias pro <xref:System.String?displayProperty=nameWithType> třídy, poskytuje řadu užitečných metod pro vyhledávání obsahu řetězce. Mezi nimi jsou <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Třída poskytuje bohaté slovník pro vyhledávání vzorů v textu. V tomto článku se dozvíte tyto postupy a jak zvolit nejlepší metody pro vaše potřeby.

## <a name="does-a-string-contain-text"></a>Obsahuje řetězec textu?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> a <xref:System.String.EndsWith%2A?displayProperty=nameWithType> metody hledat řetězec pro zadaný text. Následující příklad ukazuje, každý z těchto metod a variace, používá malá a velká písmena vyhledávání:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

V předchozím příkladu představuje bod důležité pro použití těchto metod. Hledání jsou **malá a velká písmena** ve výchozím nastavení. Můžete použít <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> hodnota výčtu k určení vyhledávání malá a velká písmena.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Kde dochází hledané kombinaci text v řetězci?

<xref:System.String.IndexOf%2A> a <xref:System.String.LastIndexOf%2A> metody také hledat text ve řetězce. Tyto metody vrací text předložena žádost o umístění. Pokud není nalezen text, že budou vracet `-1`. Následující příklad ukazuje, vyhledejte první a poslední výskyt slova "metody" a zobrazí text v rozmezí.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Vyhledávání konkrétní textu pomocí regulárních výrazů

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Třídu lze použít k vyhledání řetězců. Tato hledání mohou být v rozsahu v složitost z jednoduchého tak, aby složitá textové vzory.

Následující příklad kódu hledá slovo "na" nebo "jejich" ve větě, ignoruje případu. Statickou metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provede vyhledávání. Je mu řetězec pro hledání a vzor hledání. V takovém případě třetí argument určuje hledat bez tohoto rozlišování. Další informace naleznete v tématu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Vzor hledání popisuje text, který hledáte. Následující tabulka popisuje každý prvek vzor hledání. (Následující tabulce používá jedné `\` který, je nutné uvést jako `\\` v řetězci C#).

| vzor  | Význam     |
| -------- |-------------|
| the      | shodují s textem "na" |
| (eir)?   | Porovná 0 nebo 1 výskyt "eir" |
| \s       | odpovídat prázdný znak    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string` Metody jsou obvykle lepší možnosti, pokud chcete vyhledat řetězec přesný. Regulární výrazy jsou lépe, když hledáte pro některé vzor je zdrojový řetězec.

## <a name="does-a-string-follow-a-pattern"></a>Řetězec musí dodržovat vzor?

Následující kód používá regulární výrazy k ověření formát každý řetězce v matici. Ověření vyžaduje, aby měl každý řetězec formu telefonní číslo, ve kterém jsou tří skupin číslic oddělených pomlčkami, první dvě skupiny obsahují tři znaky a třetí skupina obsahuje čtyři číslice. Vzor hledání použit regulární výraz `^\\d{3}-\\d{3}-\\d{4}$`. Další informace najdete v tématu [jazyk regulárních výrazů – Stručná referenční příručka](../../standard/base-types/regular-expression-language-quick-reference.md).

| vzor  | Význam                             |
| -------- |-------------------------------------|
| ^        | odpovídá začátku řetězce |
| \d{3}    | odpovídá přesně 3 znaky číslice  |
| -        | odpovídá '-' znak           |
| \d{3}    | odpovídá přesně 3 znaky číslice  |
| -        | odpovídá '-' znak           |
| \d{4}    | odpovídá přesně 4 číslice znaky  |
| $        | odpovídá konci řetězce       |


[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Tento vzor hledání jednoduchého odpovídá mnoho platné řetězce. Regulární výrazy jsou lepší chcete vyhledat nebo vyhodnotit proti vzor, nikoli jednoho textového řetězce.

Tyto ukázky můžete zkusit prohlížením kódu v našem [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také  

 [Průvodce programováním v jazyce C#](../programming-guide/index.md)  
 [Řetězce](../programming-guide/strings/index.md)  
 [LINQ a řetězce](../programming-guide/concepts/linq/linq-and-strings.md)   
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>     
 [Regulární výrazy rozhraní .NET framework](../../standard/base-types/regular-expressions.md)   
 [Jazyk regulárních výrazů – Stručná referenční příručka](../../standard/base-types/regular-expression-language-quick-reference.md)   
 [Osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md)  
