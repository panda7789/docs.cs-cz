---
title: 404 - ResumeSignpostEvent
ms.date: 03/30/2017
ms.assetid: 395cc7ca-f35f-4295-be97-39a077f99c97
ms.openlocfilehash: 258e2f7e4b9dc1025461519593204c196bf6f415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048860"
---
# <a name="404---resumesignpostevent"></a>404 - ResumeSignpostEvent
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|404|  
|klíčová slova|Poradce při potížích|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost označuje opětovné aktivity začátku do konce. Obsahuje název aktivity.  
  
## <a name="message"></a>Zpráva  
 Hranice aktivity.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Rozšířená Data|`xs:string`|Název aktivity.|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
