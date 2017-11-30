---
title: "ICLRMetaHost::RequestRuntimeLoadedNotification – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32eb92263685bc3be9f0c28dea88ecfa78c2b52c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification – metoda
Poskytuje funkci zpětného volání, která záruku, která se má volat při společné jazykové verzi modulu runtime (CLR) je prvním načtení, ale ještě nebyla spuštěna. Tato metoda nahrazuje [lockclrversion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallbackFunction`  
 [v] Funkce zpětného volání, která je volána, když se načetl nový modul runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pCallbackFunction`má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Zpětné volání funguje následujícím způsobem:  
  
-   Zpětné volání je volána, pouze v případě, že je první načíst modul runtime.  
  
-   Zpětné volání není volána pro vícenásobné zátěže stejné modulu runtime.  
  
-   Pro modul runtime nejsou vícenásobně přístupné zátěže se serializují volání funkce zpětného volání.  
  
 Funkce zpětného volání má následující prototyp:  
  
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
  
 Pokud hostitel chtít načíst nebo způsobit jiný modul runtime načíst vícenásobné způsobem `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` parametry, které jsou k dispozici v zpětné volání funkce použije následujícím způsobem:  
  
-   `pfnCallbackThreadSet`musí být voláno vlákno, které může způsobit runtime zatížení předtím, než dojde k pokusu o takové zatížení.  
  
-   `pfnCallbackThreadUnset`musí být volána, když vlákno už způsobí zatížení runtime (a před návratem od počáteční zpětné volání).  
  
-   `pfnCallbackThreadSet`a `pfnCallbackThreadUnset` jsou obě nejsou vícenásobně přístupné.  
  
> [!NOTE]
>  Hostování aplikací nesmějí provádět volání `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` mimo obor `pCallbackFunction` parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrmetahost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
