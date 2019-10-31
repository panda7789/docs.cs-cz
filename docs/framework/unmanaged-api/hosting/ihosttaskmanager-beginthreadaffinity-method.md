---
title: IHostTaskManager::BeginThreadAffinity – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 7c157cf27d2fe86288024a6c35e6dcbea3c46347
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133107"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a>IHostTaskManager::BeginThreadAffinity – metoda
Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém se aktuální úloha nesmí přesunout do jiného vlákna operačního systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`BeginThreadAffinity` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 CLR obvykle volá `IHostTaskManager::BeginThreadAffinity` v kontextu volání <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>. Aktuální úlohu nesmí být přeplánována, dokud nebude provedeno odpovídající volání [IHostTaskManager:: EndThreadAffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md). Úlohy je možné přepnout, ale pokud jsou znovu přepnuty, musí být přiřazeny ke stejnému vláknu operačního systému, ze kterého byly přepnuty. Vnořené volání `BeginThreadAffinity` nemají žádný účinek, protože volání odkazuje na aktuální úlohu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
