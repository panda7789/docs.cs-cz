---
title: 1036 – RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924836"
---
# <a name="1036---runtimetransactioncompletionrequested"></a>1036 – RuntimeTransactionCompletionRequested
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1036|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita bylo plánováno dokončení běhové transakce.  
  
## <a name="message"></a>Zpráva  
 Aktivita '%1', DisplayName: %2, InstanceId: '%3' bylo plánováno dokončení běhové transakce.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:string|Název typu aktivity.|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|InstanceId|xs:string|Id instance aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
