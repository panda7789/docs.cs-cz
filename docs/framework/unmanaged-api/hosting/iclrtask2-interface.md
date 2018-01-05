---
title: "ICLRTask2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2
helpviewer_keywords: ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8701cff3400e46660fac90486cf5648d29aa9972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2-interface"></a>ICLRTask2 – rozhraní
Obsahuje všechny funkce [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní; kromě toho poskytuje metody, které umožňují zrušení vláken na opožděno na aktuální vlákno.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Zpoždění nové vlákno abort požadavky na aktuální vlákno.|  
|[EndPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Umožňuje nové nebo nevyřízené žádosti o zrušení vláken za následek vlákno zruší na aktuální vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRTask2` Dědí rozhraní `ICLRTask` rozhraní a přidá metody, které umožňují hostitele do zpoždění přerušení způsobených vlákno k ochraně oblasti kód, který nesmí nezdaří. Volání metody `BeginPreventAsyncAbort` zvýší čítač přerušení podprocesu zpoždění pro aktuální vlákno a volání `EndPreventAsyncAbort` snižuje ho. Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` mohou být použity. Tak dlouho, dokud hodnota čítače je větší než nula, jsou odložené přerušení přístup z více vláken pro aktuální vlákno.  
  
 Pokud volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` není spárovat, je možné dosáhnout stavu, ve které vlákno přerušení nelze doručit do aktuální vlákno.  
  
 Zpoždění není dodržení pro vlákno, které zruší sám sebe.  
  
 Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM). Zneužití z těchto metod může způsobit neurčené chování ve virtuálním počítači. Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač může nastavit na hodnotu nula, pokud virtuální počítač má dříve se zvýší. Podobně není čítač interní kontrola přetečení. Pokud překročí limitu integrální vzhledem k tomu, že se zvýší o hostitel a virtuální počítač, neurčené jejich výsledné chování.  
  
 Pro informace o členech zděděno z `ICLRTask` a o dalších použití tohoto rozhraní, najdete v článku [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
