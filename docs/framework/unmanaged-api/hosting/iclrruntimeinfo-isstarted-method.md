---
title: "ICLRRuntimeInfo::IsStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsStarted
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 991470ca0df3e0cf0470a8c40d3e8e4c40d96026
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisstarted-method"></a>ICLRRuntimeInfo::IsStarted – metoda
Určuje, zda byla spuštěna modulu runtime (to znamená, zda [iclrruntimehost::Start – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) byla volána a proběhla úspěšně).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbStarted`  
 [out] `true` Pokud tento modul runtime je spuštěn, jinak hodnota `false`.  
  
 `pdwStartupFlags`  
 [out] Vrátí příznaky, které byly použity při spuštění modulu runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_NOTIMPL|Společné jazykové verzi modulu runtime (CLR) je starší než verze CLR v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda funguje pouze s CLR verze starší než verze CLR v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
