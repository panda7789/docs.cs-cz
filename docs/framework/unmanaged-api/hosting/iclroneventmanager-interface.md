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
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140839"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager – rozhraní
Poskytuje metody, které umožňují hostiteli registrovat a odregistrovat zpětná volání pro události modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[RegisterActionOnEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|Zaregistruje ukazatel zpětného volání pro zadanou událost.|  
|[UnregisterActionOnEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|Zruší registraci dříve registrovaného ukazatele zpětného volání pro zadanou událost.|  
  
## <a name="remarks"></a>Poznámky  
 Pro registraci a zrušení registrace zpětných volání událostí hostitel získá odkaz na `ICLROnEventManager` zavoláním metody [ICLRControl:: GetCLRManager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .  
  
> [!NOTE]
> Události popsané v [EClrEvent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) lze aktivovat více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
