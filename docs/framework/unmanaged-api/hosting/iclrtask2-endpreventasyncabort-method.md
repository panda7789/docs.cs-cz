---
title: ICLRTask2::EndPreventAsyncAbort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 3ea36c56ef9ccf5886ba96191627e5283da186f7
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762849"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort – metoda
Umožňuje, aby nové nebo probíhající požadavky na přerušení vlákna byly výsledkem přerušení vlákna v aktuálním vlákně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|HOST_E_INVALIDOPERATION|Metoda byla volána pro vlákno, které není aktuálním vláknem.|  
  
## <a name="remarks"></a>Poznámky  
 Voláním této metody dojde k snížení čítače zpoždění-vlákno-přerušení pro aktuální vlákno o jednu.  
  
 Volání [ICLRTask2:: BeginPreventAsyncAbort –](iclrtask2-beginpreventasyncabort-method.md) a `EndPreventAsyncAbort` mohou být vnořena. Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.  
  
 Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM). Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače. Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil. Podobně není u vnitřního čítače přetečení kontrolováno. Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [BeginPreventAsyncAbort – metoda](iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2 – rozhraní](iclrtask2-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
