---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
