---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619939"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Sdílení stavu relace s Asp.Net StateServer vyžaduje, aby všechny servery ve webové farmě používaly stejnou verzi .NET Framework

#### <a name="details"></a>Podrobnosti

Při povolování <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> stavu relace musí všechny servery v dané webové farmě používat stejnou verzi .NET Framework, aby bylo možné stav správně sdílet.

#### <a name="suggestion"></a>Návrh

Ujistěte se, že upgradujete .NET Framework verze na webových serverech, které sdílejí stav ve stejnou dobu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
