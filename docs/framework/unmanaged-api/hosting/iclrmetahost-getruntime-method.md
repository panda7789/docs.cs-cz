---
title: "ICLRMetaHost::GetRuntime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 849668f10eba81ba1667ac6518ab699e4bca3bcb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime – metoda
Získá [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, která odpovídá na konkrétní verzi common language runtime (CLR). Tato metoda nahrazuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce použít s [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) příznak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzVersion`  
 [v] Verze kompilace rozhraní .NET Framework, uložená v metadatech ve formátu "v*A*. *B*[. *X*] ". *A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní, vedlejší verze a číslo sestavení.  
  
> [!NOTE]
>  Tento parametr musí odpovídat názvu adresáře pro verzi rozhraní .NET Framework, jak se objevuje pod C:\Windows\Microsoft.NET\Framework nebo C:\Windows\Microsoft.NET\Framework64.  
  
 Ukázkové hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na počtu sestavení nainstalována. Vyžaduje se předpona "v".  
  
 `riid`  
 [v] Identifikátor pro požadované rozhraní. Jedinou platnou hodnotou tohoto parametru je v současné době IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 [out] Ukazatel [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, která odpovídá požadovaný modulu runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzVersion`nebo `ppRuntime` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda komunikuje konzistentně starší verze rozhraní, jako [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní a starší verze funkce jako je například nepoužívané `CorBindTo*` funkce (najdete v části [zastaralé CLR hostování funkce](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní .NET Framework 2.0, který je hostitelem rozhraní API). To znamená moduly runtime, které jsou načteny pomocí starší verze rozhraní API jsou viditelné pro nové rozhraní API a moduly runtime, které jsou načtené s novým rozhraním API jsou viditelné pro starší verze rozhraní API. .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 [Rozhraní pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
