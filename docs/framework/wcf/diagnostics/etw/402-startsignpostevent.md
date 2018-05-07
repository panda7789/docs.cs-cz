---
title: 402 – StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: 6dfb3b187f58de2c9573c2d2f6d579e3557c3de8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="402---startsignpostevent"></a>402 – StartSignpostEvent
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|402|  
|Klíčová slova|Poradce při potížích|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost označuje začátek aktivitu začátku do konce. Obsahuje název aktivity.  
  
## <a name="message"></a>Zpráva  
 Aktivita hranic.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Rozšířená Data|`xs:string`|Název aktivity.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
