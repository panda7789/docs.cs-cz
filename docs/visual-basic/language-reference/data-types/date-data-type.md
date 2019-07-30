---
title: Date – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: ee966cdfcc957f1164c73f577fa668b203a82113
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630117"
---
# <a name="date-data-type-visual-basic"></a>Date – datový typ (Visual Basic)

Obsahuje hodnoty IEEE 64 (8 bajtů), které reprezentují data od 1. ledna do 31. prosince 9999 a časy od 12:00:00 (půlnoc) do 11:59:59.9999999 ODP. Každý přírůstek představuje 100 nanosekund, uplynulý čas od začátku 1. ledna v roce 1 v gregoriánském kalendáři. Maximální hodnota představuje 100 nanosekund před začátkem 1. ledna v roce 10000.

## <a name="remarks"></a>Poznámky

`Date` Datový typ použijte k zahrnutí hodnot data, času nebo hodnoty data a času.

Výchozí hodnota `Date` je 0:00:00 (půlnoc) od 1. ledna 0001.

Aktuální datum a čas můžete získat z <xref:Microsoft.VisualBasic.DateAndTime> třídy.

## <a name="format-requirements"></a>Požadavky na formát

Je nutné uzavřít `Date` literál v rámci znaménka čísla (`# #`). Je třeba zadat hodnotu data ve formátu M/d/rrrr, `#5/31/1993#`například nebo rrrr-mm-dd, `#1993-5-31#`například. Při prvním zadání roku můžete použít lomítka.  Tento požadavek nezávisí na vašem národním prostředí a na nastavení formátu data a času vašeho počítače.

Důvodem tohoto omezení je, že význam vašeho kódu by se nikdy neměl měnit v závislosti na národním prostředí, ve kterém je vaše aplikace spuštěná. Předpokládejme, že máte pevně zavedený `#3/4/1998#` kód `Date` literálu a máte v úmyslu do 4. března 1998. V národním prostředí, které používá mm/dd/rrrr, se 3/4/1998 zkompiluje jako zamýšlená. Ale Předpokládejme, že nasadíte aplikaci v mnoha zemích nebo oblastech. V národním prostředí, které používá dd/mm/rrrr, je pevně zakódovaný literál zkompilován do 3. dubna 1998. V národním prostředí, které používá rrrr/mm/dd, bude literál neplatný (duben 1998, 0003) a způsobit chybu kompilátoru.

## <a name="workarounds"></a>Alternativní řešení

Chcete-li `Date` převést literál na formát národního prostředí nebo na vlastní formát, zadejte do <xref:Microsoft.VisualBasic.Strings.Format%2A> funkce literál a zadejte buď předdefinovaný nebo uživatelsky definovaný formát data. Následující příklad ukazuje to.

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

Alternativně můžete použít jeden z přetížených konstruktorů <xref:System.DateTime> struktury k sestavení hodnoty data a času. Následující příklad vytvoří hodnotu, která představuje 31. května 1993 v 12:14 za odpoledne.

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a>Formát hodiny

Hodnotu času můžete zadat buď v 12 hodinách, nebo ve 24hodinovém formátu, například `#1:15:30 PM#` nebo. `#13:15:30#` Pokud však nezadáte buď minuty, nebo sekundy, je nutné zadat dop nebo PM.

## <a name="date-and-time-defaults"></a>Výchozí hodnoty data a času

Pokud nezahrnete datum do literálu data a času, Visual Basic nastaví část hodnoty data na 1. ledna 0001. Pokud nezahrnete čas do literálu data a času, Visual Basic nastaví časovou část hodnoty na začátek dne, tj. půlnoc (0:00:00).

## <a name="type-conversions"></a>Převody typu

Převedete `Date` -li hodnotu `String` na typ, Visual Basic vykreslí datum podle formátu krátkého data určeného národním prostředím runtime a vykreslí čas podle formátu času (12 hodin nebo 24 hodin) určeného parametrem národní prostředí v době běhu.

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte na to, že typy data a času v jiných prostředích nejsou kompatibilní s `Date` typem Visual Basic. Pokud předáváte argument typu datum/čas pro takovou komponentu, deklarujte ji jako `Double` `Date` místo v novém Visual Basic kódu a použijte metody <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> převodu a <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.

- **Znaky typu.** `Date`nemá žádný znak typu literálu nebo znak typu identifikátoru. Nicméně kompilátor zpracovává literály, které jsou uzavřeny v symbolech`# #`čísla ( `Date`) jako.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.DateTime?displayProperty=nameWithType> struktura.

## <a name="example"></a>Příklad

Proměnná nebo konstanta `Date` datového typu obsahuje datum i čas. Toto dokládá následující příklad.

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a>Viz také:

- <xref:System.DateTime?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Standardní řetězce formátu data a času](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
