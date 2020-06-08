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
ms.openlocfilehash: 37167b7a9aefa6cd9d5e4df043e8bbc1b0514261
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504118"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime – metoda

Poskytuje rozhraní pro upřednostňovanou verzi modulu CLR (Common Language Runtime) na základě zásad hostování, spravovaného sestavení, řetězce verze a konfiguračního streamu. Tato metoda ve skutečnosti nenačítá ani neaktivuje CLR, ale jednoduše vrátí rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které představuje výsledek zásady. Tato metoda nahrazuje metody [GetRequestedRuntimeInfo –](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion –](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost –](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg –](corbindtoruntimebycfg-function.md)a [GetCORRequiredVersion –](getcorrequiredversion-function.md) .

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

|Name|Description|
|----------|-----------------|
|`dwPolicyFlags`|pro Požadovanou. Určuje člen výčtu [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , který představuje zásadu vazby a libovolný počet modifikátorů. Jediná zásada, která je aktuálně dostupná, je [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).<br /><br /> Mezi modifikátory patří [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)a [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).|
|`pwzBinary`|pro Volitelné. Určuje cestu k souboru sestavení.|
|`pCfgStream`|pro Volitelné. Určuje konfigurační soubor jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .|
|`pwzVersion`|[in, out] Volitelné. Určuje nebo vrátí upřednostňovanou verzi CLR, která má být načtena.|
|`pcchVersion`|[in, out] Požadovanou. Určuje očekávanou velikost `pwzVersion` jako vstup, aby nedošlo k přetečení vyrovnávací paměti. Pokud `pwzVersion` je null, `pcchVersion` obsahuje očekávanou velikost `pwzVersion` při `GetRequestedRuntime` návratu, aby bylo možné předběžné přidělení; v opačném případě `pcchVersion` obsahuje počet znaků zapsaných do `pwzVersion` .|
|`pwzImageVersion`|mimo Volitelné. Při `GetRequestedRuntime` návratu obsahuje verzi CLR odpovídající rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které je vráceno.|
|`pcchImageVersion`|[in, out] Volitelné. Určuje velikost `pwzImageVersion` jako vstup, aby se předešlo přetečení vyrovnávací paměti. Pokud `pwzImageVersion` je null, `pcchImageVersion` obsahuje požadovanou velikost `pwzImageVersion` při `GetRequestedRuntime` návratu, aby bylo možné předběžné přidělení.|
|`pdwConfigFlags`|mimo Volitelné. Pokud `GetRequestedRuntime` Nástroj používá konfigurační soubor během procesu vytváření vazby, `pdwConfigFlags` obsahuje hodnotu [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) , která označuje, zda má [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) prvek `useLegacyV2RuntimeActivationPolicy` nastaven atribut a hodnotu atributu. Použijte [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) masku pro `pdwConfigFlags` k získání hodnot relevantních pro `useLegacyV2RuntimeActivationPolicy` .|
|`riid`|pro Určuje identifikátor rozhraní IID_ICLRRuntimeInfo pro požadované rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .|
|`ppRuntime`|mimo Při `GetRequestedRuntime` návratu obsahuje ukazatel na odpovídající rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .|

## <a name="remarks"></a>Poznámky

Pokud je tato metoda úspěšná, má vedlejší účinek na kombinaci dalších příznaků s aktuálními výchozími příznaky při spuštění vráceného běhového rozhraní, pokud a pouze v případě, že v datovém proudu v rámci oddílu existuje jeden nebo více následujících prvků `<configuration><runtime>` :

- `<gcServer enabled="true"/>`příčiny `STARTUP_SERVER_GC` nastavení.

- `<etwEnable enabled="true"/>`příčiny `STARTUP_ETW` nastavení.

- `<appDomainResourceMonitoring enabled="true"/>`příčiny `STARTUP_ARM` nastavení.

Výsledná výchozí `STARTUP_FLAGS` hodnota je bitová nebo kombinace hodnot, které jsou nastaveny z předchozího seznamu s výchozími příznaky spouštění.

## <a name="return-value"></a>Návratová hodnota

Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.

|HRESULT|Description|
|-------------|-----------------|
|S_OK|Metoda byla úspěšně dokončena.|
|E_POINTER|`pwzVersion`nemá hodnotu null a `pcchVersion` má hodnotu null.<br /><br /> -nebo-<br /><br /> `pwzImageVersion`nemá hodnotu null a `pcchImageVersion` má hodnotu null.|
|E_INVALIDARG|`dwPolicyFlags`neurčuje `METAHOST_POLICY_HIGHCOMPAT` .|
|ERROR_INSUFFICIENT_BUFFER|Paměť přidělená k `pwzVersion` není dostačující.<br /><br /> -nebo-<br /><br /> Paměť přidělená k `pwzImageVersion` není dostačující.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags`zahrnuje METAHOST_POLICY_APPLY_UPGRADE_POLICY a obojí `pwzVersion` a `pcchVersion` má hodnotu null.|

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** MetaHost. h

**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll

**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICLRMetaHostPolicy – rozhraní](iclrmetahostpolicy-interface.md)
- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hosting](index.md)
