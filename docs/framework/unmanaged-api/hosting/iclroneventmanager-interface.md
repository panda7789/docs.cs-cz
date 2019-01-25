---
title: ICLROnEventManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f927cece9997c78a75b1edecdb0a671203c3dd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646890"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager – rozhraní
Poskytuje metody, které umožňují hostitele tak, aby vytvářet a rušit registraci zpětná volání pro common language runtime (CLR) události.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[RegisterActionOnEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|Zaregistruje zpětné volání ukazatel zadané události.|  
|[UnregisterActionOnEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|Zrušení registrace již registrovaného zpětného volání ukazatel zadané události.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvářet a rušit registraci zpětná volání události, hostitel získá odkaz na `ICLROnEventManager` voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.  
  
> [!NOTE]
>  Události popisované v [eclrevent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) může být aktivována více než jednou a z různých vláken, který signalizuje, že uvolnění z paměti nebo vypnutí CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
