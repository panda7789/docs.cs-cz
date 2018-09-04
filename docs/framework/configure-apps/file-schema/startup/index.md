---
title: Schéma nastavení spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 68f37e3efca784b94be90d5779c9bc402f144448
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530331"
---
# <a name="startup-settings-schema"></a>Schéma nastavení spouštění
Nastavení spuštění zadat verzi common language runtime, který by měla spustit aplikace.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime. Používejte aplikace sestavené s modulem runtime verze 1.1  **\<supportedRuntime >** elementu.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|  
|[\<Po spuštění >](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.|  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Určení verze modulu Runtime, která k použití](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
