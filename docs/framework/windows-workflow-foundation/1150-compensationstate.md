---
title: 1150 – CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 61613a27c4d4d8fb0b206246fef25ae87def47a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923861"
---
# <a name="1150---compensationstate"></a>1150 – CompensationState
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1150|  
|klíčová slova|WFActivities|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Indikuje změnu stavu v aktivitu CompensableActivity.  
  
## <a name="message"></a>Zpráva  
 Aktivita CompensableActivity '%1' je ve stavu '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|Stav|xs:string|Stav kompenzaci.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
