---
title: IHostMemoryManager::GetMemoryLoad – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 2210dcd9e8a8af92b7905ec680c53c1119e6a3cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136709"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad – metoda
Získá velikost fyzické paměti, která je právě používána, a proto není k dispozici, jak je uvedeno v hostiteli.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pMemoryLoad`  
 mimo Ukazatel na přibližnou procentuální hodnotu celkové fyzické paměti, která se právě používá.  
  
 `pAvailableBytes`  
 mimo Ukazatel na počet bajtů dostupných pro modul CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `GetMemoryLoad` zabalí funkci Win32 `GlobalMemoryStatus`. Hodnota `pMemoryLoad` je ekvivalentem pole `dwMemoryLoad` ve struktuře `MEMORYSTATUS` vrácených z `GlobalMemoryStatus`.  
  
 Modul runtime používá návratovou hodnotu jako heuristickou pro uvolňování paměti. Například pokud hostitel hlásí, že je většina paměti používána, systém uvolňování paměti se může rozhodnout shromáždit z více generací a zvýšit tak množství paměti, které může být k dispozici.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
