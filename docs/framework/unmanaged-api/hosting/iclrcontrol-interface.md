---
title: ICLRControl – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615833"
---
# <a name="iclrcontrol-interface"></a>ICLRControl – rozhraní
Poskytuje metody, které umožňují hostiteli získat odkazy na a konfigurovat aspekty modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCLRManager – metoda](iclrcontrol-getclrmanager-method.md)|Získá ukazatel rozhraní na instanci kteréhokoli typu správce, který může hostitel použít ke konfiguraci CLR.|  
|[SetAppDomainManagerType – metoda](iclrcontrol-setappdomainmanagertype-method.md)|Nastaví typ odvozený od <xref:System.AppDomainManager> jako typ pro správce domény aplikace.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)
- [ICLRDebugManager – rozhraní](iclrdebugmanager-interface.md)
- [ICLRGCManager – rozhraní](iclrgcmanager-interface.md)
- [ICLRHostBindingPolicyManager – rozhraní](iclrhostbindingpolicymanager-interface.md)
- [ICLRHostProtectionManager – rozhraní](iclrhostprotectionmanager-interface.md)
- [ICLROnEventManager – rozhraní](iclroneventmanager-interface.md)
- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [IHostControl – rozhraní](ihostcontrol-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
