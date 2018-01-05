---
title: "ICLRMetaHostPolicy::GetRequestedRuntime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy.GetRequestedRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0501e104b2ed74656de125e668b7234efcbc9997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime – metoda
Poskytuje rozhraní pro upřednostňované verzí common language runtime (CLR) na základě hostování zásad, spravované sestavení, řetězec verze a konfiguraci datového proudu. Ve skutečnosti není načíst nebo aktivovat modulu CLR, ale jednoduše vrátí tato metoda [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které představuje výsledek zásad. Tato metoda nahrazuje [getrequestedruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [getrequestedruntimeversion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [corbindtoruntimebycfg –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), a [getcorrequiredversion –](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
  
|Název|Popis|  
|----------|-----------------|  
|`dwPolicyFlags`|[v] Vyžaduje se. Určuje členem [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) výčtu představující zásadu vazby a libovolný počet modifikátory. Pouze zásady, které aktuálně nejsou k dispozici je [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Modifikátory zahrnují [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), a [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|  
|`pwzBinary`|[v] Volitelný parametr. Určuje cestu k souboru sestavení.|  
|`pCfgStream`|[v] Volitelný parametr. Určuje konfiguračním souboru jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|  
|`pwzVersion`|[ve out] Volitelný parametr. Určuje nebo vrátí upřednostňovaný verze CLR má být načten.|  
|`pcchVersion`|[ve out] Vyžaduje se. Určuje očekávanou velikost `pwzVersion` jako vstup, aby se zabránilo přetečení vyrovnávací paměti. Pokud `pwzVersion` má hodnotu null, `pcchVersion` obsahuje očekávané velikosti `pwzVersion` při `GetRequestedRuntime` vrátí umožnit předběžné přidělení; v opačném `pcchVersion` obsahuje počet znaků, které jsou zapsány do `pwzVersion`.|  
|`pwzImageVersion`|[out] Volitelný parametr. Když `GetRequestedRuntime` vrátí, obsahuje odpovídající verze CLR do [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, která je vrácena.|  
|`pcchImageVersion`|[ve out] Volitelný parametr. Určuje velikost `pwzImageVersion` jako vstup, aby se zabránilo přetečení vyrovnávací paměti. Pokud `pwzImageVersion` má hodnotu null, `pcchImageVersion` obsahuje požadovaná velikost `pwzImageVersion` při `GetRequestedRuntime` vrátí umožnit předběžné přidělení.|  
|`pdwConfigFlags`|[out] Volitelný parametr. Pokud `GetRequestedRuntime` použije konfigurační soubor během procesu vázání, až se obnoví, `pdwConfigFlags` obsahuje [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) hodnotu, která určuje, zda [ \<spuštění >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) má element `useLegacyV2RuntimeActivationPolicy` atribut sady a hodnota atributu. Použít [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) maskování na `pdwConfigFlags` získat hodnoty relevantní pro `useLegacyV2RuntimeActivationPolicy`.|  
|`riid`|[v] Určuje identifikátor rozhraní IID_ICLRRuntimeInfo požadované [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.|  
|`ppRuntime`|[out] Když `GetRequestedRuntime` vrátí, obsahuje odkazy odpovídající [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Když tato metoda bude úspěšná, má vedlejším účinkem kombinace další příznaky s aktuální příznaky spuštění výchozí vrácený runtime rozhraní, pokud jeden nebo více následujících prvků existovat v datovém proudu konfigurace v rámci `<configuration><runtime>` části:  
  
-   `<gcServer enabled="true"/>`způsobí, že `STARTUP_SERVER_GC` nastavit.  
  
-   `<etwEnable enabled="true"/>`způsobí, že `STARTUP_ETW` nastavit.  
  
-   `<appDomainResourceMonitoring enabled="true"/>`způsobí, že `STARTUP_ARM` nastavit.  
  
 Výsledný výchozí `STARTUP_FLAGS` hodnota je bitová kombinace OR hodnot, které jsou nastavené v předchozím seznamu s příznaky spuštění výchozí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzVersion`není null a `pcchVersion` má hodnotu null.<br /><br /> -nebo-<br /><br /> `pwzImageVersion`není null a `pcchImageVersion` má hodnotu null.|  
|E_INVALIDARG|`dwPolicyFlags`neurčuje `METAHOST_POLICY_HIGHCOMPAT`.|  
|ERROR_INSUFFICIENT_BUFFER|Paměť přidělit `pwzVerison` je k dispozici.<br /><br /> -nebo-<br /><br /> Paměť přidělit `pwzImageVerison` je k dispozici.|  
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags`zahrnuje METAHOST_POLICY_APPLY_UPGRADE_POLICY a obě `pwzVersion` a `pcchVersion` mají hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRMetaHostPolicy – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
