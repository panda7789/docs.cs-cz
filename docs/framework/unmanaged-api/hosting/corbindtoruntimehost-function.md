---
title: "CorBindToRuntimeHost – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeHost
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeHost
helpviewer_keywords: CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6d69f39aa74665843b0bf91407e764ea67f41d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="05a0a-102">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="05a0a-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="05a0a-103">Umožňuje hostitelům načíst zadaná verze modulu common language runtime (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="05a0a-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="05a0a-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05a0a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a0a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05a0a-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05a0a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="05a0a-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="05a0a-107">[v] Řetězec, který popisuje verzi modulu CLR, které se má zatížení.</span><span class="sxs-lookup"><span data-stu-id="05a0a-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="05a0a-108">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí, které jsou odděleny tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="05a0a-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="05a0a-109">Řetězec předány jako `pwszVersion` musí začínat znak "v" následované první tři části číslo verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="05a0a-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="05a0a-110">Některé verze modulu CLR jsou nainstalovány s prohlášení o zásadách, která určuje kompatibility s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="05a0a-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="05a0a-111">Ve výchozím nastavení, vyhodnotí shim spuštění `pwszVersion` proti příkazy zásad a zatížením nejnovější verzi modulu runtime, je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="05a0a-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="05a0a-112">Hostitel může vynutit shim přeskočit vyhodnocení zásad a načíst přesné verze zadaná v `pwszVersion` předáním hodnoty STARTUP_LOADER_SAFEMODE pro `startupFlags` parametr.</span><span class="sxs-lookup"><span data-stu-id="05a0a-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="05a0a-113">Pokud `pwszVersion` je `null,` metodu nenačte žádné verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="05a0a-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="05a0a-114">Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, která označuje, že se nepodařilo načíst modul runtime.</span><span class="sxs-lookup"><span data-stu-id="05a0a-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="05a0a-115">[v] Řetězec, který určuje, jestli zatížení serveru nebo pracovní stanice sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="05a0a-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="05a0a-116">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="05a0a-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="05a0a-117">Sestavení serveru je optimalizovaná tak, aby využít výhod více procesorů pro kolekce a sestavení pracovní stanici je optimalizovaná pro klientské aplikace spuštěné na počítač s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="05a0a-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="05a0a-118">Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načíst sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="05a0a-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="05a0a-119">Při spuštění na počítač s jedním procesorem, je vždy načteno sestavení pracovní stanice, i když `pwszBuildFlavor` je nastaven na `svr`.</span><span class="sxs-lookup"><span data-stu-id="05a0a-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="05a0a-120">Ale pokud `pwszBuildFlavor` je nastaven na `svr` a je zadána souběžné uvolňování (naleznete v popisu `startupFlags` parametr), je načíst sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="05a0a-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05a0a-121">Souběžné uvolňování není podporována v aplikacích spuštěných WOW64 x86 emulátoru na 64bitových systémech, které implementují architektuře Intel Itanium (dříve se označovaly jako platformu IA-64).</span><span class="sxs-lookup"><span data-stu-id="05a0a-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="05a0a-122">Další informace o používání WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitové aplikace](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="05a0a-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="05a0a-123">[v] Název konfiguračního souboru hostitele, který určuje verzi modulu CLR načíst.</span><span class="sxs-lookup"><span data-stu-id="05a0a-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="05a0a-124">Pokud název souboru neobsahuje plně kvalifikovanou cestu, předpokládá se, že soubor je ve stejném adresáři jako spustitelný soubor, který je uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="05a0a-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="05a0a-125">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="05a0a-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="05a0a-126">[v] Sadu příznaky, které se řídí souběžné uvolňování domény neutrální kód a chování `pwszVersion` parametr.</span><span class="sxs-lookup"><span data-stu-id="05a0a-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="05a0a-127">Výchozí hodnota je jedinou doménu, pokud žádné příznak nastaven.</span><span class="sxs-lookup"><span data-stu-id="05a0a-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="05a0a-128">Seznam podporovaných hodnot najdete v tématu [STARTUP_FLAGS – výčet](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="05a0a-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="05a0a-129">[v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05a0a-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="05a0a-130">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="05a0a-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="05a0a-131">[v] `IID` Rozhraní jste požádali.</span><span class="sxs-lookup"><span data-stu-id="05a0a-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="05a0a-132">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="05a0a-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="05a0a-133">[out] Ukazatel rozhraní na verzi modulu runtime, která byla načtena.</span><span class="sxs-lookup"><span data-stu-id="05a0a-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05a0a-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05a0a-134">Requirements</span></span>  
 <span data-ttu-id="05a0a-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a0a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a0a-136">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="05a0a-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="05a0a-137">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05a0a-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05a0a-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a0a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a0a-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="05a0a-139">See Also</span></span>  
 [<span data-ttu-id="05a0a-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="05a0a-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="05a0a-141">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="05a0a-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="05a0a-142">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="05a0a-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="05a0a-143">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="05a0a-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="05a0a-144">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05a0a-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="05a0a-145">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="05a0a-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
