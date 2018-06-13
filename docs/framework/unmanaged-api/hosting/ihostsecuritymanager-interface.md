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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13f60730fedef4876f81f078f811104777050175
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440252"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager – rozhraní
Poskytuje metody, které umožňují přístup a kontrolu nad kontext zabezpečení aktuálně prováděné vlákno.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSecurityContext – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Získá požadované [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.|  
|[ImpersonateLoggedOnUser – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Požadavky kódu být spuštěn pomocí pověření aktuální identita uživatele.|  
|[OpenThreadToken – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Otevře se token přístupu přidružené k aktuální vlákno.|  
|[RevertToSelf – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Ukončí zosobnění aktuální identitu uživatele a vrátí původní tokenu vlákna.|  
|[SetSecurityContext – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Nastaví kontext zabezpečení pro aktuálně prováděné vlákno.|  
|[SetThreadToken – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Nastaví popisovač pro aktuálně prováděné vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel přístup můžete řídit všechny kód vlákno tokeny modul common language runtime (CLR) i uživatelského kódu. Ho můžete také zajistit, že dokončení zabezpečení informace o kontextu je předán přes asynchronních operací nebo body kódu s přístupem kód s omezeným přístupem. `IHostSecurityContext` zapouzdří tato informace kontextu zabezpečení, která je plné krytí modulu CLR.  
  
 Modul CLR interně zpracovává kontextu spravovaných vláken. Vyžádá si konkrétní proces `IHostSecurityManager` v následujících situacích:  
  
-   Ve vlákně finalizační metodu během provádění finalizační metodu.  
  
-   Během provádění konstruktoru třídy a modulu.  
  
-   V asynchronní bodů na pracovní vlákno ve voláních [ihostthreadpoolmanager::QueueUserWorkItem –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metoda.  
  
-   V obslužném portů dokončení vstupně-výstupní operace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
