---
title: CorBindToRuntimeHost – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1952121a6c0c735926944c839c3c7e8a8db5fb53
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396828"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="0b40a-102">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="0b40a-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="0b40a-103">Umožňuje hostitelům načíst zadanou verzi modulu common language runtime (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="0b40a-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="0b40a-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b40a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b40a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b40a-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0b40a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b40a-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="0b40a-107">[in] Řetězec, který popisuje verzi modulu CLR, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="0b40a-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="0b40a-108">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="0b40a-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="0b40a-109">Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="0b40a-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="0b40a-110">Některé verze modulu CLR jsou nainstalovány s prohlášením o zásadách, které určuje kompatibilitu s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0b40a-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="0b40a-111">Ve výchozím nastavení překrytí spuštění vyhodnotí `pwszVersion` proti prohlášení zásad a načte nejnovější verze modulu runtime, který je kompatibilní s verzí, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="0b40a-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="0b40a-112">Hostitel může donutit překrytí, aby přeskočilo hodnocení zásad a načetlo přesnou verzi zadané v `pwszVersion` předáním hodnoty startup_loader_safemode pro `startupFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="0b40a-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="0b40a-113">Pokud `pwszVersion` je `null,` metoda nenačte žádné verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0b40a-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="0b40a-114">Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, což znamená, že se nezdařilo načtení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0b40a-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="0b40a-115">[in] Řetězec, který určuje, jestli se má načíst server nebo pracovní stanice sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="0b40a-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="0b40a-116">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="0b40a-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="0b40a-117">Sestavení serveru je optimalizováno pro využití více procesorů pro uvolňování paměti kolekce a sestavení pracovní stanice je optimalizována pro klientské aplikace spuštěné v počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="0b40a-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="0b40a-118">Pokud `pwszBuildFlavor` je nastavena na hodnotu null, je načteno sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="0b40a-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="0b40a-119">Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno, i když `pwszBuildFlavor` je nastavena na `svr`.</span><span class="sxs-lookup"><span data-stu-id="0b40a-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="0b40a-120">Ale pokud `pwszBuildFlavor` je nastavena na `svr` a souběžné uvolňování je vyznačeno (viz popis `startupFlags` parametr), načte se sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="0b40a-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b40a-121">Souběžné uvolňování paměti se nepodporuje v aplikacích spuštěných WOW64 x86 emulátor v 64bitových systémech, které implementují Intel Itanium architekturu (dříve označovanou jako IA-64).</span><span class="sxs-lookup"><span data-stu-id="0b40a-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="0b40a-122">Další informace o použití modulu WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="0b40a-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="0b40a-123">[in] Název konfiguračního souboru hostitele, který určuje verzi modulu CLR pro načtení.</span><span class="sxs-lookup"><span data-stu-id="0b40a-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="0b40a-124">Pokud název souboru neobsahuje úplnou cestu, soubor je považován za ve stejném adresáři jako spustitelný soubor, který provádí volání.</span><span class="sxs-lookup"><span data-stu-id="0b40a-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="0b40a-125">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="0b40a-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="0b40a-126">[in] Sada příznaků, které řídí souběžné uvolňování paměti, doménově neutrální kód a chování `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="0b40a-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="0b40a-127">Pokud není nastaven žádný příznak, výchozí hodnota je jedinou doménu.</span><span class="sxs-lookup"><span data-stu-id="0b40a-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="0b40a-128">Seznam podporovaných hodnot naleznete v tématu [startup_flags – výčet](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0b40a-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0b40a-129">[in] `CLSID` Třídy typu coclass, která implementuje [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0b40a-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0b40a-130">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0b40a-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0b40a-131">[in] `IID` Rozhraní, které jste požádali.</span><span class="sxs-lookup"><span data-stu-id="0b40a-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="0b40a-132">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0b40a-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0b40a-133">[out] Ukazatel rozhraní na verzi modulu runtime, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="0b40a-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b40a-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b40a-134">Requirements</span></span>  
 <span data-ttu-id="0b40a-135">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b40a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b40a-136">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="0b40a-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0b40a-137">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b40a-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b40a-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b40a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b40a-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b40a-139">See Also</span></span>  
 [<span data-ttu-id="0b40a-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="0b40a-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="0b40a-141">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="0b40a-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="0b40a-142">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="0b40a-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="0b40a-143">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="0b40a-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="0b40a-144">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b40a-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="0b40a-145">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="0b40a-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
