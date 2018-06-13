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
ms.openlocfilehash: 59f0441b79244eb529be338495c32af886a5f2b3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745094"
---
# <a name="startup-settings-schema"></a>Schéma nastavení spouštění
Spuštění – nastavení zadejte verzi modulu CLR, která by měla spustit aplikace.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime. Aplikace vytvořené s nástroji runtime verze 1.1 by měly používat  **\<supportedRuntime >** element.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|  
|[\<spuštění >](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.|  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Zadání kterou verzi modulu Runtime pro použití](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
