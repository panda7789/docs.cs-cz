---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f9b09001212de6d5aa4f5fde577b9eeb9d967ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1016---completecompletionworkitem"></a>1016 - CompleteCompletionWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1016|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že je dokončená CompletionWorkItem.  
  
## <a name="message"></a>Zpráva  
 Bylo dokončeno CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'. Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
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
