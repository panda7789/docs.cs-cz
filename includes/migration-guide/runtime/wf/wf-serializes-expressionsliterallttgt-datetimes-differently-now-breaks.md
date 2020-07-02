---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620077"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializace výrazy. literály T literály se &lt; &gt; teď liší (přerušují vlastní analyzátory XAML).

#### <a name="details"></a>Podrobnosti

Přidružený <xref:System.Windows.Markup.ValueSerializer> objekt převede <xref:System.DateTime?displayProperty=fullName> objekt nebo, <xref:System.DateTimeOffset?displayProperty=fullName> jehož sekunda a <xref:System.DateTime.Millisecond?displayProperty=fullName> komponenty jsou nenulové a (pro <xref:System.DateTime?displayProperty=fullName> hodnotu), jejíž vlastnost není <xref:System.DateTime.Kind> určena pro syntaxi elementu vlastnosti místo řetězce. Tato změna umožňuje <xref:System.DateTime?displayProperty=fullName> , <xref:System.DateTimeOffset?displayProperty=fullName> aby hodnoty a byly kulaté Trip. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.

#### <a name="suggestion"></a>Návrh

Tato změna umožňuje <xref:System.DateTime?displayProperty=fullName> , <xref:System.DateTimeOffset?displayProperty=fullName> aby hodnoty a byly kulaté Trip. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|
