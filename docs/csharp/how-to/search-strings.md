---
title: Hledání řetězců (C# průvodce)
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: 15ea77d13a93d88bd996a22b6fe1aaad81df572d
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959699"
---
# <a name="how-to-search-strings"></a>Jak hledat řetězce

Můžete použít dvě hlavní strategie pro hledání textu v řetězcích. Metody <xref:System.String> třídy hledají konkrétní text. Regulární výrazy hledají vzory v textu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Typ [řetězce](../language-reference/builtin-types/reference-types.md#the-string-type) , který je aliasem pro třídu <xref:System.String?displayProperty=nameWithType>, poskytuje řadu užitečných metod pro hledání obsahu řetězce. Mezi nimi se <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A><xref:System.String.IndexOf%2A><xref:System.String.LastIndexOf%2A>. Třída <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> poskytuje bohatou slovník pro hledání vzorů v textu. V tomto článku se seznámíte s těmito technikami a zvolíte nejlepší způsob pro vaše potřeby.

## <a name="does-a-string-contain-text"></a>Obsahuje řetězec text?

Metody <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> a <xref:System.String.EndsWith%2A?displayProperty=nameWithType> prohledají řetězec pro konkrétní text. Následující příklad ukazuje každou z těchto metod a variaci, která používá hledání bez rozlišení velkých a malých písmen:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Předchozí příklad ukazuje důležitý bod pro použití těchto metod. U hledání se ve výchozím nastavení **rozlišují malá a velká písmena** . Pomocí hodnoty výčtu <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> zadáte hledání bez rozlišení velkých a malých písmen.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Kde v řetězci dojde k hledanému textu?

Metody <xref:System.String.IndexOf%2A> a <xref:System.String.LastIndexOf%2A> také vyhledávají text v řetězcích. Tyto metody vracejí umístění hledaného textu. Pokud se text nenajde, vrátí `-1`. Následující příklad ukazuje hledání prvního a posledního výskytu slova "metody" a zobrazuje text mezi.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Hledání konkrétního textu pomocí regulárních výrazů

Třídu <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> lze použít pro hledání řetězců. Tato hledání mohou být v rozsahu od jednoduchých až po složité textové vzory.

Následující příklad kódu vyhledá ve větě slovo "" nebo "jejich", ignoruje případ. Statická metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provede hledání. Dáte mu řetězec pro hledání a vzor hledání. V tomto případě třetí argument určuje hledání bez rozlišování velkých a malých písmen. Další informace najdete v tématu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Vzor hledání popisuje hledaný text. Následující tabulka popisuje jednotlivé prvky vzoru vyhledávání. (Následující tabulka používá jednu `\`, která musí být uvozená jako `\\` v C# řetězci).

| vzorku  | Význam     |
| -------- |-------------|
| the      | odpovídá textu "The" |
| (eir)?   | porovnává 0 nebo 1 výskyt "EIR" |
| \s       | odpovídá prázdnému znaku    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> Metody `string` jsou obvykle lepší volby při hledání přesný řetězec. Regulární výrazy jsou lepší při hledání určitého vzoru ve zdrojovém řetězci.

## <a name="does-a-string-follow-a-pattern"></a>Sleduje řetězec vzor?

Následující kód používá regulární výrazy k ověření formátu každého řetězce v poli. Ověřování vyžaduje, aby měl každý řetězec formu telefonního čísla, ve kterém jsou tři skupiny číslic oddělené pomlčkami, první dvě skupiny obsahují tři číslice a třetí skupina obsahuje čtyři číslice. Vzor hledání používá `^\\d{3}-\\d{3}-\\d{4}$`regulárních výrazů. Další informace najdete v tématu [Jazyk regulárních výrazů – rychlé reference](../../standard/base-types/regular-expression-language-quick-reference.md).

| vzorku  | Význam                             |
| -------- |-------------------------------------|
| ^        | odpovídá začátku řetězce |
| \d{3}    | odpovídá přesně 3 číslicovým znakům  |
| -        | odpovídá znaku '-'           |
| \d{3}    | odpovídá přesně 3 číslicovým znakům  |
| -        | odpovídá znaku '-'           |
| \d{4}    | odpovídá přesně 4 znakům číslice  |
| $        | odpovídá konci řetězce       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Tento jednoduchý vzor hledání odpovídá mnoha platným řetězcům. Regulární výrazy jsou lepší vyhledat nebo ověřit proti vzorci místo jediného textového řetězce.

Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
- [LINQ a řetězce](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework regulární výrazy](../../standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md)
