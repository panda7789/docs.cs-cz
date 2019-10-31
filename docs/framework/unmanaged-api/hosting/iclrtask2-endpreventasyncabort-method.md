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
ms.openlocfilehash: 8ae66e0bf96138e5bc2f33e4c14ad86e7dabc6b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124555"
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
  
 Volání [ICLRTask2:: BeginPreventAsyncAbort –](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) a `EndPreventAsyncAbort` můžou být vnořená. Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.  
  
 Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM). Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače. Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil. Podobně není u vnitřního čítače přetečení kontrolováno. Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [BeginPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
