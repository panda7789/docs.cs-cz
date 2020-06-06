---
title: Schéma nastavení spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701512"
---
# <a name="startup-settings-schema"></a>Schéma nastavení spouštění

Nastavení spuštění určuje verzi modulu CLR (Common Language Runtime), která má aplikaci spustit.  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime). Aplikace sestavené s modulem runtime verze 1,1 by měly používat **\<supportedRuntime>** element.|  
|[\<supportedRuntime>](supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|  
|[\<startup>](startup-element.md)|Obsahuje **\<requiredRuntime>** prvky a **\<supportedRuntime>** .|  
  
## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru](../index.md)
- [Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
