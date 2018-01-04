---
title: "ICLRRuntimeInfo::IsLoaded – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoaded
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f1a83db3a5fc7b5f8b4ad763208fa31ab8f840e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded – metoda
Určuje, zda modul CLR (CLR) přidružené [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní je načten do procesu. Modul runtime můžete načíst bez také spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hndProcess`  
 [v] Popisovač pro proces.  
  
 `pbLoaded`  
 [out] `true` Pokud modulu CLR je načíst do procesu, jinak hodnota `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pbLoaded`má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je zpětně kompatibilní s následující funkce a rozhraní:  
  
-   [Icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní (v rozhraní .NET Framework verze 1 hostování API).  
  
-   [Iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní (v rozhraní .NET Framework 2.0 hostující rozhraní API).  
  
-   Zastaralé `CorBindTo*` funkce (viz [zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní .NET Framework 2.0, který je hostitelem rozhraní API).  
  
 Hostitel může volání jednoho z zastaralé `CorBindTo*` funkce, jako [corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) funkce pro vytvoření instance na konkrétní verzi modulu CLR. Potom může volat hostitele [iclrmetahost::getruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metoda a zadejte číslo verze získat [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.  
  
 Pokud hostitel pak zavolá `IsLoaded` metodu vrácených [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, `pbLoaded` vrátí `true`, jinak vrátí `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
