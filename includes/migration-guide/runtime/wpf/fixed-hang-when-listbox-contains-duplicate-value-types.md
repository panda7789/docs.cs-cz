---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622017"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a>Opraveno zablokování, když seznam obsahuje duplicitní typy hodnot

#### <a name="details"></a>Podrobnosti

Opravili jsme problém, kdy virtualizace <xref:System.Windows.Controls.ItemsControl> může během posouvání zareagovat, když kolekce položek obsahuje duplicitní objekty typu hodnoty.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4,8|
|Typ|Modul runtime|
