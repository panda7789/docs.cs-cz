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
ms.openlocfilehash: 0a03438968f487f574606f415fb9d43223030038
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222152"
---
# <a name="startup-settings-schema"></a>Schéma nastavení spouštění

Nastavení spuštění zadat verzi common language runtime, který by měla spustit aplikace.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<requiredRuntime >](requiredruntime-element.md)|Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime. Používejte aplikace sestavené s modulem runtime verze 1.1  **\<supportedRuntime >** elementu.|  
|[\<supportedRuntime >](supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|  
|[\<Po spuštění >](startup-element.md)|Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.|  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)  
- [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)