---
title: ICLRTask2::BeginPreventAsyncAbort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1b5c0f5636748b96cc7d9667155581f1595a4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort – metoda
Zpoždění nové vlákno přerušení požadavky od vést k přerušení přístup z více vláken na aktuální vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|HOST_E_INVALIDOPERATION|Volání metody na vlákno, která není aktuální vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 Voláním této metody zvýší čítač přerušení podprocesu zpoždění pro aktuální vlákno o jednu.  
  
 Volání `BeginPreventAsyncAbort` a [iclrtask2::endpreventasyncabort –](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) mohou být použity. Tak dlouho, dokud hodnota čítače je větší než nula, jsou odložené přerušení přístup z více vláken pro aktuální vlákno. Pokud toto volání není spárovaný s volání `EndPreventAsyncAbort` metoda, je možné dosáhnout stavu, ve které vlákno přerušení nelze doručit do aktuální vlákno.  
  
 Zpoždění není dodržení pro vlákno, které zruší sám sebe.  
  
 Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM). Zneužití z těchto metod může způsobit neurčené chování ve virtuálním počítači. Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač může nastavit na hodnotu nula, pokud virtuální počítač má dříve se zvýší. Podobně není čítač interní kontrola přetečení. Pokud překročí limitu integrální vzhledem k tomu, že se zvýší o hostitel a virtuální počítač, neurčené jejich výsledné chování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EndPreventAsyncAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [ICLRTask2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
