---
title: 1031 – CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008795"
---
# <a name="1031---completefaultworkitem"></a>1031 – CompleteFaultWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1031|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že položka FaultWorkItem byla dokončena.  
  
## <a name="message"></a>Zpráva  
 Položka FaultWorkItem byla dokončena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'. Výjimka byla rozšířena z aktivity %4, DisplayName: %5, InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|Název typu selhání aktivity.|  
|FaultActivityDisplayName|xs:string|Zobrazovaný název selhání aktivity.|  
|FaultActivityInstanceId|xs:string|Id instance selhání aktivity.|  
|ExceptionActivity|xs:string|Název typu aktivity, která vyvolala výjimku.|  
|ExceptionActivityDisplayName|xs:string|Zobrazovaný název aktivity, která vyvolala výjimku.|  
|ExceptionActivityInstanceId|xs:string|Id instance aktivity, která vyvolala výjimku.|  
|Výjimka|xs:string|Podrobnosti o výjimce pro výjimku|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
