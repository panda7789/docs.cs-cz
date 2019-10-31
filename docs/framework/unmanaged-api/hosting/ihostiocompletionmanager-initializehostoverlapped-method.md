---
title: IHostIoCompletionManager::InitializeHostOverlapped – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 9fd299ad25166bcbcf0202da13a5b4cbdd20d7d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133793"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped – metoda
Poskytuje hostiteli možnost inicializovat jakákoli vlastní data pro připojení ke struktuře Win32 `OVERLAPPED`, která se používá pro asynchronní vstupně-výstupní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pvOverlapped`  
 pro Ukazatel na strukturu `OVERLAPPED` Win32, která se má zahrnout do vstupně-výstupních požadavků.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|K přidělení požadovaného prostředku není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce platformy Windows používají strukturu `OVERLAPPED` k uložení stavu asynchronních vstupně-výstupních požadavků. CLR volá metodu `InitializeHostOverlapped`, aby hostitel mohl připojit vlastní data k instanci `OVERLAPPED`.  
  
> [!IMPORTANT]
> Chcete-li se dostat na začátek vlastního bloku dat, musí hostitelé nastavit posun na velikost `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).  
  
 Návratová hodnota E_OUTOFMEMORY značí, že hostitel nedokázal inicializovat vlastní data. V tomto případě CLR ohlásí chybu a volání se nezdařilo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
