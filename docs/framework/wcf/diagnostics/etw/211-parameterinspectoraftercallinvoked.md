---
title: 211 – ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: ada3ced31def2bb821b975e09f50ad83f28d56bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="211---parameterinspectoraftercallinvoked"></a>211 – ParameterInspectorAfterCallInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|211|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované po Model služby má vyvolat `AfterCall` metodu `ParameterInspector`.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolat 'AfterCall' na ParameterInspector typu '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název typu|`xs:string`|Položka FullName CLR typu vyvolanou `ParameterInspector`.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
