---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509969"
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1009|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita je naplánován pro spuštění.  
  
## <a name="message"></a>Zpráva  
 Nadřazená aktivita %1, DisplayName: %2, identifikátor InstanceId: '%3' naplánované podřízené aktivity "%4", DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Nadřazená aktivita|xs:String|Název typu nadřazené aktivity.|  
|ParentDisplayName|xs:String|Zobrazovaný název nadřazené aktivity.|  
|ParentInstanceId|xs:String|Id instance nadřazené aktivity.|  
|ChildActivity|xs:String|Název typu naplánované podřízené aktivity.|  
|ChildDisplayName|xs:String|Zobrazovaný název naplánované podřízené aktivity.|  
|ChildInstanceId|xs:String|Id instance plánované podřízené aktivity.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
