---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237621"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Vylepšení gridových řádků prostoru přidělování algoritmu

|   |   |
|---|---|
|Podrobnosti|Opravena chyba v [algoritmu pro přidělování velikostí](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) <xref:System.Windows.Controls.Grid> v souboru .NET Framework 4.7.  V některých případech, například Grid s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky byly uspořádány na nesprávné pozici, případně mimo Grid úplně.|
|Návrh|Aby aplikace mohla využívat tyto změny, musí být spuštěna v rozhraní .NET Framework 4.8 nebo novějším.|
|Rozsah|Hlavní|
|Version|4.8|
|Typ|Modul runtime|
