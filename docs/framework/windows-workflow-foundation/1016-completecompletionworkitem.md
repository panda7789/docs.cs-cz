---
title: 1016 – CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925083"
---
# <a name="1016---completecompletionworkitem"></a>1016 – CompleteCompletionWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1016|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že položka CompletionWorkItem byla dokončena.  
  
## <a name="message"></a>Zpráva  
 Položka CompletionWorkItem byla dokončena pro nadřazenou aktivitu '%1', DisplayName: %2, InstanceId: '%3'. Dokončeno %4, DisplayName: %5, InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Nadřazená aktivita|xs:string|Název typu Nadřazená aktivita.|  
|ParentDisplayName|xs:string|Zobrazovaný název Nadřazená aktivita.|  
|ParentInstanceId|xs:string|Id instance Nadřazená aktivita.|  
|CompletedActivity|xs:string|Název typu dokončené aktivity.|  
|CompletedActivityDisplayName|xs:string|Zobrazovaný název dokončené aktivity.|  
|CompletedActivityInstanceId|xs:string|Id instance dokončené aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
