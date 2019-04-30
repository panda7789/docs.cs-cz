---
title: 402 – StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: 6dfb3b187f58de2c9573c2d2f6d579e3557c3de8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774950"
---
# <a name="402---startsignpostevent"></a>402 – StartSignpostEvent
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|402|  
|klíčová slova|Poradce při potížích|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost označuje začátek aktivity začátku do konce. Obsahuje název aktivity.  
  
## <a name="message"></a>Zpráva  
 Hranice aktivity.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Rozšířená Data|`xs:string`|Název aktivity.|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
