---
title: ICLRIoCompletionManager::OnComplete – metoda
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: 39c9752912e88b04455516c0e9bed43610ba8aa0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703823"
---
# <a name="iclriocompletionmanageroncomplete-method"></a>ICLRIoCompletionManager::OnComplete – metoda
Upozorňuje modul CLR (Common Language Runtime) na stav vstupně-výstupních požadavků, který byl proveden pomocí volání metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 pro Hodnota HRESULT, která indikuje stav operace vazby.  
  
- S_OK označuje, že operace byla úspěšně dokončena.  
  
- HOST_E_INTERRUPTED označuje, že volání bylo ukončeno před dokončením.  
  
- E_FAIL označuje, že došlo k neznámé, neobnovitelné, závažné chybě.  
  
 `NumberOfBytesTransferred`  
 pro Počet bajtů přenesených během zpracování vstupně-výstupních požadavků.  
  
 `pvOverlapped`  
 pro Ukazatel na `OVERLAPPED` strukturu, která byla předána volání `IHostIoCompletionManager::Bind` metody.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OnComplete`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud hostitel implementuje abstrakci dokončení vstupně-výstupních operací, CLR vytvoří požadavky na vstupně-výstupní operace prostřednictvím hostitele pomocí metod [IHostIoCompletionManager](ihostiocompletionmanager-interface.md). Hostitel pak zavolá `OnComplete` metodu, která upozorní modul runtime na výsledek takových požadavků.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRIoCompletionManager – rozhraní](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager – rozhraní](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager – rozhraní](ihostthreadpoolmanager-interface.md)
