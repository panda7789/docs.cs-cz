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
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804328"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager – rozhraní
Poskytuje metody, které upozorňují na hostitele akcí, které modul CLR (Common Language Runtime) provede v případě přerušení, vypršení časového limitu nebo selhání.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnDefaultAction – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Upozorní hostitele, že modul CLR má převzít výchozí akci určenou voláním metody [ICLRPolicyManager:: setdefaultaction –](iclrpolicymanager-setdefaultaction-method.md) v reakci na přerušení nebo <xref:System.AppDomain> uvolnění vlákna.|  
|[OnFailure – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|Upozorní hostitele, že se chystá modul CLR, aby provedl akci určenou voláním [ICLRPolicyManager:: SetActionOnFailure –](iclrpolicymanager-setactiononfailure-method.md) v reakci na přidělení prostředků nebo selhání opětovného získávání.|  
|[OnTimeout – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|Upozorní hostitele, že se chystá modul CLR provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnTimeout –](iclrpolicymanager-setactionontimeout-method.md) v reakci na časový limit.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [EClrFailure – výčet](eclrfailure-enumeration.md)
- [EClrOperation – výčet](eclroperation-enumeration.md)
- [EPolicyAction – výčet](epolicyaction-enumeration.md)
- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
