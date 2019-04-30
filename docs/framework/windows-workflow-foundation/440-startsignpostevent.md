---
title: 440 – StartSignpostEvent1
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 4b2b6b0fa9df4725edd4929512eb1d7534d933b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774133"
---
# <a name="440---startsignpostevent1"></a>440 – StartSignpostEvent1
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|440|  
|klíčová slova|Poradce při potížích|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 V trasování činnosti, označuje, že zpráva má spuštěn překročení hranice aktivity v odeslání nebo přijetí.  
  
## <a name="message"></a>Zpráva  
 Hranice aktivity.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ExtendedData|`xs:string`|Název aktivity.|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
