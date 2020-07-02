---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621121"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Perské kalendář teď používá algoritmus hidžra. inflace.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,6 <xref:System.Globalization.PersianCalendar?displayProperty=fullName> Třída používá algoritmus hidžra. Převod dat mezi daty <xref:System.Globalization.PersianCalendar?displayProperty=fullName> a dalšími kalendáři může způsobit trochu odlišný výsledek začínající .NET Framework 4,6 pro data starší než 1800 nebo novější než 2023 (gregoriánský). Také <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> je nyní <code>March 22, 0622</code> místo <code>March 21, 0622</code> .

#### <a name="suggestion"></a>Návrh

Počítejte s tím, že některá počáteční nebo pozdě data mohou být mírně odlišná při použití PersianCalendar v .NET Framework 4,6. Při serializaci dat mezi procesy, které mohou běžet na různých verzích .NET Framework, je také neukládejte jako řetězce PersianCalendar data (protože se tyto hodnoty mohou lišit).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
