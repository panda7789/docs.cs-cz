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
ms.openlocfilehash: 7e1965917e8a1c5ae07cf119df3664b969a979be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969255"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="c4171-102">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="c4171-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="c4171-103">Umožňuje hostitelům načíst zadanou verzi modulu CLR (Common Language Runtime) do procesu.</span><span class="sxs-lookup"><span data-stu-id="c4171-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="c4171-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c4171-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4171-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4171-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c4171-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4171-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="c4171-107">pro Řetězec, který popisuje verzi CLR, kterou chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="c4171-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="c4171-108">Číslo verze v .NET Framework se skládá ze čtyř částí oddělených tečkami: *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="c4171-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="c4171-109">Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="c4171-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="c4171-110">Některé verze modulu CLR jsou nainstalovány s příkazem zásad, který určuje kompatibilitu s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c4171-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="c4171-111">Ve výchozím nastavení překrytí po spuštění `pwszVersion` vyhodnocuje příkazy zásad a načte nejnovější verzi modulu runtime, která je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="c4171-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="c4171-112">Hostitel může vynutit překrytí a přeskočit vyhodnocení zásad a načíst přesnou verzi určenou `pwszVersion` v předáním hodnoty STARTUP_LOADER_SAFEMODE `startupFlags` pro parametr.</span><span class="sxs-lookup"><span data-stu-id="c4171-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="c4171-113">Pokud `pwszVersion` je`null,` Metoda nenačte žádnou verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="c4171-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="c4171-114">Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, což znamená, že se nepodařilo načíst modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c4171-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="c4171-115">pro Řetězec, který určuje, zda má být načten Server nebo pracovní stanice sestavení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c4171-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="c4171-116">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="c4171-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="c4171-117">Sestavení serveru je optimalizované tak, aby využívalo více procesorů pro uvolňování paměti a aby bylo sestavení pracovní stanice optimalizované pro klientské aplikace běžící na počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="c4171-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="c4171-118">Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načteno sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="c4171-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="c4171-119">Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno i v případě `pwszBuildFlavor` , že je `svr`nastavena na.</span><span class="sxs-lookup"><span data-stu-id="c4171-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="c4171-120">Pokud `pwszBuildFlavor` je však nastavena na `svr` a souběžné uvolňování paměti zadáno ( `startupFlags` viz popis parametru), je sestavení serveru načteno.</span><span class="sxs-lookup"><span data-stu-id="c4171-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4171-121">Souběžné uvolňování paměti není podporováno v aplikacích spouštějících emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64).</span><span class="sxs-lookup"><span data-stu-id="c4171-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="c4171-122">Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="c4171-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="c4171-123">pro Název konfiguračního souboru hostitele, který určuje verzi modulu CLR, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="c4171-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="c4171-124">Pokud název souboru neobsahuje plně kvalifikovanou cestu, předpokládá se, že se soubor nachází ve stejném adresáři jako spustitelný soubor, který provádí volání.</span><span class="sxs-lookup"><span data-stu-id="c4171-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="c4171-125">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c4171-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="c4171-126">pro Sada příznaků, která řídí souběžné uvolňování paměti, doménový kód neutrální a chování `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="c4171-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="c4171-127">Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak.</span><span class="sxs-lookup"><span data-stu-id="c4171-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="c4171-128">Seznam podporovaných hodnot naleznete v tématu [výčet STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c4171-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="c4171-129">pro Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) `CLSID`</span><span class="sxs-lookup"><span data-stu-id="c4171-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="c4171-130">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c4171-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="c4171-131">pro `IID` Rozhraní, které požadujete.</span><span class="sxs-lookup"><span data-stu-id="c4171-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="c4171-132">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c4171-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="c4171-133">mimo Ukazatel rozhraní na verzi modulu runtime, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="c4171-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4171-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4171-134">Requirements</span></span>  
 <span data-ttu-id="c4171-135">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4171-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4171-136">**Hlaviček** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="c4171-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c4171-137">**Knihovna** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4171-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4171-138">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4171-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4171-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4171-139">See also</span></span>

- [<span data-ttu-id="c4171-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="c4171-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="c4171-141">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="c4171-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="c4171-142">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="c4171-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="c4171-143">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="c4171-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="c4171-144">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4171-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="c4171-145">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="c4171-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
