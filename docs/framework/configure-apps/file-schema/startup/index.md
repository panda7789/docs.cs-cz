---
title: "Schéma nastavení spouštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 61ea6d0c974683e73e835720cff48ff84169217e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [\<PaveOver > Zadání kterou verzi modulu Runtime pro použití](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
