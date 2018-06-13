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
ms.openlocfilehash: c83f6dfe069b75f1ab3256f4e5a083f85b50adad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435913"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="302f9-102">ICLRMetaHost::GetRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="302f9-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="302f9-103">Získá [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, která odpovídá na konkrétní verzi common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="302f9-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="302f9-104">Tato metoda nahrazuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce použít s [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) příznak.</span><span class="sxs-lookup"><span data-stu-id="302f9-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="302f9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="302f9-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="302f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="302f9-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="302f9-107">[v] Verze kompilace rozhraní .NET Framework, uložená v metadatech ve formátu "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="302f9-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="302f9-108">*A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní, vedlejší verze a číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="302f9-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="302f9-109">Tento parametr musí odpovídat názvu adresáře pro verzi rozhraní .NET Framework, jak se objevuje pod C:\Windows\Microsoft.NET\Framework nebo C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="302f9-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="302f9-110">Ukázkové hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na počtu sestavení nainstalována.</span><span class="sxs-lookup"><span data-stu-id="302f9-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="302f9-111">Vyžaduje se předpona "v".</span><span class="sxs-lookup"><span data-stu-id="302f9-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="302f9-112">[v] Identifikátor pro požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="302f9-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="302f9-113">Jedinou platnou hodnotou tohoto parametru je v současné době IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="302f9-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="302f9-114">[out] Ukazatel [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, která odpovídá požadovaný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="302f9-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="302f9-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="302f9-115">Return Value</span></span>  
 <span data-ttu-id="302f9-116">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="302f9-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="302f9-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="302f9-117">HRESULT</span></span>|<span data-ttu-id="302f9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="302f9-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="302f9-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="302f9-119">S_OK</span></span>|<span data-ttu-id="302f9-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="302f9-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="302f9-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="302f9-121">E_POINTER</span></span>|<span data-ttu-id="302f9-122">`pwzVersion` nebo `ppRuntime` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="302f9-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="302f9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="302f9-123">Remarks</span></span>  
 <span data-ttu-id="302f9-124">Tato metoda komunikuje konzistentně starší verze rozhraní, jako [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní a starší verze funkce jako je například nepoužívané `CorBindTo*` funkce (najdete v části [zastaralé CLR hostování funkce](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní .NET Framework 2.0, který je hostitelem rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="302f9-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="302f9-125">To znamená moduly runtime, které jsou načteny pomocí starší verze rozhraní API jsou viditelné pro nové rozhraní API a moduly runtime, které jsou načtené s novým rozhraním API jsou viditelné pro starší verze rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="302f9-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span> <span data-ttu-id="302f9-126">.</span><span class="sxs-lookup"><span data-stu-id="302f9-126">.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="302f9-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="302f9-127">Requirements</span></span>  
 <span data-ttu-id="302f9-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="302f9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="302f9-129">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="302f9-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="302f9-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="302f9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="302f9-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="302f9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302f9-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="302f9-132">See Also</span></span>  
 [<span data-ttu-id="302f9-133">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="302f9-133">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="302f9-134">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="302f9-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 [<span data-ttu-id="302f9-135">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="302f9-135">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="302f9-136">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="302f9-136">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="302f9-137">Hostování</span><span class="sxs-lookup"><span data-stu-id="302f9-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
