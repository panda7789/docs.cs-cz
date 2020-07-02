---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621997"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Vylepšení algoritmu přidělujícího místo řádků v mřížce

#### <a name="details"></a>Podrobnosti

Opravili jsme chybu v [algoritmu pro přidělování velikostí do](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) v <xref:System.Windows.Controls.Grid> zavedeném v .NET Framework 4,7.  V některých případech, například v mřížce <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, byly řádky uspořádány na nesprávnou pozici, případně mimo mřížku.

#### <a name="suggestion"></a>Návrh

Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4,8 nebo novější.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4,8|
|Typ|Modul runtime|
