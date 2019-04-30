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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73d5c98500c510630b1f8d6081b654a6dbd88a5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771797"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime – metoda

Poskytuje rozhraní pro preferovanou verzi modulu common language runtime (CLR) na základě hostování zásad, spravované sestavení, řetězec verze a konfiguraci datového proudu. Ve skutečnosti načíst nebo aktivovat CLR, ale jednoduše vrátí tato metoda [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které představuje výsledek zásad. Tato metoda nahrazuje [getrequestedruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [getrequestedruntimeversion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), a [getcorrequiredversion –](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) metody.

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

|Název|Popis|
|----------|-----------------|
|`dwPolicyFlags`|[in] Povinné. Určuje členem [metahost_policy_flags –](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) výčet představující zásady vazeb a libovolný počet modifikátory. Pouze zásady, které jsou aktuálně dostupné [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Modifikátory zahrnují [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), a [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|[in] Volitelné. Určuje cestu k souboru sestavení.|
|`pCfgStream`|[in] Volitelné. Určuje konfigurační soubor jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[out v] Volitelné. Určuje nebo vrátí upřednostňovanou verzi CLR, který se má načíst.|
|`pcchVersion`|[out v] Povinné. Určuje očekávanou velikost `pwzVersion` jako vstup, aby se zabránilo přetečení vyrovnávací paměti. Pokud `pwzVersion` má hodnotu null, `pcchVersion` obsahuje očekávané velikosti `pwzVersion` při `GetRequestedRuntime` povolit předběžné přidělení; v opačném případě vrátí hodnotu `pcchVersion` obsahuje počet znaků, které jsou zapsány do `pwzVersion`.|
|`pwzImageVersion`|[out] Volitelné. Když `GetRequestedRuntime` vrátí, obsahuje odpovídající verzi CLR na [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, která je vrácena.|
|`pcchImageVersion`|[out v] Volitelné. Určuje velikost `pwzImageVersion` jako vstup, aby se zabránilo přetečení vyrovnávací paměti. Pokud `pwzImageVersion` má hodnotu null, `pcchImageVersion` obsahuje požadované velikosti `pwzImageVersion` při `GetRequestedRuntime` vrátí povolit předběžné přidělení.|
|`pdwConfigFlags`|[out] Volitelné. Pokud `GetRequestedRuntime` používá konfigurační soubor během vazby, když vrátí, `pdwConfigFlags` obsahuje [metahost_config_flags –](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) hodnotu, která určuje, zda [ \<spuštění >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) element má `useLegacyV2RuntimeActivationPolicy` atribut sady a hodnota atributu. Použít [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) maskování na `pdwConfigFlags` abyste získali hodnoty pro relevantní `useLegacyV2RuntimeActivationPolicy`.|
|`riid`|[in] Určuje identifikátor rozhraní IID_ICLRRuntimeInfo pro požadovanou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.|
|`ppRuntime`|[out] Když `GetRequestedRuntime` vrátí, obsahuje ukazatel na odpovídající [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.|

## <a name="remarks"></a>Poznámky

Když tato metoda bude úspěšná, nemá vliv na straně kombinace další příznaky se aktuální výchozí spuštění příznaky vrácené modul runtime rozhraní a pouze v případě jeden nebo více z následujících prvků existovat v datovém proudu konfigurace v rámci `<configuration><runtime>` části:

- `<gcServer enabled="true"/>` způsobí, že `STARTUP_SERVER_GC` nastavit.

- `<etwEnable enabled="true"/>` způsobí, že `STARTUP_ETW` nastavit.

- `<appDomainResourceMonitoring enabled="true"/>` způsobí, že `STARTUP_ARM` nastavit.

Výsledný výchozí `STARTUP_FLAGS` bitová kombinace OR hodnot, které jsou nastavené v předchozím seznamu spuštění Flags výchozí hodnotu.

## <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.

|HRESULT|Popis|
|-------------|-----------------|
|S_OK|Metoda byla úspěšně dokončena.|
|E_POINTER|`pwzVersion` není rovno hodnotě null a `pcchVersion` má hodnotu null.<br /><br /> -nebo-<br /><br /> `pwzImageVersion` není rovno hodnotě null a `pcchImageVersion` má hodnotu null.|
|E_INVALIDARG|`dwPolicyFlags` neurčuje `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|Paměť přidělená k `pwzVersion` je nedostatečné.<br /><br /> -nebo-<br /><br /> Paměť přidělená k `pwzImageVersion` je nedostatečné.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` zahrnuje METAHOST_POLICY_APPLY_UPGRADE_POLICY a obě `pwzVersion` a `pcchVersion` má hodnotu Null.|

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** MetaHost.h

**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICLRMetaHostPolicy – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
