---
title: Hledání řetězců (Průvodce C#)
description: Přečtěte si o dvou strategiích pro hledání textu v řetězcích v jazyce C#. Metody třídy String hledají konkrétní text. Regulární výrazy hledají vzory v textu.
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: 17bf6e080542242d30791b70ffbf00b05f03a7b0
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86473991"
---
# <a name="how-to-search-strings"></a>Jak hledat řetězce

Můžete použít dvě hlavní strategie pro hledání textu v řetězcích. Metody <xref:System.String> hledání konkrétního textu ve třídě Regulární výrazy hledají vzory v textu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Typ [řetězce](../language-reference/builtin-types/reference-types.md#the-string-type) , který je aliasem pro <xref:System.String?displayProperty=nameWithType> třídu, poskytuje řadu užitečných metod pro hledání obsahu řetězce. Mezi nimi patří <xref:System.String.Contains%2A> , <xref:System.String.StartsWith%2A> , <xref:System.String.EndsWith%2A> , <xref:System.String.IndexOf%2A> , <xref:System.String.LastIndexOf%2A> . <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>Třída poskytuje bohatou slovník pro hledání vzorů v textu. V tomto článku se seznámíte s těmito technikami a zvolíte nejlepší způsob pro vaše potřeby.

## <a name="does-a-string-contain-text"></a>Obsahuje řetězec text?

<xref:System.String.Contains%2A?displayProperty=nameWithType>Metody, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> a <xref:System.String.EndsWith%2A?displayProperty=nameWithType> vyhledávají konkrétní text v řetězci. Následující příklad ukazuje každou z těchto metod a variaci, která používá vyhledávání bez rozlišování velkých a malých písmen:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet1":::

Předchozí příklad ukazuje důležitý bod pro použití těchto metod. U hledání se ve výchozím nastavení **rozlišují malá a velká písmena** . Použijte <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> hodnotu výčtu k určení hledání bez rozlišování velkých a malých písmen.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Kde v řetězci dojde k hledanému textu?

<xref:System.String.IndexOf%2A>Metody a <xref:System.String.LastIndexOf%2A> také vyhledávají text v řetězcích. Tyto metody vracejí umístění hledaného textu. Pokud se text nenajde, vrátí se `-1` . Následující příklad ukazuje hledání prvního a posledního výskytu slova "metody" a zobrazuje text mezi.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet2":::

## <a name="finding-specific-text-using-regular-expressions"></a>Hledání konkrétního textu pomocí regulárních výrazů

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>Třídu lze použít pro hledání řetězců. Tato hledání mohou být v rozsahu od jednoduchých až po složité textové vzory.

Následující příklad kódu vyhledá ve větě slovo "" nebo "jejich", ignoruje případ. Statická metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provede hledání. Dáte mu řetězec pro hledání a vzor hledání. V tomto případě třetí argument určuje hledání bez rozlišování velkých a malých písmen. Další informace naleznete v tématu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.

Vzor hledání popisuje hledaný text. Následující tabulka popisuje jednotlivé prvky vzoru vyhledávání. (Níže uvedená tabulka používá jeden `\` , který musí být uvozen jako `\\` v řetězci jazyka C#).

| Vzor  | Význam                          |
|----------|----------------------------------|
| `the`    | odpovídá textu "The"             |
| `(eir)?` | porovnává 0 nebo 1 výskyt "EIR" |
| `\s`     | odpovídá prázdnému znaku    |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet3":::

> [!TIP]
> `string`Metody jsou obvykle lepší volby při hledání přesný řetězec. Regulární výrazy jsou lepší při hledání určitého vzoru ve zdrojovém řetězci.

## <a name="does-a-string-follow-a-pattern"></a>Sleduje řetězec vzor?

Následující kód používá regulární výrazy k ověření formátu každého řetězce v poli. Ověřování vyžaduje, aby měl každý řetězec formu telefonního čísla, ve kterém jsou tři skupiny číslic oddělené pomlčkami, první dvě skupiny obsahují tři číslice a třetí skupina obsahuje čtyři číslice. Vzor hledání používá regulární výraz `^\\d{3}-\\d{3}-\\d{4}$` . Další informace najdete v tématu [Jazyk regulárních výrazů – rychlé reference](../../standard/base-types/regular-expression-language-quick-reference.md).

| Vzor | Význam                             |
|---------|-------------------------------------|
| `^`     | odpovídá začátku řetězce |
| `\d{3}` | odpovídá přesně 3 číslicovým znakům  |
| `-`     | odpovídá znaku '-'           |
| `\d{3}` | odpovídá přesně 3 číslicovým znakům  |
| `-`     | odpovídá znaku '-'           |
| `\d{4}` | odpovídá přesně 4 znakům číslice  |
| `$`     | odpovídá konci řetězce       |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet4":::

Tento jednoduchý vzor hledání odpovídá mnoha platným řetězcům. Regulární výrazy jsou lepší vyhledat nebo ověřit proti vzorci místo jediného textového řetězce.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
- [LINQ a řetězce](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework regulární výrazy](../../standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md)
