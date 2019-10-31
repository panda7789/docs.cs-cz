---
title: IHostIoCompletionManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133850"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) pracovat s porty dokončovacího vstupu a výstupu poskytovanými hostitelem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Bind – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Váže popisovač k portu pro dokončení I/O.|  
|[CloseIoCompletionPort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Uzavře port, který byl vytvořen pomocí předchozího volání `CreateIoCompletionPort`.|  
|[CreateIoCompletionPort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Požaduje, aby hostitel vytvořil nový port pro dokončení vstupu/výstupu.|  
|[GetAvailableThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Získá počet vláken dokončení v/v, která aktuálně nezpracovávají požadavky.|  
|[GetHostOverlappedSize – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Získá velikost libovolných vlastních dat, která hostitel chce připojit k vstupně-výstupním žádostem.|  
|[GetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Získá maximální počet vláken, která může hostitel Allot na požadavky na vstupně-výstupní operace služby.|  
|[GetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Získá minimální počet vláken, která hostitel poskytuje pro vstupně-výstupní požadavky služby.|  
|[InitializeHostOverlapped – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Poskytuje hostiteli možnost inicializovat jakákoli vlastní data týkající se vstupně-výstupních požadavků.|  
|[SetCLRIoCompletionManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Poskytuje hostitele s ukazatelem rozhraní na instanci [ICLRIoCompletionManager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) implementované modulem CLR.|  
|[SetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Nastaví maximální počet vláken, která hostitel allots na požadavky na vstupně-výstupní operace služby.|  
|[SetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Nastaví minimální počet vláken, které by měl hostitel Allot na dokončení vstupu a výstupu.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostIoCompletionManager` odpovídá rozhraní `ICLRIoCompletionManager` implementovanému modulem CLR. CLR volá metody `IHostIoCompletionManager` pro vázání popisovačů k portům, které poskytuje hostitel, a Hostitel volá metody `ICLRIoCompletionManager` k hlášení dokončení vstupně-výstupních požadavků.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
