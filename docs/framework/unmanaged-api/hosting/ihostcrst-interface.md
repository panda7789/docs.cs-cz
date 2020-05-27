---
title: IHostCrst – rozhraní
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804905"
---
# <a name="ihostcrst-interface"></a>IHostCrst – rozhraní
Slouží jako reprezentace kritické části pro vlákno.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Enter – metoda](ihostcrst-enter-method.md)|Vstupuje do kritické části.|  
|[Leave – metoda](ihostcrst-leave-method.md)|Ponechá oddíl kritické.|  
|[SetSpinCount – metoda](ihostcrst-setspincount-method.md)|Nastaví počet číselníků pro kritickou část.|  
|[TryEnter – metoda](ihostcrst-tryenter-method.md)|Pokusí se zadat kritickou část a okamžitě nahlásit úspěšnost nebo selhání.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostCrst`umožňuje modulu CLR (Common Language Runtime) komunikovat přímo s reprezentací hostitele kritické sekce místo použití funkcí Win32, jako je například `EnterCriticalSection` nebo `LeaveCriticalSection` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
