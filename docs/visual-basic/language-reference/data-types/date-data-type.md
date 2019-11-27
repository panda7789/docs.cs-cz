---
title: Date – datový typ
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
ms.openlocfilehash: 972df72874753a0f1213f3a4942468c59e3913ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344029"
---
# <a name="date-data-type-visual-basic"></a>Date – datový typ (Visual Basic)

Obsahuje hodnoty IEEE 64 (8 bajtů), které reprezentují data od 1. ledna do 31. prosince 9999 a časy od 12:00:00 (půlnoc) do 11:59:59.9999999 ODP. Každý přírůstek představuje 100 nanosekund, uplynulý čas od začátku 1. ledna v roce 1 v gregoriánském kalendáři. Maximální hodnota představuje 100 nanosekund před začátkem 1. ledna v roce 10000.

## <a name="remarks"></a>Poznámky

Datový typ `Date` použijte k omezení hodnot data, času nebo hodnoty data a času.

Výchozí hodnota `Date` je 0:00:00 (půlnoc) 1. ledna 0001.

Aktuální datum a čas můžete získat z <xref:Microsoft.VisualBasic.DateAndTime> třídy.

## <a name="format-requirements"></a>Požadavky na formát

V symbolech čísla (`# #`) je nutné uzavřít `Date` literál. Je třeba zadat hodnotu data ve formátu M/d/rrrr, například `#5/31/1993#`nebo RRRR-MM-DD, například `#1993-5-31#`. Při prvním zadání roku můžete použít lomítka.  Tento požadavek nezávisí na vašem národním prostředí a na nastavení formátu data a času vašeho počítače.

Důvodem tohoto omezení je, že význam vašeho kódu by se nikdy neměl měnit v závislosti na národním prostředí, ve kterém je vaše aplikace spuštěná. Předpokládejme, že máte pevně zavedený `Date` literál `#3/4/1998#` a máte na mysli 4. března 1998. V národním prostředí, které používá mm/dd/rrrr, se 3/4/1998 zkompiluje jako zamýšlená. Ale Předpokládejme, že nasadíte aplikaci v mnoha zemích nebo oblastech. V národním prostředí, které používá dd/mm/rrrr, je pevně zakódovaný literál zkompilován do 3. dubna 1998. V národním prostředí, které používá rrrr/mm/dd, bude literál neplatný (duben 1998, 0003) a způsobit chybu kompilátoru.

## <a name="workarounds"></a>Alternativní řešení

Chcete-li převést `Date` literálu na formát národního prostředí nebo na vlastní formát, zadejte literál do funkce <xref:Microsoft.VisualBasic.Strings.Format%2A> a zadejte buď předdefinovaný nebo uživatelsky definovaný formát data. Následující příklad ukazuje to.

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

Alternativně můžete použít jeden z přetížených konstruktorů struktury <xref:System.DateTime> k sestavení hodnoty data a času. Následující příklad vytvoří hodnotu, která představuje 31. května 1993 v 12:14 za odpoledne.

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a>Formát hodiny

Hodnotu času můžete zadat buď do 12 hodin, nebo ve 24hodinovém formátu, například `#1:15:30 PM#` nebo `#13:15:30#`. Pokud však nezadáte buď minuty, nebo sekundy, je nutné zadat dop nebo PM.

## <a name="date-and-time-defaults"></a>Výchozí hodnoty data a času

Pokud nezahrnete datum do literálu data a času, Visual Basic nastaví část hodnoty data na 1. ledna 0001. Pokud nezahrnete čas do literálu data a času, Visual Basic nastaví časovou část hodnoty na začátek dne, tj. půlnoc (0:00:00).

## <a name="type-conversions"></a>Převody typu

Převedete-li `Date` hodnotu na typ `String`, Visual Basic vykreslí datum podle formátu krátkého data určeného národním prostředím runtime a vykreslí čas podle formátu času (12 hodin nebo 24 hodin) určeného národním prostředím runtime.

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte na to, že typy data a času v jiných prostředích nejsou kompatibilní s typem `Date` Visual Basic. Pokud předáváte argument typu datum/čas do takové součásti, deklarujte ji jako `Double` místo `Date` v novém kódu Visual Basic a použijte metody převodu <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> a <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.

- **Znaky typu.** `Date` nemá žádný znak typu literálu ani znak typu identifikátoru. Nicméně Kompilátor považuje literály uzavřené v symbolech čísla (`# #`) jako `Date`.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.DateTime?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Proměnná nebo konstanta datového typu `Date` obsahuje data i čas. Toto dokládá následující příklad.

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
