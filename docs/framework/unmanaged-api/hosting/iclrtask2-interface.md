---
title: ICLRTask2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124528"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 – rozhraní
Poskytuje všechny funkce rozhraní [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ; Kromě toho poskytuje metody, které umožňují, aby bylo přerušení vlákna zpožděno v aktuálním vlákně.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Zpozdí žádosti o přerušení nového vlákna v aktuálním vlákně.|  
|[EndPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Umožňuje, aby nové nebo probíhající požadavky na přerušení vlákna byly výsledkem přerušení vlákna v aktuálním vlákně.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICLRTask2` dědí `ICLRTask` rozhraní a přidává metody, které umožní hostiteli zpozdit přerušení vlákna, aby chránila oblast kódu, která nesmí selhat. Volání `BeginPreventAsyncAbort` zvýší čítač zpožděného vlákna na přerušení pro aktuální vlákno a volání `EndPreventAsyncAbort` sníží. Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` mohou být vnořena. Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.  
  
 Pokud nejsou volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` spárována, je možné spojit se stavem, ve kterém je přerušeno přerušení vlákna nelze doručit do aktuálního vlákna.  
  
 Zpoždění se nerespektuje pro vlákno, které se přerušuje.  
  
 Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM). Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače. Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil. Podobně není u vnitřního čítače přetečení kontrolováno. Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.  
  
 Informace o členech zděděných z `ICLRTask` a o ostatních použití tohoto rozhraní naleznete v tématu rozhraní [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
