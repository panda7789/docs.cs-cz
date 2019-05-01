---
title: 1010 – ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008368"
---
# <a name="1010---activitycompleted"></a>1010 – ActivityCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1010|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita byl dokončen.  
  
## <a name="message"></a>Zpráva  
 Aktivita '%1', DisplayName: %2, InstanceId: '%3' byla dokončena ve stavu "%4".  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:string|Název typu aktivity.|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|InstanceId|xs:string|Id instance aktivity.|  
|Stav|xs:string|Stav aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
