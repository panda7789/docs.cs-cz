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
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="b068d-102">ICLRMetaHostPolicy::GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="b068d-102">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="b068d-103">Poskytuje rozhraní pro upřednostňovanou verzi modulu CLR (Common Language Runtime) na základě zásad hostování, spravovaného sestavení, řetězce verze a konfiguračního streamu.</span><span class="sxs-lookup"><span data-stu-id="b068d-103">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="b068d-104">Tato metoda ve skutečnosti nenačítá ani neaktivuje CLR, ale jednoduše vrátí rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které představuje výsledek zásady.</span><span class="sxs-lookup"><span data-stu-id="b068d-104">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="b068d-105">Tato metoda nahrazuje metody [GetRequestedRuntimeInfo –](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion –](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost –](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg –](corbindtoruntimebycfg-function.md)a [GetCORRequiredVersion –](getcorrequiredversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b068d-105">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="b068d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b068d-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="b068d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b068d-107">Parameters</span></span>

|<span data-ttu-id="b068d-108">Name</span><span class="sxs-lookup"><span data-stu-id="b068d-108">Name</span></span>|<span data-ttu-id="b068d-109">Description</span><span class="sxs-lookup"><span data-stu-id="b068d-109">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="b068d-110">pro Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="b068d-110">[in] Required.</span></span> <span data-ttu-id="b068d-111">Určuje člen výčtu [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , který představuje zásadu vazby a libovolný počet modifikátorů.</span><span class="sxs-lookup"><span data-stu-id="b068d-111">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="b068d-112">Jediná zásada, která je aktuálně dostupná, je [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b068d-112">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="b068d-113">Mezi modifikátory patří [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)a [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b068d-113">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="b068d-114">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b068d-114">[in] Optional.</span></span> <span data-ttu-id="b068d-115">Určuje cestu k souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="b068d-115">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="b068d-116">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b068d-116">[in] Optional.</span></span> <span data-ttu-id="b068d-117">Určuje konfigurační soubor jako <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b068d-117">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="b068d-118">[in, out] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b068d-118">[in, out] Optional.</span></span> <span data-ttu-id="b068d-119">Určuje nebo vrátí upřednostňovanou verzi CLR, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="b068d-119">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="b068d-120">[in, out] Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="b068d-120">[in, out] Required.</span></span> <span data-ttu-id="b068d-121">Určuje očekávanou velikost `pwzVersion` jako vstup, aby nedošlo k přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b068d-121">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="b068d-122">Pokud `pwzVersion` je null, `pcchVersion` obsahuje očekávanou velikost `pwzVersion` při `GetRequestedRuntime` návratu, aby bylo možné předběžné přidělení; v opačném případě `pcchVersion` obsahuje počet znaků zapsaných do `pwzVersion` .</span><span class="sxs-lookup"><span data-stu-id="b068d-122">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="b068d-123">mimo Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b068d-123">[out] Optional.</span></span> <span data-ttu-id="b068d-124">Při `GetRequestedRuntime` návratu obsahuje verzi CLR odpovídající rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které je vráceno.</span><span class="sxs-lookup"><span data-stu-id="b068d-124">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="b068d-125">[in, out] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b068d-125">[in, out] Optional.</span></span> <span data-ttu-id="b068d-126">Určuje velikost `pwzImageVersion` jako vstup, aby se předešlo přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b068d-126">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="b068d-127">Pokud `pwzImageVersion` je null, `pcchImageVersion` obsahuje požadovanou velikost `pwzImageVersion` při `GetRequestedRuntime` návratu, aby bylo možné předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="b068d-127">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="b068d-128">mimo Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b068d-128">[out] Optional.</span></span> <span data-ttu-id="b068d-129">Pokud `GetRequestedRuntime` Nástroj používá konfigurační soubor během procesu vytváření vazby, `pdwConfigFlags` obsahuje hodnotu [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) , která označuje, zda má [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) prvek `useLegacyV2RuntimeActivationPolicy` nastaven atribut a hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="b068d-129">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="b068d-130">Použijte [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) masku pro `pdwConfigFlags` k získání hodnot relevantních pro `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="b068d-130">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="b068d-131">pro Určuje identifikátor rozhraní IID_ICLRRuntimeInfo pro požadované rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b068d-131">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="b068d-132">mimo Při `GetRequestedRuntime` návratu obsahuje ukazatel na odpovídající rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b068d-132">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b068d-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b068d-133">Remarks</span></span>

<span data-ttu-id="b068d-134">Pokud je tato metoda úspěšná, má vedlejší účinek na kombinaci dalších příznaků s aktuálními výchozími příznaky při spuštění vráceného běhového rozhraní, pokud a pouze v případě, že v datovém proudu v rámci oddílu existuje jeden nebo více následujících prvků `<configuration><runtime>` :</span><span class="sxs-lookup"><span data-stu-id="b068d-134">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="b068d-135">`<gcServer enabled="true"/>`příčiny `STARTUP_SERVER_GC` nastavení.</span><span class="sxs-lookup"><span data-stu-id="b068d-135">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="b068d-136">`<etwEnable enabled="true"/>`příčiny `STARTUP_ETW` nastavení.</span><span class="sxs-lookup"><span data-stu-id="b068d-136">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="b068d-137">`<appDomainResourceMonitoring enabled="true"/>`příčiny `STARTUP_ARM` nastavení.</span><span class="sxs-lookup"><span data-stu-id="b068d-137">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="b068d-138">Výsledná výchozí `STARTUP_FLAGS` hodnota je bitová nebo kombinace hodnot, které jsou nastaveny z předchozího seznamu s výchozími příznaky spouštění.</span><span class="sxs-lookup"><span data-stu-id="b068d-138">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="b068d-139">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b068d-139">Return Value</span></span>

<span data-ttu-id="b068d-140">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="b068d-140">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="b068d-141">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b068d-141">HRESULT</span></span>|<span data-ttu-id="b068d-142">Description</span><span class="sxs-lookup"><span data-stu-id="b068d-142">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="b068d-143">S_OK</span><span class="sxs-lookup"><span data-stu-id="b068d-143">S_OK</span></span>|<span data-ttu-id="b068d-144">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b068d-144">The method completed successfully.</span></span>|
|<span data-ttu-id="b068d-145">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b068d-145">E_POINTER</span></span>|<span data-ttu-id="b068d-146">`pwzVersion`nemá hodnotu null a `pcchVersion` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b068d-146">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="b068d-147">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b068d-147">-or-</span></span><br /><br /> <span data-ttu-id="b068d-148">`pwzImageVersion`nemá hodnotu null a `pcchImageVersion` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b068d-148">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="b068d-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b068d-149">E_INVALIDARG</span></span>|<span data-ttu-id="b068d-150">`dwPolicyFlags`neurčuje `METAHOST_POLICY_HIGHCOMPAT` .</span><span class="sxs-lookup"><span data-stu-id="b068d-150">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="b068d-151">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b068d-151">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b068d-152">Paměť přidělená k `pwzVersion` není dostačující.</span><span class="sxs-lookup"><span data-stu-id="b068d-152">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="b068d-153">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b068d-153">-or-</span></span><br /><br /> <span data-ttu-id="b068d-154">Paměť přidělená k `pwzImageVersion` není dostačující.</span><span class="sxs-lookup"><span data-stu-id="b068d-154">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="b068d-155">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="b068d-155">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="b068d-156">`dwPolicyFlags`zahrnuje METAHOST_POLICY_APPLY_UPGRADE_POLICY a obojí `pwzVersion` a `pcchVersion` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b068d-156">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="b068d-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b068d-157">Requirements</span></span>

<span data-ttu-id="b068d-158">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b068d-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b068d-159">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b068d-159">**Header:** MetaHost.h</span></span>

<span data-ttu-id="b068d-160">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b068d-160">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="b068d-161">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b068d-161">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b068d-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b068d-162">See also</span></span>

- [<span data-ttu-id="b068d-163">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b068d-163">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="b068d-164">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="b068d-164">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="b068d-165">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b068d-165">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b068d-166">Hosting</span><span class="sxs-lookup"><span data-stu-id="b068d-166">Hosting</span></span>](index.md)
