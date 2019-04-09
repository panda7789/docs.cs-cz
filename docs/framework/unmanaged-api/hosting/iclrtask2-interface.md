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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172468"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 – rozhraní
Obsahuje všechny funkce, které jsou součástí [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní; navíc poskytuje metody, které umožňují zrušení vláken k zpozdit u aktuálního vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Nové vlákno zpoždění přerušit požadavky pro aktuální vlákno.|  
|[EndPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Umožňuje nové nebo čekající vlákno přerušení požadavky na vlákno za následek přerušení v aktuálním vláknu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRTask2` Dědí rozhraní `ICLRTask` rozhraní a přidá metody, které umožňují hostitele tak, aby zpoždění přerušení vlákna, k ochraně oblasti kódu, který nesmí nezdaří. Volání `BeginPreventAsyncAbort` zvýší čítač přerušení podprocesu zpoždění pro aktuální vlákno a volání `EndPreventAsyncAbort` sníží ho. Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` mohou být vnořené. Čítač je větší než nula, jsou zpožděné přerušení vlákna pro aktuální vlákno.  
  
 Pokud volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` jsou nespárováno, je možné dosáhnout stavu, ve které vlákno nelze doručit přeruší aktuální vlákno.  
  
 Prodleva není podporována pro vlákna je samotný přeruší.  
  
 Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM). Nesprávné použití těchto metod může způsobit neurčené chování ve virtuálním počítači. Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač by mohl nastavit na nulu, když virtuální počítač má dříve zvýší jeho. Podobně čítač interní nepovolenou přetečení. Pokud překročí limit integrální vzhledem k tomu, že je zvýšen o hostitele a virtuální počítač, výsledné chování není zadána.  
  
 Pro informace o členy zděděné z `ICLRTask` a o dalších použitích tohoto rozhraní, podívejte se [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
