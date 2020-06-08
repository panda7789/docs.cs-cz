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
ms.openlocfilehash: d482e25c7bf0f028e2478c8e7b7863bc54d7aeb9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504189"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="af913-102">ICLRMetaHost::GetRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="af913-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="af913-103">Získá rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které odpovídá konkrétní verzi modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="af913-103">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="af913-104">Tato metoda nahrazuje funkci [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) použitou s příznakem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="af913-104">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af913-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af913-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af913-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="af913-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="af913-107">pro Verze kompilace .NET Framework uložená v metadatech ve formátu "v*A*. *B*[.\* X\*] ".</span><span class="sxs-lookup"><span data-stu-id="af913-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="af913-108">*A*, *B*a *X* jsou desítková čísla, která odpovídají hlavní verzi, dílčí verzi a číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="af913-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af913-109">Tento parametr se musí shodovat s názvem adresáře pro verzi .NET Framework, jak se zobrazuje v části C:\Windows\Microsoft.NET\Framework nebo C:\Windows\Microsoft.NET\Framework64..</span><span class="sxs-lookup"><span data-stu-id="af913-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="af913-110">Příklady hodnot jsou "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" a "v 4.0". *X*, kde *x* závisí na nainstalovaném čísle sestavení.</span><span class="sxs-lookup"><span data-stu-id="af913-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="af913-111">Předpona "v" je povinná.</span><span class="sxs-lookup"><span data-stu-id="af913-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="af913-112">pro Identifikátor požadovaného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="af913-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="af913-113">V současné době je jediná platná hodnota pro tento parametr IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="af913-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="af913-114">mimo Ukazatel na rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které odpovídá požadovanému modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="af913-114">[out] A pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af913-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af913-115">Return Value</span></span>  
 <span data-ttu-id="af913-116">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="af913-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="af913-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af913-117">HRESULT</span></span>|<span data-ttu-id="af913-118">Description</span><span class="sxs-lookup"><span data-stu-id="af913-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af913-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="af913-119">S_OK</span></span>|<span data-ttu-id="af913-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="af913-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="af913-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="af913-121">E_POINTER</span></span>|<span data-ttu-id="af913-122">`pwzVersion`nebo `ppRuntime` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="af913-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af913-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af913-123">Remarks</span></span>  
 <span data-ttu-id="af913-124">Tato metoda komunikuje konzistentně se staršími rozhraními, jako je rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) a starší funkce, jako jsou zastaralé `CorBindTo*` funkce (viz téma [zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md) v rozhraní API pro hostování .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="af913-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="af913-125">To znamená, že moduly runtime načtené pomocí starší verze rozhraní API jsou viditelné pro nové rozhraní API a moduly runtime načtené pomocí nového rozhraní API jsou viditelné pro starší rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="af913-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af913-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af913-126">Requirements</span></span>  
 <span data-ttu-id="af913-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af913-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af913-128">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="af913-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="af913-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af913-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af913-130">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af913-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af913-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af913-131">See also</span></span>

- [<span data-ttu-id="af913-132">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af913-132">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="af913-133">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="af913-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="af913-134">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="af913-134">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="af913-135">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="af913-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="af913-136">Hosting</span><span class="sxs-lookup"><span data-stu-id="af913-136">Hosting</span></span>](index.md)
