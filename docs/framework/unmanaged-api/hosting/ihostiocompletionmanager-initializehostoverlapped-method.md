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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 023e112aa8273d99efce2e0f2116f95569ac0c3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped – metoda
Poskytuje hostitele příležitost k inicializaci vlastní dat připojit k Win32 `OVERLAPPED` struktura, která se používá pro asynchronní vstupně-výstupní požadavky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvOverlapped`  
 [v] Ukazatel na Win32 `OVERLAPPED` struktura bude zahrnuta v žádosti o vstupně-výstupní operace.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti nebylo k dispozici pro přidělení požadovaný prostředek.|  
  
## <a name="remarks"></a>Poznámky  
 Použití funkce na platformu Windows `OVERLAPPED` struktura k uložení stavu pro asynchronní vstupně-výstupní požadavky. Volání CLR `InitializeHostOverlapped` metoda poskytnout možnost připojit vlastní data pro hostitele `OVERLAPPED` instance.  
  
> [!IMPORTANT]
>  Abyste se dostali na začátku bloku svá vlastní data, hostitelé musí nastavit posun na velikost `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).  
  
 Vrácená hodnota E_OUTOFMEMORY označuje, že hostitele se nepodařilo inicializovat svá vlastní data. V takovém případě modulu CLR nahlásí chybu a selže volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [GetHostOverlappedSize – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [IHostIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
