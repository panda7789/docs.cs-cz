---
title: IHostCrst::Enter – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a472b686799bfec4b53b8880a0c52c6f0846b03a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442374"
---
# <a name="ihostcrstenter-method"></a>IHostCrst::Enter – metoda
Zadá kritické část, která je reprezentována aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `option`  
 [v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, která určuje, jaké akce hostitele by měla přijmout, pokud operace bloky.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Enter` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `Enter` odpovídá Win32 `EnterCriticalSection` funkce.  
  
> [!NOTE]
>  Tato metoda nevrátí, dokud nebude zadán kritická sekce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostCrst – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
