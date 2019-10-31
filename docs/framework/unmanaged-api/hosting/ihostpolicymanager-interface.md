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
ms.openlocfilehash: 6ba7b7adc104db528293d77c3591370c6ce02c25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128601"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager – rozhraní
Poskytuje metody, které upozorňují na hostitele akcí, které modul CLR (Common Language Runtime) provede v případě přerušení, vypršení časového limitu nebo selhání.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnDefaultAction – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Upozorní hostitele, že modul CLR má převzít výchozí akci určenou voláním metody [ICLRPolicyManager:: setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) v reakci na přerušení vlákna nebo <xref:System.AppDomain> uvolnění.|  
|[OnFailure – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|Upozorní hostitele, že se chystá modul CLR, aby provedl akci určenou voláním [ICLRPolicyManager:: SetActionOnFailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) v reakci na přidělení prostředků nebo selhání opětovného získávání.|  
|[OnTimeout – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|Upozorní hostitele, že se chystá modul CLR provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) v reakci na časový limit.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation – výčet](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
