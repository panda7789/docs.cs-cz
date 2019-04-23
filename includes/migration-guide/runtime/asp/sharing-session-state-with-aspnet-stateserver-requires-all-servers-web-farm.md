---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981528"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Sdílení stavu relace s Asp.Net StateServer vyžaduje všechny servery ve webové farmě, aby používal stejnou verzi rozhraní .NET Framework

|   |   |
|---|---|
|Podrobnosti|Při povolování <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> stavu relace, všechny servery v dané webové farmě musí používat stejnou verzi rozhraní .NET Framework v pořadí pro stav tak, aby správně sdílené.|
|Doporučení|Ujistěte se, že upgrade verze rozhraní .NET Framework na webových serverech, které sdílejí stavu ve stejnou dobu.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
