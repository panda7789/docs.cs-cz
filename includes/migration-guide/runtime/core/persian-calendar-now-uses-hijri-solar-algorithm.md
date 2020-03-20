---
ms.openlocfilehash: bfe406161ac754124a2cc38c68a80c3b9fb2c7f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858442"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Perský kalendář nyní používá algoritmus hijríslunce

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6 používá <xref:System.Globalization.PersianCalendar?displayProperty=name> třída algoritmus hijri. Převod dat mezi <xref:System.Globalization.PersianCalendar?displayProperty=name> a jiné kalendáře může způsobit mírně odlišný výsledek počínaje .NET Framework 4.6 pro data starší než 1800 nebo později než 2023 (gregoriánský). Také <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> je <code>March 22, 0622</code> nyní <code>March 21, 0622</code>místo .|
|Návrh|Uvědomte si, že některé časné nebo pozdní data se mohou mírně lišit při použití PersianCalendar v rozhraní .NET Framework 4.6. Také při serializaci dat mezi procesy, které mohou být spuštěny na různých verzích rozhraní .NET Framework, neukládejte je jako řetězce date PersianCalendar (protože tyto hodnoty se mohou lišit).|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
