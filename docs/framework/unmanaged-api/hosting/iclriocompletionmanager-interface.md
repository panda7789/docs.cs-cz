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
ms.openlocfilehash: 71afc5e9772f82b922e8f428e6d808e46d092704
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504209"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager – rozhraní
Implementuje metodu zpětného volání, která umožňuje hostiteli upozorňovat modul CLR (Common Language Runtime) na stav zadaných vstupně-výstupních požadavků.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[OnComplete – metoda](iclriocompletionmanager-oncomplete-method.md)|Upozorňuje CLR na stav vstupně-výstupní žádosti, která byla vytvořena pomocí volání metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel implementuje abstrakci dokončení vstupně-výstupních operací pomocí rozhraní [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) . CLR vytvoří v/v požadavky prostřednictvím tohoto rozhraní a hostitel upozorní modul runtime na výsledek takových požadavků pomocí `ICLRIoCompletionManager` rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostIoCompletionManager – rozhraní](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager – rozhraní](ihostthreadpoolmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
