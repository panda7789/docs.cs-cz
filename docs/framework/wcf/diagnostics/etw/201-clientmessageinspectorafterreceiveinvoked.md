---
title: 201 – ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 96ca318c141d49e2ac5594d5ee101658a2aa8f21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782030"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a>201 – ClientMessageInspectorAfterReceiveInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|201|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován po má Model služby `AfterReceiveReply` metodu na inspektoru zprávy klienta.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolal metodu 'AfterReceiveReply"na třídě ClientMessageInspector typu '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Celý název CLR typu vyvolaný inspector.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
