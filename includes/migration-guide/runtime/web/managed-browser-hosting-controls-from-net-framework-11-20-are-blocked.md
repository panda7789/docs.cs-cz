---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620071"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Spravované prohlížeče hostující ovládací prvky z .NET Framework 1,1 a 2,0 jsou blokované

#### <a name="details"></a>Podrobnosti

Hostování těchto ovládacích prvků je blokováno v aplikaci Internet Explorer.

#### <a name="suggestion"></a>Návrh

Internet Explorer nespustí aplikaci, která používá hostovací ovládací prvky spravovaného prohlížeče. Předchozí chování lze obnovit nastavením hodnoty EnableIEHosting podklíče registru pro <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> <code>1</code> systémy x86 a 32 procesy v systémech x64 a nastavením <code>EnableIEHosting</code> hodnoty podklíče registru na <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> <code>1</code> 64 procesy v systémech x64.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime|
