---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d483a681cae6328dd6111b320a12b5a064d3ff5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1014---schedulecompletionworkitem"></a>1014 - ScheduleCompletionWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1014|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že bylo naplánováno CompletionWorkItem.  
  
## <a name="message"></a>Zpráva  
 Bylo naplánováno CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.  Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Nadřazená aktivita|xs:String|Název typu nadřazené aktivity.|  
|ParentDisplayName|xs:String|Zobrazovaný název nadřazené aktivity.|  
|ParentInstanceId|xs:String|Id instance nadřazené aktivity.|  
|CompletedActivity|xs:String|Název typu dokončené aktivity.|  
|CompletedActivityDisplayName|xs:String|Zobrazovaný název dokončené aktivity.|  
|CompletedActivityInstanceId|xs:String|Id instance dokončené aktivity.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
