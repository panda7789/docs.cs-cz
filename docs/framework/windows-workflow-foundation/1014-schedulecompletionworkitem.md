---
title: 1014 – ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982264"
---
# <a name="1014---schedulecompletionworkitem"></a>1014 – ScheduleCompletionWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1014|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že položka CompletionWorkItem byla plánována.  
  
## <a name="message"></a>Zpráva  
 Položka CompletionWorkItem byla plánována-Nadřazená aktivita '%1', DisplayName: %2, InstanceId: '%3'.  Dokončeno %4, DisplayName: %5, InstanceId: '%6'.  
  
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
