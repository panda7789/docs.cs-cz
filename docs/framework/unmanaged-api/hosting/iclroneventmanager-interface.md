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
ms.openlocfilehash: 30312e6e09535cee2968b1f9e8ac87b461c5ff40
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703515"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager – rozhraní
Poskytuje metody, které umožňují hostiteli registrovat a odregistrovat zpětná volání pro události modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[RegisterActionOnEvent – metoda](iclroneventmanager-registeractiononevent-method.md)|Zaregistruje ukazatel zpětného volání pro zadanou událost.|  
|[UnregisterActionOnEvent – metoda](iclroneventmanager-unregisteractiononevent-method.md)|Zruší registraci dříve registrovaného ukazatele zpětného volání pro zadanou událost.|  
  
## <a name="remarks"></a>Poznámky  
 Pro registraci a zrušení registrace zpětných volání událostí hostitel získá odkaz na `ICLROnEventManager` volání metody [ICLRControl:: GetCLRManager –](iclrcontrol-getclrmanager-method.md) .  
  
> [!NOTE]
> Události popsané v [EClrEvent –](eclrevent-enumeration.md) lze aktivovat více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [EClrEvent – výčet](eclrevent-enumeration.md)
- [IActionOnCLREvent – rozhraní](iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
