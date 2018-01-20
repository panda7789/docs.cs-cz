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
ms.workload: dotnet
ms.openlocfilehash: f344139fd7d7c84aa75ab5e17b6312f3b0c3e031
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="startup-settings-schema"></a>Schéma nastavení spouštění
Spuštění – nastavení zadejte verzi modulu CLR, která by měla spustit aplikace.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime. Aplikace vytvořené s nástroji runtime verze 1.1 by měly používat  **\<supportedRuntime >** element.|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|  
|[\<spuštění >](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.|  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Zadání kterou verzi modulu Runtime pro použití](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
