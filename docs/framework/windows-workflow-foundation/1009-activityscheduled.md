---
title: 1009 – ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924654"
---
# <a name="1009---activityscheduled"></a>1009 – ActivityScheduled
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1009|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že pro spuštění je naplánované aktivity.  
  
## <a name="message"></a>Zpráva  
 Nadřazená aktivita %1, DisplayName: %2, InstanceId: '%3' naplánovala podřízenou aktivitu "%4", DisplayName: %5, InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Nadřazená aktivita|xs:string|Název typu Nadřazená aktivita.|  
|ParentDisplayName|xs:string|Zobrazovaný název Nadřazená aktivita.|  
|ParentInstanceId|xs:string|Id instance Nadřazená aktivita.|  
|ChildActivity|xs:string|Název typu naplánovala podřízenou aktivitu.|  
|ChildDisplayName|xs:string|Zobrazovaný název naplánovala podřízenou aktivitu.|  
|ChildInstanceId|xs:string|Id instance naplánovala podřízenou aktivitu.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
