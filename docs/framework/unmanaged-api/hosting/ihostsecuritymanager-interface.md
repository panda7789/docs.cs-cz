---
title: IHostSecurityManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 9b7cc41848e41976f388e38bf22c9ea0f90abbae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121483"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager – rozhraní
Poskytuje metody, které umožňují přístup a řízení kontextu zabezpečení aktuálně prováděného vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSecurityContext – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Získá požadovaná [IHostSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.|  
|[ImpersonateLoggedOnUser – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Požaduje, aby se kód spustil s použitím přihlašovacích údajů aktuální identity uživatele.|  
|[OpenThreadToken – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Otevře volitelný přístupový token přidružený k aktuálnímu vláknu.|  
|[RevertToSelf – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Ukončí zosobnění identity aktuálního uživatele a vrátí původní token vlákna.|  
|[SetSecurityContext – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Nastaví kontext zabezpečení pro aktuálně prováděné vlákno.|  
|[SetThreadToken – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Nastaví popisovač pro aktuálně prováděné vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může řídit všechna přístupová oprávnění k tokenům vláken pomocí modulu CLR (Common Language Runtime) i uživatelského kódu. Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu. `IHostSecurityContext` zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro CLR.  
  
 Modul CLR zpracovává kontext spravovaného vlákna interně. Dotazuje se `IHostSecurityManager` specifických pro proces v následujících situacích:  
  
- Ve vlákně finalizační metody při provádění finalizační metody.  
  
- Během provádění konstruktoru třídy a modulu.  
  
- V asynchronních bodech v pracovním vlákně v volání metody [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) .  
  
- Při údržbě portů pro dokončení vstupně-výstupních operací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
