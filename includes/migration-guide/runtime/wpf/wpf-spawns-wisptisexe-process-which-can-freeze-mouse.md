---
ms.openlocfilehash: e0f72d19a884087b1f0f6ebd1b6baea75bc37af4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620105"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF vytvoří proces wisptis.exe, který může zablokovat myš.

#### <a name="details"></a>Podrobnosti

Byl představen problém v 4.5.2, který způsobuje, že <code>wisptis.exe</code> by bylo možné zablokovat vstup myši.

#### <a name="suggestion"></a>Návrh

Oprava tohoto problému je k dispozici v servisním vydání .NET Framework 4.5.2 (kumulativní oprava hotfix 3026376) nebo prostřednictvím upgradu na .NET Framework 4,6

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4.5.2|
|Typ|Modul runtime|
