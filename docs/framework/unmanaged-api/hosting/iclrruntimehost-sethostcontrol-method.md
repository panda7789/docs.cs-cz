---
title: ICLRRuntimeHost::SetHostControl – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 644b31ae8e8f0c51c08bcad57220a028406cfd3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504070"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl – metoda
Nastaví ukazatel rozhraní, který modul CLR (Common Language Runtime) může použít k získání implementace [rozhraní IHostControl](ihostcontrol-interface.md)hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pHostControl`  
 pro Ukazatel rozhraní na implementaci [rozhraní IHostControl](ihostcontrol-interface.md)hostitele.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetHostControl`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_CLR_ALREADY_STARTED|Modul CLR již byl inicializován.|  
  
## <a name="remarks"></a>Poznámky  
 Je nutné volat `SetHostControl` před inicializací modulu CLR, tedy před voláním [metody Start](iclrruntimehost-start-method.md) nebo použitím libovolného [rozhraní metadat](../metadata/metadata-interfaces.md). Doporučuje se volat `SetHostControl` hned po volání [funkce CorBindToCurrentRuntime –](corbindtocurrentruntime-function.md) nebo [funkce CorBindToRuntimeEx –](corbindtoruntimeex-function.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRRuntimeHost – rozhraní](iclrruntimehost-interface.md)
- [IHostControl – rozhraní](ihostcontrol-interface.md)
