---
title: ICLRGCManager2::SetGCStartupLimitsEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65fbf0bf42f7312ad80b61bf452b62a4d0ff93c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a>ICLRGCManager2::SetGCStartupLimitsEx – metoda
Nastaví velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `SegmentSize`  
 [v] Zadaná velikost paměti segment kolekce.  
  
 Velikost minimální segmentu je 4 MB volného místa. Segmenty může být vyšší v přírůstcích po 1 MB nebo větší.  
  
 `MaxGen0Size`  
 [v] Zadaná maximální velikost pro generování 0.  
  
 Velikost minimální generace 0 je 64 KB.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimitsEx` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty, `SetGCStartupLimitsEx` sady lze zadat pouze, před zahájením hostitele. Novější volá, aby se `SetGCStartupLimitsEx` jsou ignorovány.  
  
 Nastavit buď parametr bez ovlivnění dalších, zadejte 0 (nula) pro parametr, které nechcete změnit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Automatická správa paměti](../../../../docs/standard/automatic-memory-management.md)  
 [Uvolňování paměti](../../../../docs/standard/garbage-collection/index.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRGCManager2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
