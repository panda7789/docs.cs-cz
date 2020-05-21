---
title: ICLRSyncManager::DeleteRWLockOwnerIterator – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: a4094a64d27072ce257341398bb49419bef9b8bb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763147"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a>ICLRSyncManager::DeleteRWLockOwnerIterator – metoda
Požaduje, aby modul CLR (Common Language Runtime) zničil iterátor, který byl vytvořen voláním metody [ICLRSyncManager:: CreateRWLockOwnerIterator –](iclrsyncmanager-createrwlockowneriterator-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Iterator`  
 pro Iterátor, který byl vytvořen pomocí volání `CreateRWLockOwnerIterator` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`DeleteRWLockOwnerIterator`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu nebo je ve stavu, ve kterém nemůže spustit spravovaný kód, nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může zavolat tuto metodu a `CreateRWLockOwnerIterator` zajistit, aby její implementace vlákna zůstala synchronizovaná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
