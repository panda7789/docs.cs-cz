---
title: IHostAutoEvent – rozhraní
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: a24939ac0b0808546ef3615fae4909c6c3cf8a2e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804996"
---
# <a name="ihostautoevent-interface"></a>IHostAutoEvent – rozhraní
Poskytuje reprezentaci implementace události automatického resetování hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Set – metoda](ihostautoevent-set-method.md)|Nastaví aktuální `IHostAutoEvent` instanci na signálový stav.|  
|[Wait – metoda](ihostautoevent-wait-method.md)|Způsobí, že aktuální `IHostAutoEvent` instance počká, dokud událost nevlastníte nebo dokud neuplyne zadaný čas.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostManualEvent – rozhraní](ihostmanualevent-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
