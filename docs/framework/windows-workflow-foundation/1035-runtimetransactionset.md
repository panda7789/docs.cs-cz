---
title: 1035 – RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924849"
---
# <a name="1035---runtimetransactionset"></a>1035 – RuntimeTransactionSet
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1035|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita nastavil běhové transakce.  
  
## <a name="message"></a>Zpráva  
 Běhová transakce byla nastavena aktivitou %1, DisplayName: %2, InstanceId: '%3'.  Provádění bylo izolováno na aktivitu na %4, DisplayName: %5, InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:string|Název typu aktivity.|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|InstanceId|xs:string|Id instance aktivity.|  
|IsolatedActivity|xs:string|Název typu aktivity, která transakce je izolovaná na.|  
|IsolatedActivityDisplayName|xs:string|Zobrazovaný název aktivity, která transakce je izolováno na.|  
|IsolatedActivityInstanceId|xs:string|Id instance, která transakce je izolovaná na aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
