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
ms.openlocfilehash: a9889ddf1c03f14835101f31d0a3b264f0016267
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676548"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="6ce54-102">ICLRMetaHost::GetRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="6ce54-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="6ce54-103">Získá [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které odpovídá na konkrétní verzi modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6ce54-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="6ce54-104">Tato metoda nahrazuje [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce použitá s [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) příznak.</span><span class="sxs-lookup"><span data-stu-id="6ce54-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce54-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ce54-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ce54-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ce54-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="6ce54-107">[in] Kompilace verzi rozhraní .NET Framework uložena v metadatech ve formátu "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="6ce54-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="6ce54-108">*A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní verze, podverze a číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ce54-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ce54-109">Tento parametr musí odpovídat názvu adresáře pro verzi rozhraní .NET Framework, jak se zobrazí v části C:\Windows\Microsoft.NET\Framework nebo C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="6ce54-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="6ce54-110">Příklad hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na číslo sestavení nainstalována.</span><span class="sxs-lookup"><span data-stu-id="6ce54-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="6ce54-111">Vyžaduje se předpona "v".</span><span class="sxs-lookup"><span data-stu-id="6ce54-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="6ce54-112">[in] Identifikátor pro požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ce54-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="6ce54-113">V současné době je jedinou platnou hodnotou pro tento parametr IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="6ce54-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="6ce54-114">[out] Ukazatel [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které odpovídá požadovaný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="6ce54-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ce54-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ce54-115">Return Value</span></span>  
 <span data-ttu-id="6ce54-116">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="6ce54-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6ce54-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ce54-117">HRESULT</span></span>|<span data-ttu-id="6ce54-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6ce54-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ce54-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ce54-119">S_OK</span></span>|<span data-ttu-id="6ce54-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="6ce54-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="6ce54-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6ce54-121">E_POINTER</span></span>|<span data-ttu-id="6ce54-122">`pwzVersion` nebo `ppRuntime` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6ce54-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ce54-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ce54-123">Remarks</span></span>  
 <span data-ttu-id="6ce54-124">Tato metoda komunikuje konzistentně starší verze rozhraní, jako [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní a starší verze funkce, jako je například zastaralá `CorBindTo*` funkcí (naleznete v tématu [zastaralé hostování funkce CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní .NET Framework 2.0, který je hostitelem rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="6ce54-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="6ce54-125">To znamená modulů runtime, která jsou načtena pomocí starší verze rozhraní API jsou viditelné pro nové rozhraní API a moduly runtime, které jsou načteny pomocí nového rozhraní API jsou viditelné pro starší verze rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6ce54-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ce54-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ce54-126">Requirements</span></span>  
 <span data-ttu-id="6ce54-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ce54-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ce54-128">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6ce54-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6ce54-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ce54-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ce54-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ce54-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce54-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ce54-131">See also</span></span>
- [<span data-ttu-id="6ce54-132">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ce54-132">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="6ce54-133">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6ce54-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="6ce54-134">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6ce54-134">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="6ce54-135">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6ce54-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="6ce54-136">Hostování</span><span class="sxs-lookup"><span data-stu-id="6ce54-136">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
