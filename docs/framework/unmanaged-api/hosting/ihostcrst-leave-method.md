---
title: IHostCrst::Leave – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae5561abb7cd0770fd5b7f290a4aa8dff85b6150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441649"
---
# <a name="ihostcrstleave-method"></a>IHostCrst::Leave – metoda
Ponechá kritické části, která je reprezentována aktuální instancí třídy [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Leave` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `Leave` Umožňuje CLR komunikovat přímo s hostitele dělení na vlákna implementace, nikoli pomocí odpovídající Win32 `LeaveCriticalSection` funkce. Vlákno, která přebírá vlastnictví kritická sekce reprezentována aktuální `IHostCrst` instance musí volat `Leave` po pokaždé, když se zadá tuto část, kritické.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostCrst – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
