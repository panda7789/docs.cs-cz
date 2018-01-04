---
title: "ICLRRuntimeInfo::SetDefaultStartupFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.SetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69306210ae4e957562d0bda88159d0506bca3877
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags – metoda
Nastaví příznaky spuštění a konfiguračního souboru hostitele, který se použije ke spuštění modulu runtime. Tato metoda nahrazuje použití `startupFlags` parametr ve [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwStartupFlags`  
 [v] Příznaky spuštění hostitele k nastavení. Použít stejnou příznaky jako s [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.  
  
 `pwzHostConfigFile`  
 [v] Cestu k adresáři konfiguračního souboru hostitelů nastavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel s více vlákny synchronizovat volání této metody. Jinak, může být přístup z více vláken A volání `SetStartupFlags` metoda po dokončení volání vlákno B `SetStartupFlags` a před zahájením vlákno B modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
