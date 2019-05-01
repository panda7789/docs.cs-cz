---
title: 1015 – StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032263"
---
# <a name="1015---startcompletionworkitem"></a>1015 – StartCompletionWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1015|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že položka CompletionWorkItem je spuštění.  
  
## <a name="message"></a>Zpráva  
 Spouštění provedení položky CompletionWorkItem pro nadřízenou aktivitu '%1', DisplayName: %2, InstanceId: '%3'. Dokončeno %4, DisplayName: %5, InstanceId: '%6'.  
  
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
