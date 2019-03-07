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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18a2156b87fb4bf72e8de7c32c7e20d2a017c900
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479267"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification – metoda
Poskytuje funkce zpětného volání, která je zaručeně volán při společné jazykové verzi modulu runtime (CLR) je prvním načtení, ale ještě nebyl spuštěn. Tato metoda nahrazuje [lockclrversion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallbackFunction`  
 [in] Funkce zpětného volání, která se vyvolá po načtení nového modulu runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pCallbackFunction` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Zpětné volání pracuje následujícím způsobem:  
  
-   Zpětné volání je vyvolat pouze při prvním načtení modulu runtime.  
  
-   Zpětné volání není vyvolána vícenásobné načtení stejných modulů runtime.  
  
-   Pro načtení modulu runtime bez reentrant serializují volání funkce zpětného volání.  
  
 Funkce zpětného volání obsahuje následující prototyp:  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Prototypy funkcí zpětného volání jsou následující:  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Pokud si klade za cíl hostitele k načtení nebo způsobí jiný modul runtime načtení vícenásobné způsobem, `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` parametry, které jsou k dispozici při zpětném volání funkce musí použít následujícím způsobem:  
  
-   `pfnCallbackThreadSet` musí být volána vláknem, které může způsobit, že modul runtime zatížení předtím, než dojde k pokusu o takové zatížení.  
  
-   `pfnCallbackThreadUnset` musí být volána, když vlákno již způsobí, že modul runtime zatížení (a před návratem z počáteční zpětné volání).  
  
-   `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` jsou mimo reentrant.  
  
> [!NOTE]
>  Hostování aplikací nesmějí volat `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` mimo obor `pCallbackFunction` parametru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
