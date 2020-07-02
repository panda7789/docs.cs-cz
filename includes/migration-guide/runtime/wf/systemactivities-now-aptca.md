---
ms.openlocfilehash: beaac7b14535335a665add4fa056a60793879753
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620074"
---
### <a name="systemactivities-is-now-aptca"></a>System. Activitiess je teď APTCA.

#### <a name="details"></a>Podrobnosti

Sestavení je označeno <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributem.

#### <a name="suggestion"></a>Návrh

Odvozené třídy nelze označit pomocí <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> . Dříve musely být odvozené typy označeny pomocí <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> . Tato změna by však neměla mít žádný reálný dopad.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|
