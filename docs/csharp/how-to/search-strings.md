---
title: Jak vyhledávat řetězce (Průvodce C# )
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: 15ea77d13a93d88bd996a22b6fe1aaad81df572d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74959699"
---
# <a name="how-to-search-strings"></a>Jak hledat řetězce

K hledání textu v řetězcích můžete použít dvě hlavní strategie. Metody třídy <xref:System.String> vyhledávají konkrétní text. Regulární výrazy vyhledávají vzorky v textu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Typ [řetězce,](../language-reference/builtin-types/reference-types.md#the-string-type) který je alias <xref:System.String?displayProperty=nameWithType> pro třídu, poskytuje řadu užitečných metod pro vyhledávání obsahu řetězce. Mezi nimi <xref:System.String.Contains%2A> <xref:System.String.StartsWith%2A>jsou <xref:System.String.EndsWith%2A> <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>, , , . Třída <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> poskytuje bohatou slovní zásobu pro hledání vzorů v textu. V tomto článku se naučíte tyto techniky a jak zvolit nejlepší metodu pro vaše potřeby.

## <a name="does-a-string-contain-text"></a>Obsahuje řetězec text?

V <xref:System.String.Contains%2A?displayProperty=nameWithType> <xref:System.String.StartsWith%2A?displayProperty=nameWithType> a <xref:System.String.EndsWith%2A?displayProperty=nameWithType> metody hledat řetězec pro konkrétní text. Následující příklad ukazuje každou z těchto metod a variantu, která používá hledání bez rozlišování velkých a malých písmen:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Předchozí příklad ukazuje důležitý bod pro použití těchto metod. Hledání ve výchozím nastavení **rozlišují malá a velká písmena.** Hodnotu <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> výčtu slouží k určení hledání bez rozlišování velkých a malých písmen.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Kde se vyhledávaný text vyskytuje v řetězci?

Metody <xref:System.String.IndexOf%2A> <xref:System.String.LastIndexOf%2A> a také vyhledávají text v řetězcích. Tyto metody vrátí umístění hledaného textu. Pokud text není nalezen, vrátí `-1`se . Následující příklad ukazuje hledání prvního a posledního výskytu slova "metody" a zobrazuje text mezi nimi.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Hledání konkrétního textu pomocí regulárních výrazů

Třídu <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> lze použít k vyhledávání řetězců. Tato hledání mohou být složitější od jednoduchých až po složité textové vzory.

Následující příklad kódu hledá slovo "" nebo "jejich" ve větě, ignoruje případ. Statická <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metoda provádí hledání. Dáte mu řetězec k vyhledávání a vyhledávací vzor. V tomto případě třetí argument určuje hledání bez rozlišování velkých a malých písmen. Další informace naleznete v tématu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Vyhledávací vzor popisuje hledaný text. Následující tabulka popisuje každý prvek vyhledávacího vzoru. (Níže uvedená tabulka `\` používá singl, `\\` který musí být uvozeny jako v řetězci C#).

| Vzor  | Význam     |
| -------- |-------------|
| prostředek      | odpovídají textu "the" |
| (eir)?   | shoda 0 nebo 1 výskyt "eir" |
| \s       | porovná se s nebílým znakem    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> Metody `string` jsou obvykle lepší volby při hledání přesného řetězce. Regulární výrazy jsou lepší při hledání nějakého vzoru ve zdrojovém řetězci.

## <a name="does-a-string-follow-a-pattern"></a>Sleduje řetězec vzorek?

Následující kód používá regulární výrazy k ověření formátu každého řetězce v poli. Ověření vyžaduje, aby každý řetězec měl tvar telefonního čísla, ve kterém jsou tři skupiny číslic odděleny pomlčkami, první dvě skupiny obsahují tři číslice a třetí skupina obsahuje čtyři číslice. Vyhledávací vzor používá regulární výraz `^\\d{3}-\\d{3}-\\d{4}$`. Další informace naleznete v [tématu Jazyk regulárních výrazů – stručný přehled](../../standard/base-types/regular-expression-language-quick-reference.md).

| Vzor  | Význam                             |
| -------- |-------------------------------------|
| ^        | odpovídá začátku řetězce |
| \d{3}    | přesně 3 číslice znaků  |
| -        | odpovídá znaku '-'           |
| \d{3}    | přesně 3 číslice znaků  |
| -        | odpovídá znaku '-'           |
| \d{4}    | přesně 4 číslice znaků  |
| $        | odpovídá konci řetězce       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Tento jediný vyhledávací vzor odpovídá mnoha platným řetězcům. Regulární výrazy je lepší vyhledat nebo ověřit proti vzorek, spíše než jeden textový řetězec.

Tyto ukázky můžete vyzkoušet tak, že se podíváte na kód v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako zip soubor](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
- [LINQ a řetězce](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework – regulární výrazy](../../standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Doporučené postupy pro použití řetězců v rozhraní .NET](../../standard/base-types/best-practices-strings.md)
