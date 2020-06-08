---
title: IHostSecurityManager::SetSecurityContext – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: 6a6b4d0351e22026dc873aad8281d0259d871a14
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501479"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a>IHostSecurityManager::SetSecurityContext – metoda
Nastaví kontext zabezpečení aktuálně zpracovávaného vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `eContextType`  
 pro Jedna z hodnot [EContextType –](econtexttype-enumeration.md) , která označuje typ kontextu, který modul CLR (Common Language Runtime) umísťuje na hostitele.  
  
 `ppSecurityContext`  
 mimo Ukazatel na adresu nového objektu [IHostSecurityContext –](ihostsecuritycontext-interface.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetSecurityContext`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá `SetSecurityContext` v několika scénářích. Před tím, než se spustí třídy a konstruktory modulu a finalizační metody, vyvolá volání CLR `SetSecurityContext` k ochraně hostitele před selháním spuštění. Poté obnoví kontext zabezpečení do původního stavu po provedení konstruktoru nebo finalizační metody pomocí jiného volání metody `SetSecurityContext` . Podobný vzor se děje I v/v dokončování. Pokud hostitel implementuje [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), VYVOLÁ volání CLR `SetSecurityContext` po volání [ICLRIoCompletionManager –::-Complete](iclriocompletionmanager-oncomplete-method.md).  
  
 V asynchronních bodech v pracovních vláknech volání CLR v rámci `SetSecurityContext` <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), v závislosti na tom, zda hostitel nebo modul CLR implementuje fond vláken.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [EContextType – výčet](econtexttype-enumeration.md)
- [ICLRIoCompletionManager – rozhraní](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager – rozhraní](ihostiocompletionmanager-interface.md)
- [IHostSecurityContext – rozhraní](ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager – rozhraní](ihostthreadpoolmanager-interface.md)
