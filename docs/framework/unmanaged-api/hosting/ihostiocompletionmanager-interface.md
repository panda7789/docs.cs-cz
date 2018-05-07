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
ms.openlocfilehash: 194dcec6ea484e9cd2d3a17093c1eceb16c8f6c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager – rozhraní
Poskytuje metody, které povolit modul CLR (CLR) pro interakci s porty dokončení vstupně-výstupních operací od hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Bind – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Vytvoří vazbu k portu dokončení vstupně-výstupních operací popisovač.|  
|[CloseIoCompletionPort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Zavření portů, která byla vytvořena pomocí dřívější volání `CreateIoCompletionPort`.|  
|[CreateIoCompletionPort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Počet požadavků, hostitele vytvořit nový port dokončení vstupně-výstupní operace.|  
|[GetAvailableThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Získá počet vláken dokončení vstupně-výstupních operací, které nejsou aktuálně zpracování požadavků.|  
|[GetHostOverlappedSize – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Získá velikost vlastní data, která hostitele chtít připojit k vstupně-výstupní požadavky.|  
|[GetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Získá maximální počet vláken, které můžete přidělit hostitele se žádostí o službu vstupně-výstupní operace.|  
|[GetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Získá minimální počet vláken, která poskytuje hostitele se žádostí o službu vstupně-výstupní operace.|  
|[InitializeHostOverlapped – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Poskytuje hostitele příležitost k inicializaci vlastních dat o požadavek vstupně-výstupní operace.|  
|[SetCLRIoCompletionManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Poskytuje ukazatele rozhraní na hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementované modulu CLR.|  
|[SetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Nastaví maximální počet vláken, která allots hostitele se žádostí o službu vstupně-výstupní operace.|  
|[SetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Nastaví minimální počet vláken, která by měla přidělit hostitele na dokončení vstupně-výstupní operace.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostIoCompletionManager` odpovídá `ICLRIoCompletionManager` rozhraní implementované modulu CLR. CLR volá metody `IHostIoCompletionManager` k vytvoření vazby popisovače porty, které poskytuje hostitele a hostitele volá metody `ICLRIoCompletionManager` nahlásit dokončení vstupně-výstupní požadavky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
