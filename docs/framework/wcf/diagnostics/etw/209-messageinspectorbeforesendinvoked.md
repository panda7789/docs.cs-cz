---
title: 209 – MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="209---messageinspectorbeforesendinvoked"></a>209 – MessageInspectorBeforeSendInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|209|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované po Model služby má vyvolat `BeforeSend` metodu na zpráva inspector.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolat 'BeforeSendRequest' na MessageInspector typu '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Položka FullName CLR typu vyvolanou `MessageInspector`.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
