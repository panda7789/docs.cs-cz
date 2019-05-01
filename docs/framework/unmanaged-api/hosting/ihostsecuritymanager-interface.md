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
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957583"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager – rozhraní
Poskytuje metody, které umožňují přístup a kontrolu nad kontextu zabezpečení aktuálně spuštěné vlákno.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSecurityContext – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Získá požadovanou [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.|  
|[ImpersonateLoggedOnUser – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Požadavky, který kód spuštěn pomocí pověření aktuální identitu uživatele.|  
|[OpenThreadToken – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Otevře se token přístupu spojený s aktuální vlákno.|  
|[RevertToSelf – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Zosobnění aktuální identitu uživatele se ukončí a vrátí původní token vlákna.|  
|[SetSecurityContext – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Nastaví kontext zabezpečení pro aktuálně spuštěné vlákno.|  
|[SetThreadToken – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Nastaví obslužnou rutinu pro aktuálně spuštěné vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitele můžete řídit veškerý kód přístup k vláknu tokeny common language runtime (CLR) a kód uživatele. Můžete také zajistit zabezpečení úplné informace o kontextu je předán přes asynchronní operace nebo body kódu s přístup ke kódu s omezeným přístupem. `IHostSecurityContext` zapouzdřuje tyto informace kontextu zabezpečení, což je neprůhledný modulu CLR.  
  
 Modul CLR interně zpracovává kontext spravované vlákna. Dotazy specifické pro proces `IHostSecurityManager` v následujících situacích:  
  
- Na finalizační podproces během spuštění finalizační metody.  
  
- Během provádění konstruktoru třídy a modulu.  
  
- V asynchronní body na pracovního vlákna ve voláních [ihostthreadpoolmanager::QueueUserWorkItem –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metody.  
  
- V obslužném portů dokončení vstupně-výstupních operací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
