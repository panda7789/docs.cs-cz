---
title: ICLRMetaHostPolicy::GetRequestedRuntime – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 1b07029990ef529ded57bc569beff1061ad0f938
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140864"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime – metoda

Poskytuje rozhraní pro upřednostňovanou verzi modulu CLR (Common Language Runtime) na základě zásad hostování, spravovaného sestavení, řetězce verze a konfiguračního streamu. Tato metoda ve skutečnosti nenačítá ani neaktivuje CLR, ale jednoduše vrátí rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , které představuje výsledek zásady. Tato metoda nahrazuje metody [GetRequestedRuntimeInfo –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)a [GetCORRequiredVersion –](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a>Parametry

|Name|Popis|
|----------|-----------------|
|`dwPolicyFlags`|pro Požadovanou. Určuje člen výčtu [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) , který představuje zásadu vazby a libovolný počet modifikátorů. Jediná zásada, která je aktuálně k dispozici, je [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Modifikátory zahrnují [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)a [METAHOST_POLICY_. ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|pro Volitelné. Určuje cestu k souboru sestavení.|
|`pCfgStream`|pro Volitelné. Určuje konfigurační soubor jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[in, out] Volitelné. Určuje nebo vrátí upřednostňovanou verzi CLR, která má být načtena.|
|`pcchVersion`|[in, out] Požadovanou. Určuje očekávanou velikost `pwzVersion` jako vstup, aby se předešlo přetečení vyrovnávací paměti. Pokud má `pwzVersion` hodnotu null, `pcchVersion` při návratu `GetRequestedRuntime` obsahuje očekávanou velikost `pwzVersion`, aby bylo možné předběžné přidělení; v opačném případě `pcchVersion` obsahuje počet znaků zapsaných do `pwzVersion`.|
|`pwzImageVersion`|mimo Volitelné. Pokud `GetRequestedRuntime` vrací, obsahuje verzi CLR odpovídající rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , které je vráceno.|
|`pcchImageVersion`|[in, out] Volitelné. Určuje velikost `pwzImageVersion` jako vstup, aby nedošlo k přetečení vyrovnávací paměti. Pokud má `pwzImageVersion` hodnotu null, `pcchImageVersion` při návratu `GetRequestedRuntime` obsahuje požadovanou velikost `pwzImageVersion`, aby bylo možné předběžně přidělit.|
|`pdwConfigFlags`|mimo Volitelné. Pokud `GetRequestedRuntime` používá konfigurační soubor během procesu vytváření vazby, `pdwConfigFlags` obsahuje hodnotu [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) , která označuje, zda má [\<spouštěcí >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) element nastaven atribut `useLegacyV2RuntimeActivationPolicy` a hodnotu atribut. Použijte masku [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) k `pdwConfigFlags` k získání hodnot relevantních pro `useLegacyV2RuntimeActivationPolicy`.|
|`riid`|pro Určuje identifikátor rozhraní IID_ICLRRuntimeInfo pro požadované rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .|
|`ppRuntime`|mimo Když `GetRequestedRuntime` vrací, obsahuje ukazatel na odpovídající rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .|

## <a name="remarks"></a>Poznámky

Pokud je tato metoda úspěšná, má vedlejší účinky na kombinaci dalších příznaků s aktuálními výchozími příznaky při spuštění vráceného běhového rozhraní, pokud a pouze v případě, že v datovém proudu v rámci `<configuration><runtime>` existuje jeden nebo více následujících prvků. section

- `<gcServer enabled="true"/>` způsobí, že `STARTUP_SERVER_GC` nastavit.

- `<etwEnable enabled="true"/>` způsobí, že `STARTUP_ETW` nastavit.

- `<appDomainResourceMonitoring enabled="true"/>` způsobí, že `STARTUP_ARM` nastavit.

Výsledná výchozí hodnota `STARTUP_FLAGS` je bitová nebo kombinace hodnot, které jsou nastaveny z předchozího seznamu s výchozími příznaky spouštění.

## <a name="return-value"></a>Návratová hodnota

Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.

|HRESULT|Popis|
|-------------|-----------------|
|S_OK|Metoda byla úspěšně dokončena.|
|E_POINTER|`pwzVersion` není null a `pcchVersion` je null.<br /><br /> -nebo-<br /><br /> `pwzImageVersion` není null a `pcchImageVersion` je null.|
|E_INVALIDARG|`dwPolicyFlags` neurčuje `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|Paměť přidělená `pwzVersion` není dostačující.<br /><br /> -nebo-<br /><br /> Paměť přidělená `pwzImageVersion` není dostačující.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` zahrnuje METAHOST_POLICY_APPLY_UPGRADE_POLICY a `pwzVersion` i `pcchVersion` mají hodnotu null.|

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** MetaHost. h

**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll

**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICLRMetaHostPolicy – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
