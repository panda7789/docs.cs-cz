---
title: 208 – MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 3499131fcb52f0a0ab6d0e78e165522b7092612f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="208---messageinspectorafterreceiveinvoked"></a>208 – MessageInspectorAfterReceiveInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|208|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované po Model služby má vyvolat `AfterReceive` metodu na zpráva inspector.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolat 'AfterReceiveReply' na MessageInspector typu '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Položka FullName CLR typu vyvolanou `MessageInspector`.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
