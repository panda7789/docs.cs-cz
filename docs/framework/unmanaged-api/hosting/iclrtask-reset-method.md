---
title: "ICLRTask::Reset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8dc37f47fc01d73ff499ef974a2e11345a95286a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset – metoda
Modul CLR (CLR) informuje, že byla dokončena úloha hostitele a umožňuje CLR znovu použít aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představují jiná úloha.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fFull`  
 [v] `true`, pokud by se modul runtime obnovit všechny statické hodnoty související s vlákno plody kromě a informace o zabezpečení a národního prostředí aktuálního `ICLRTask` instanci, jinak hodnota `false`.  
  
 Pokud je hodnota `true`, modul runtime obnoví data, která byla uložená pomocí <xref:System.Threading.Thread.AllocateDataSlot%2A> nebo <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Reset`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže spustit spravovaného kódu nebo zpracovat volání. úspěšně|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR provést recyklaci vytvořili `ICLRTask` instancí, aby se zabránilo režii opakovaně vytváření nových instancí pokaždé, když potřebuje novou úlohu. Hostitele povolí tuto funkci voláním `ICLRTask::Reset` místo [iclrtask::exittask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po jeho dokončení úlohy. Následující seznam shrnuje normální životní cyklus `ICLRTask` instance:  
  
1.  Vytvoří nový modul runtime `ICLRTask` instance.  
  
2.  Volání modulu runtime [ihosttaskmanager::getcurrenttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) získat odkaz na aktuální úlohy hostitele.  
  
3.  Volání modulu runtime [ihosttask::setclrtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) přidružit nové instance hostitele úloh.  
  
4.  Úloha se spustí a dokončení.  
  
5.  Hostitel zničí úlohy voláním `ICLRTask::ExitTask`.  
  
 `Reset`mění tento scénář dvěma způsoby. V kroku 5 výše, volání hostitele `Reset` resetovat úlohu do čistého stavu a potom odpojí `ICLRTask` instance z jeho přidružených [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance. V případě potřeby můžete také mezipaměti hostitele `IHostTask` instance pro opakované použití. V kroku 1 výše, modul runtime vrátí recykluje `ICLRTask` z mezipaměti místo vytvoření nové instance.  
  
 Tento postup funguje dobře, pokud hostitel má také fond znovu použitelné pracovní úkoly. Když hostitel zničí jeden z jeho `IHostTask` instancí ho zničí odpovídající `ICLRTask` voláním `ExitTask`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
