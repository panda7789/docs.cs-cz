---
title: ICLRPolicyManager::SetActionOnFailure – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 143052febe136e969987c35bc06f6c3b3356aedf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140778"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure – metoda
Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu zadaného selhání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `failure`  
 pro Jedna z hodnot [EClrFailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) , která označuje typ selhání, u kterého se má provést akce.  
  
 `action`  
 pro Jedna z hodnot [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) označující akci, která se má provést, když dojde k selhání. Seznam podporovaných hodnot naleznete v části poznámky.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Pro zadanou operaci nelze nastavit akci zásad, nebo byla pro tuto operaci zadána neplatná akce zásad.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení vyvolá CLR výjimku, když se nepovede přidělit prostředek, jako je například paměť. `SetActionOnFailure` umožňuje hostiteli přepsat toto chování zadáním akce zásady, která se má provést při selhání. V následující tabulce jsou uvedeny kombinace hodnot [EClrFailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) a [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , které jsou podporovány. (Předpona FAIL_ se vynechává z hodnot [EClrFailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) .)  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||Není k dispozici||  
|eThrowException|X|X||||Není k dispozici||  
|`eAbortThread`|X|X||||Není k dispozici|X|  
|`eRudeAbortThread`|X|X||||Není k dispozici|X|  
|`eUnloadAppDomain`|X|X||X||Není k dispozici|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|Není k dispozici|X|  
|`eExitProcess`|X|X||X|X|Není k dispozici|X|  
|eFastExitProcess|X|X||X|X|Není k dispozici||  
|`eRudeExitProcess`|X|X|X|X|X|Není k dispozici||  
|`eDisableRuntime`|X|X|X|X|X|Není k dispozici||  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
