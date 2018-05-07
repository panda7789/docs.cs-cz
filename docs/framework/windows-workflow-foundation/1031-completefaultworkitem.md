---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1031|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že je dokončená FaultWorkItem.  
  
## <a name="message"></a>Zpráva  
 FaultWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'. Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
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
