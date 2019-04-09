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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c3bebe8eabd4d5fd5faec21e0b0efc408353bc2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197266"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager – rozhraní
Poskytuje metody, které umožňují common language runtime (CLR) pro interakci s poskytované hostitelem portů dokončení vstupně-výstupních operací.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Bind – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Vytvoří vazbu popisovač na port dokončení vstupně-výstupních operací.|  
|[CloseIoCompletionPort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Zavře port, který byl vytvořen pomocí dřívějším volání `CreateIoCompletionPort`.|  
|[CreateIoCompletionPort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Požadavky, že hostitele, vytvořte nový port dokončení vstupně-výstupních operací.|  
|[GetAvailableThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Získá počet podprocesů dokončení vstupně-výstupních operací, které nejsou aktuálně zpracování požadavků.|  
|[GetHostOverlappedSize – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Získá velikost vlastní data, která si klade za cíl hostitele pro připojení k vstupně-výstupní požadavky.|  
|[GetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Získá maximální počet vláken, která může přidělit hostitele služby vstupně-výstupní požadavky.|  
|[GetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Získá minimální počet vláken, která obsahuje hostitele služby vstupně-výstupní požadavky.|  
|[InitializeHostOverlapped – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Poskytuje hostitele příležitost k inicializaci vlastních dat o požadavek na vstupně-výstupních operací.|  
|[SetCLRIoCompletionManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Poskytuje ukazatel rozhraní k hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementován modulem CLR.|  
|[SetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Nastaví maximální počet vláken, která allots hostitele služby vstupně-výstupní požadavky.|  
|[SetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Nastaví minimální počet vláken, která by měla přidělit hostitele na dokončení vstupně-výstupních operací.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostIoCompletionManager` odpovídá `ICLRIoCompletionManager` rozhraní implementované CLR. CLR volá metody dané `IHostIoCompletionManager` zpracovává vytvořit vazbu na porty, které obsahuje hostitele a hostitele volá metody dané `ICLRIoCompletionManager` Oznámit dokončení vstupně-výstupní požadavky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
