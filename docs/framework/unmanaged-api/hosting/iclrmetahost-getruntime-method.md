---
title: ICLRMetaHost::GetRuntime – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55fd6e6eec0c5107398bd0a7dda0281f69eb471b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492514"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime – metoda
Získá [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které odpovídá na konkrétní verzi modulu common language runtime (CLR). Tato metoda nahrazuje [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce použitá s [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) příznak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzVersion`  
 [in] Kompilace verzi rozhraní .NET Framework uložena v metadatech ve formátu "v*A*. *B*[. *X*] ". *A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní verze, podverze a číslo sestavení.  
  
> [!NOTE]
>  Tento parametr musí odpovídat názvu adresáře pro verzi rozhraní .NET Framework, jak se zobrazí v části C:\Windows\Microsoft.NET\Framework nebo C:\Windows\Microsoft.NET\Framework64.  
  
 Příklad hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na číslo sestavení nainstalována. Vyžaduje se předpona "v".  
  
 `riid`  
 [in] Identifikátor pro požadované rozhraní. V současné době je jedinou platnou hodnotou pro tento parametr IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 [out] Ukazatel [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které odpovídá požadovaný modul runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzVersion` nebo `ppRuntime` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda komunikuje konzistentně starší verze rozhraní, jako [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní a starší verze funkce, jako je například zastaralá `CorBindTo*` funkcí (naleznete v tématu [zastaralé hostování funkce CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní .NET Framework 2.0, který je hostitelem rozhraní API). To znamená modulů runtime, která jsou načtena pomocí starší verze rozhraní API jsou viditelné pro nové rozhraní API a moduly runtime, které jsou načteny pomocí nového rozhraní API jsou viditelné pro starší verze rozhraní API. .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [Rozhraní pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
