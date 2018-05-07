---
title: 440 - StartSignpostEvent1
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 4b2b6b0fa9df4725edd4929512eb1d7534d933b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="440---startsignpostevent1"></a>440 - StartSignpostEvent1
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|440|  
|Klíčová slova|Poradce při potížích|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 V trasování aktivit, označuje, že zpráva má spuštěn překročení hranici aktivity v odeslat nebo přijmout.  
  
## <a name="message"></a>Zpráva  
 Aktivita hranic.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|ExtendedData|`xs:string`|Název aktivity.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
