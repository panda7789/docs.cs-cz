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
ms.openlocfilehash: b067ca72e030bce24a7efde5e3488a00024e9613
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762864"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 – rozhraní
Poskytuje všechny funkce rozhraní [ICLRTask](iclrtask-interface.md) ; Kromě toho poskytuje metody, které umožňují, aby bylo přerušení vlákna zpožděno v aktuálním vlákně.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginPreventAsyncAbort – metoda](iclrtask2-beginpreventasyncabort-method.md)|Zpozdí žádosti o přerušení nového vlákna v aktuálním vlákně.|  
|[EndPreventAsyncAbort – metoda](iclrtask2-endpreventasyncabort-method.md)|Umožňuje, aby nové nebo probíhající požadavky na přerušení vlákna byly výsledkem přerušení vlákna v aktuálním vlákně.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRTask2`Rozhraní dědí `ICLRTask` rozhraní a přidává metody, které umožní hostiteli zpozdit přerušení vlákna, aby chránila oblast kódu, která nesmí selhat. Volání `BeginPreventAsyncAbort` zvýší čítač zpožděného vlákna na přerušení pro aktuální vlákno a zavoláním `EndPreventAsyncAbort` ho sníží. Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` můžou být vnořená. Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.  
  
 Pokud volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` nejsou spárována, je možné spojit se stavem, ve kterém nelze podprocesy přerušit, nelze doručit do aktuálního vlákna.  
  
 Zpoždění se nerespektuje pro vlákno, které se přerušuje.  
  
 Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM). Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače. Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil. Podobně není u vnitřního čítače přetečení kontrolováno. Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.  
  
 Informace o členech zděděných z `ICLRTask` a o ostatních použití tohoto rozhraní naleznete v rozhraní [ICLRTask](iclrtask-interface.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
