---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1029|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že bylo naplánováno FaultWorkItem.  
  
## <a name="message"></a>Zpráva  
 Bylo naplánováno FaultWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.  Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:String|Název typu selhání aktivity.|  
|FaultActivityDisplayName|xs:String|Zobrazovaný název selhání aktivity.|  
|FaultActivityInstanceId|xs:String|Id instance selhání aktivity.|  
|ExceptionActivity|xs:String|Název typu aktivity, která vrátila výjimku.|  
|ExceptionActivityDisplayName|xs:String|Zobrazovaný název aktivity, která vrátila výjimku.|  
|ExceptionActivityInstanceId|xs:String|Id instance aktivity, která vrátila výjimku.|  
|Výjimka|xs:String|Podrobnosti o výjimce pro výjimky|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
