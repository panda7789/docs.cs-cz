---
title: 1018 – StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008860"
---
# <a name="1018---startcancelactivityworkitem"></a>1018 – StartCancelActivityWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1018|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že položka CancelActivityWorkItem je spuštění.  
  
## <a name="message"></a>Zpráva  
 Začátek provádění položky CancelActivityWorkItem pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:string|Název typu aktivity.|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|InstanceId|xs:string|Id instance aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
