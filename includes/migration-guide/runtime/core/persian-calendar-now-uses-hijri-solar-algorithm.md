---
ms.openlocfilehash: bfe406161ac754124a2cc38c68a80c3b9fb2c7f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664417"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Perský kalendář nyní používá algoritmus hidžra sluneční soustavy.

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6 <xref:System.Globalization.PersianCalendar?displayProperty=name> třída používá algoritmus sluneční hidžra. Převod dat mezi <xref:System.Globalization.PersianCalendar?displayProperty=name> a ostatních kalendářích, které může vytvořit výsledek mírně lišit od verze rozhraní .NET Framework 4.6 pro data starší než 1 800 nebo pozdější než 2023 (gregoriánského). Navíc <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> je nyní <code>March 22, 0622</code> místo <code>March 21, 0622</code>.|
|Doporučení|Mějte na paměti, že některá data časnému nebo pozdní může mírně lišit při používání perského kalendáře v rozhraní .NET Framework 4.6. Navíc při serializaci dat mezi procesy, které můžou běžet na různé verze rozhraní .NET Framework, nebudou ukládat je jako perského kalendáře řetězců kalendářních dat (protože mohou být tyto hodnoty odlišné).|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
