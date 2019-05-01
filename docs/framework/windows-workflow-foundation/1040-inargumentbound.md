---
title: 1040 – InArgumentBound
ms.date: 03/30/2017
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
ms.openlocfilehash: 984372c07ccfb11f2f05d5488fa5ffc95075db41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009744"
---
# <a name="1040---inargumentbound"></a>1040 – InArgumentBound
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1040|  
|klíčová slova|WFActivities|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že byla vázaná v argumentu.  
  
## <a name="message"></a>Zpráva  
 V argumentu '%1' pro aktivitu %2, DisplayName: %3, InstanceId: '%4' byla svázána s hodnotou: %5.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Argument InArgument|xs:string|Název argument InArgument.|  
|Aktivita|xs:string|Název typu aktivity.|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|InstanceId|xs:string|Id instance aktivity.|  
|Hodnota|xs:string|Hodnota vázán argument InArgument.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
