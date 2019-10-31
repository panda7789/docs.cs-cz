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
ms.openlocfilehash: 676a1d50202333203c13fcf916dbb14a6d91fb8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121448"
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
 pro Jedna z hodnot [EContextType –](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) , která označuje typ kontextu, který modul CLR (Common Language Runtime) umísťuje na hostitele.  
  
 `ppSecurityContext`  
 mimo Ukazatel na adresu nového objektu [IHostSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetSecurityContext` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá `SetSecurityContext` v několika scénářích. Před tím, než se spustí třídy a konstruktory modulu a finalizační metody, vyvolá CLR `SetSecurityContext` k ochraně hostitele před selháním spuštění. Poté obnoví kontext zabezpečení do původního stavu po provedení konstruktoru nebo finalizační metody pomocí jiného volání `SetSecurityContext`. Podobný vzor se děje I v/v dokončování. Pokud hostitel implementuje [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), CLR volá `SetSecurityContext` po volání [ICLRIoCompletionManager –::-Complete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).  
  
 V asynchronních bodech v pracovních vláknech volá CLR `SetSecurityContext` v rámci <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> nebo uvnitř [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), podle toho, zda hostitel nebo modul CLR implementuje fond vláken.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [EContextType – výčet](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [ICLRIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
