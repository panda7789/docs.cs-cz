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
ms.openlocfilehash: b2c334c7a757c2f4044d08787bdae93ffc2804e4
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803887"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager – rozhraní
Poskytuje metody, které umožňují přístup a řízení kontextu zabezpečení aktuálně prováděného vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSecurityContext – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Získá požadovaná [IHostSecurityContext –](ihostsecuritycontext-interface.md) z hostitele.|  
|[ImpersonateLoggedOnUser – metoda](ihostsecuritymanager-impersonateloggedonuser-method.md)|Požaduje, aby se kód spustil s použitím přihlašovacích údajů aktuální identity uživatele.|  
|[OpenThreadToken – metoda](ihostsecuritymanager-openthreadtoken-method.md)|Otevře volitelný přístupový token přidružený k aktuálnímu vláknu.|  
|[RevertToSelf – metoda](ihostsecuritymanager-reverttoself-method.md)|Ukončí zosobnění identity aktuálního uživatele a vrátí původní token vlákna.|  
|[SetSecurityContext – metoda](ihostsecuritymanager-setsecuritycontext-method.md)|Nastaví kontext zabezpečení pro aktuálně prováděné vlákno.|  
|[SetThreadToken – metoda](ihostsecuritymanager-setthreadtoken-method.md)|Nastaví popisovač pro aktuálně prováděné vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může řídit všechna přístupová oprávnění k tokenům vláken pomocí modulu CLR (Common Language Runtime) i uživatelského kódu. Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu. `IHostSecurityContext`Zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro CLR.  
  
 Modul CLR zpracovává kontext spravovaného vlákna interně. Dotazuje se na konkrétní proces `IHostSecurityManager` v následujících situacích:  
  
- Ve vlákně finalizační metody při provádění finalizační metody.  
  
- Během provádění konstruktoru třídy a modulu.  
  
- V asynchronních bodech v pracovním vlákně v volání metody [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) .  
  
- Při údržbě portů pro dokončení vstupně-výstupních operací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostSecurityContext – rozhraní](ihostsecuritycontext-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
