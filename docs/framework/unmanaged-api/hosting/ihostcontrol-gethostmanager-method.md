---
title: IHostControl::GetHostManager – metoda
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: 25e931ec17cad3508d548fb4ca7e53b0ade3f119
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804958"
---
# <a name="ihostcontrolgethostmanager-method"></a>IHostControl::GetHostManager – metoda
Získá ukazatel rozhraní na implementaci rozhraní se zadaným hostitelem `IID` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 pro `IID`Rozhraní, pro které se modul CLR (Common Language Runtime) dotazuje na.  
  
 `ppObject`  
 mimo Ukazatel na rozhraní implementovaného hostitelem nebo hodnotu null, pokud hostitel toto rozhraní nepodporuje.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetHostManager`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Požadovaná `IID` není platná.|  
|E_NOINTERFACE|Požadované rozhraní není podporováno.|  
  
## <a name="remarks"></a>Poznámky  
 CLR dotazuje hostitele, aby zjistil, zda podporuje jedno nebo více následujících rozhraní:  
  
- [IHostMemoryManager](ihostmemorymanager-interface.md)  
  
- [IHostTaskManager](ihosttaskmanager-interface.md)  
  
- [IHostThreadPoolManager](ihostthreadpoolmanager-interface.md)  
  
- [IHostIoCompletionManager](ihostiocompletionmanager-interface.md)  
  
- [IHostSyncManager](ihostsyncmanager-interface.md)  
  
- [IHostAssemblyManager](ihostassemblymanager-interface.md)  
  
- [IHostGCManager](ihostgcmanager-interface.md)  
  
- [IHostPolicyManager](ihostpolicymanager-interface.md)  
  
- [IHostSecurityManager](ihostsecuritymanager-interface.md)  
  
 Pokud hostitel podporuje zadané rozhraní, nastaví `ppObject` implementaci tohoto rozhraní. V opačném případě se nastaví `ppObject` na hodnotu null.  
  
 Modul CLR nevolá `Release` správce hostitelů ani po jeho vypnutí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostControl – rozhraní](ihostcontrol-interface.md)
