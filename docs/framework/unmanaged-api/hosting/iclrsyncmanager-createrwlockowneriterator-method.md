---
title: ICLRSyncManager::CreateRWLockOwnerIterator – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: f8fde4905c41dffde90c6361b5a8cdffa15deb4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503962"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator – metoda
Požadavky, které modul CLR (Common Language Runtime) vytvoří iterátor, který může hostitel použít k určení sady úloh čekajících na zámek pro zápis čtenářů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cookie`  
 pro Soubor cookie přidružený k požadovanému zámku zapisovače čtenářů  
  
 `pIterator`  
 mimo Ukazatel na iterátor, který může být předán metodám [GetRWLockOwnerNext –](iclrsyncmanager-getrwlockownernext-method.md) a [DeleteRWLockOwnerIterator –](iclrsyncmanager-deleterwlockowneriterator-method.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator`bylo voláno ve vlákně, které aktuálně používá spravovaný kód.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitelé obvykle volají `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` metody, a `GetRWLockOwnerNext` během zjišťování vzájemného zablokování. Hostitel zodpovídá za to, že zámek zapisovače proti čtečce je stále platný, protože CLR nepokusí zachovat zámek čtečky zapisovače čtenářů. K dispozici je několik strategií pro hostitele, aby se zajistila platnost zámku:  
  
- Hostitel může blokovat volání vydaných verzí na zámek zapisovače pro čtení (například [IHostSemaphore:: ReleaseSemaphore –](ihostsemaphore-releasesemaphore-method.md)) a přitom zajistit, že tento blok nezpůsobí zablokování.  
  
- Hostitel může zablokovat ukončení čekání na objekt události přidružený k zámku zapisovače pro čtení a znovu zajistit, aby tento blok nezpůsoboval zablokování.  
  
> [!NOTE]
> `CreateRWLockOwnerIterator`musí být volána pouze v vláknech, které aktuálně spouštějí nespravovaný kód.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
