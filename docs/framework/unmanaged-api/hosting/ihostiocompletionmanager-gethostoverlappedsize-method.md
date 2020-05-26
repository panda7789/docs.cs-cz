---
title: IHostIoCompletionManager::GetHostOverlappedSize – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: a97009a4ebc834d867dddcc350033c550364ea42
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804747"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize – metoda
Získá velikost libovolných vlastních dat, která hostitel chce připojit k vstupně-výstupním žádostem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcbSize`  
 mimo Ukazatel na počet bajtů, které by měl přidělovat modul CLR (Common Language Runtime) Kromě velikosti `OVERLAPPED` objektu Win32.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Všechna asynchronní vstupně-výstupní volání rozhraní API platformy Windows přebírají `OVERLAPPED` objekt Win32, který poskytuje informace, jako je například pozice ukazatele souboru. Aby bylo možné zachovat stav, aplikace, které provádí asynchronní vstupně-výstupní volání, obvykle do struktury přidávají vlastní data. `GetHostOverlappedSize`a [IHostIoCompletionManager:: InitializeHostOverlapped –](ihostiocompletionmanager-initializehostoverlapped-method.md) poskytují příležitost k tomu, aby hostitel zahrnoval taková vlastní data.  
  
 CLR volá `GetHostOverlappedSize` metodu pro určení velikosti vlastních dat, která hostitel chce připojit k `OVERLAPPED` objektu.  
  
> [!NOTE]
> `GetHostOverlappedSize`se volá jenom jednou. Vlastní data hostitele musí mít stejnou velikost pro každou vstupně-výstupní žádost.  
  
> [!IMPORTANT]
> Velikost `OVERLAPPED` samotného objektu není obsažena v hodnotě `pcbSize` .  
  
 Další informace o `OVERLAPPED` struktuře najdete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager – rozhraní](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager – rozhraní](ihostiocompletionmanager-interface.md)
