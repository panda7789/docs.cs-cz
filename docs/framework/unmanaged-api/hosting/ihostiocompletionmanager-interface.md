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
ms.openlocfilehash: 095872f8d4bd4f7d3351b8b3e3f8f8445b615cd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501532"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) pracovat s porty dokončovacího vstupu a výstupu poskytovanými hostitelem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Bind – metoda](ihostiocompletionmanager-bind-method.md)|Váže popisovač k portu pro dokončení I/O.|  
|[CloseIoCompletionPort – metoda](ihostiocompletionmanager-closeiocompletionport-method.md)|Uzavře port, který byl vytvořen pomocí dřívějšího volání `CreateIoCompletionPort` .|  
|[CreateIoCompletionPort – metoda](ihostiocompletionmanager-createiocompletionport-method.md)|Požaduje, aby hostitel vytvořil nový port pro dokončení vstupu/výstupu.|  
|[GetAvailableThreads – metoda](ihostiocompletionmanager-getavailablethreads-method.md)|Získá počet vláken dokončení v/v, která aktuálně nezpracovávají požadavky.|  
|[GetHostOverlappedSize – metoda](ihostiocompletionmanager-gethostoverlappedsize-method.md)|Získá velikost libovolných vlastních dat, která hostitel chce připojit k vstupně-výstupním žádostem.|  
|[GetMaxThreads – metoda](ihostiocompletionmanager-getmaxthreads-method.md)|Získá maximální počet vláken, která může hostitel Allot na požadavky na vstupně-výstupní operace služby.|  
|[GetMinThreads – metoda](ihostiocompletionmanager-getminthreads-method.md)|Získá minimální počet vláken, která hostitel poskytuje pro vstupně-výstupní požadavky služby.|  
|[InitializeHostOverlapped – metoda](ihostiocompletionmanager-initializehostoverlapped-method.md)|Poskytuje hostiteli možnost inicializovat jakákoli vlastní data týkající se vstupně-výstupních požadavků.|  
|[SetCLRIoCompletionManager – metoda](ihostiocompletionmanager-setclriocompletionmanager-method.md)|Poskytuje hostitele s ukazatelem rozhraní na instanci [ICLRIoCompletionManager –](iclriocompletionmanager-interface.md) implementované modulem CLR.|  
|[SetMaxThreads – metoda](ihostiocompletionmanager-setmaxthreads-method.md)|Nastaví maximální počet vláken, která hostitel allots na požadavky na vstupně-výstupní operace služby.|  
|[SetMinThreads – metoda](ihostiocompletionmanager-setminthreads-method.md)|Nastaví minimální počet vláken, které by měl hostitel Allot na dokončení vstupu a výstupu.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostIoCompletionManager`odpovídá `ICLRIoCompletionManager` rozhraní implementovanému modulem CLR. CLR volá metody `IHostIoCompletionManager` pro vázání popisovačů k portům, které poskytuje hostitel, a Hostitel volá metody `ICLRIoCompletionManager` pro hlášení dokončení vstupně-výstupních požadavků.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](hosting-interfaces.md)
