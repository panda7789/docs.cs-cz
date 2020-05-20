---
title: ICLRIoCompletionManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: 822b51531b7afc1c824c74b9580d9208e347e13b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703562"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager – rozhraní
Implementuje metodu zpětného volání, která umožňuje hostiteli upozorňovat modul CLR (Common Language Runtime) na stav zadaných vstupně-výstupních požadavků.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnComplete – metoda](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|Upozorňuje CLR na stav vstupně-výstupní žádosti, která byla vytvořena pomocí volání metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel implementuje abstrakci dokončení vstupně-výstupních operací pomocí rozhraní [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) . CLR vytvoří v/v požadavky prostřednictvím tohoto rozhraní a hostitel upozorní modul runtime na výsledek takových požadavků pomocí `ICLRIoCompletionManager` rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostIoCompletionManager – rozhraní](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager – rozhraní](ihostthreadpoolmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
