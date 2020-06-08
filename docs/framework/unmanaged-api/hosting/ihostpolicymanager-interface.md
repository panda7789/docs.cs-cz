---
title: IHostPolicyManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: d6b34403a45cc40863d79b59396041e496989045
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503927"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager – rozhraní
Poskytuje metody, které upozorňují na hostitele akcí, které modul CLR (Common Language Runtime) provede v případě přerušení, vypršení časového limitu nebo selhání.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[OnDefaultAction – metoda](ihostpolicymanager-ondefaultaction-method.md)|Upozorní hostitele, že modul CLR má převzít výchozí akci určenou voláním metody [ICLRPolicyManager:: setdefaultaction –](iclrpolicymanager-setdefaultaction-method.md) v reakci na přerušení nebo <xref:System.AppDomain> uvolnění vlákna.|  
|[OnFailure – metoda](ihostpolicymanager-onfailure-method.md)|Upozorní hostitele, že se chystá modul CLR, aby provedl akci určenou voláním [ICLRPolicyManager:: SetActionOnFailure –](iclrpolicymanager-setactiononfailure-method.md) v reakci na přidělení prostředků nebo selhání opětovného získávání.|  
|[OnTimeout – metoda](ihostpolicymanager-ontimeout-method.md)|Upozorní hostitele, že se chystá modul CLR provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnTimeout –](iclrpolicymanager-setactionontimeout-method.md) v reakci na časový limit.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](eclrfailure-enumeration.md)
- [EClrOperation – výčet](eclroperation-enumeration.md)
- [EPolicyAction – výčet](epolicyaction-enumeration.md)
- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
