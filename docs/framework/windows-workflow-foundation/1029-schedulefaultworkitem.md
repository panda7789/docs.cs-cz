---
title: 1029 – ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924355"
---
# <a name="1029---schedulefaultworkitem"></a>1029 – ScheduleFaultWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1029|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že položka FaultWorkItem byla plánována.  
  
## <a name="message"></a>Zpráva  
 Položka FaultWorkItem byla plánována pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.  Výjimka byla rozšířena z aktivity %4, DisplayName: %5, InstanceId: '%6'.  
  
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
