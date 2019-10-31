---
title: ICLRMetaHost::RequestRuntimeLoadedNotification – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
ms.openlocfilehash: 23f868bba2dc058d99f1c5c09e9b311b1ff3634a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140901"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification – metoda
Poskytuje funkci zpětného volání, která je zaručena k volání při prvním načtení verze modulu CLR (Common Language Runtime), ale ještě nebyla spuštěna. Tato metoda nahrazuje funkci [LockClrVersion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallbackFunction`  
 pro Funkce zpětného volání, která je vyvolána, když byl načten nový modul runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pCallbackFunction` je null.|  
  
## <a name="remarks"></a>Poznámky  
 Zpětné volání funguje následujícím způsobem:  
  
- Zpětné volání je vyvoláno pouze při prvním načtení modulu runtime.  
  
- Zpětné volání není vyvoláno pro znovu vstupující načtení stejného modulu runtime.  
  
- Pro neopětovné zařazení za běhu jsou volání funkce zpětného volání serializována.  
  
 Funkce zpětného volání má následující prototyp:  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Prototypy funkce zpětného volání jsou následující:  
  
- `pfnCallbackThreadSet`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Pokud hostitel zamýšlí načíst nebo způsobí, že jiný modul runtime bude načten znovu, je nutné použít parametry `pfnCallbackThreadSet` a `pfnCallbackThreadUnset`, které jsou k dispozici ve funkci zpětného volání následujícím způsobem:  
  
- `pfnCallbackThreadSet` musí být voláno vláknem, které může způsobit zatížení za běhu před tím, než se provede pokus o načtení.  
  
- `pfnCallbackThreadUnset` musí být volána, pokud vlákno již nebude způsobovat takové načtení za běhu (a před návratem z prvotního zpětného volání).  
  
- `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` se nepoužívají.  
  
> [!NOTE]
> Hostitelské aplikace nesmí volat `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` mimo obor parametru `pCallbackFunction`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
