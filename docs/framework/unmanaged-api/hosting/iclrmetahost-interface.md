---
title: ICLRMetaHost – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1b189b79a02f04b7f795ff2524441f12b053cec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984630"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="749ff-102">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="749ff-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="749ff-103">Poskytuje metody, které vrátí konkrétní verzi modulu common language runtime (CLR) podle její číslo verze, seznam všech nainstalovaných CLRs, vypsat všechny moduly runtime, která jsou načtena do určeného procesu, zjistit verzi modulu CLR použitou pro kompilaci sestavení, ukončit proces vypnutí čistý modul runtime a načítání starší verze rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="749ff-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="749ff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="749ff-104">Methods</span></span>  
  
|<span data-ttu-id="749ff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-105">Method</span></span>|<span data-ttu-id="749ff-106">Popis</span><span class="sxs-lookup"><span data-stu-id="749ff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="749ff-107">EnumerateInstalledRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="749ff-108">Vrátí výčet, který obsahuje platnou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ukazatel rozhraní pro každou verzi CLR, který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="749ff-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="749ff-109">EnumerateLoadedRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="749ff-110">Vrátí výčet, který obsahuje platnou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ukazatel rozhraní pro každý modul CLR, který je načten do daného procesu.</span><span class="sxs-lookup"><span data-stu-id="749ff-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="749ff-111">Tato metoda nahrazuje [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="749ff-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="749ff-112">ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="749ff-113">Pokusí se korektně vypnout všechny načtené moduly runtime a poté ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="749ff-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="749ff-114">Nahrazuje [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="749ff-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="749ff-115">GetRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="749ff-116">Získá [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které odpovídá konkrétní verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="749ff-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="749ff-117">Tato metoda nahrazuje [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce použitá s [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) příznak.</span><span class="sxs-lookup"><span data-stu-id="749ff-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="749ff-118">GetVersionFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="749ff-119">Získá sestavení původní verzi rozhraní .NET Framework kompilace (uložené v metadatech) zadané cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="749ff-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="749ff-120">Tato metoda nahrazuje [getfileversion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="749ff-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="749ff-121">QueryLegacyV2RuntimeBinding – metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="749ff-122">Vrátí rozhraní, která představuje modul runtime, ke kterému zásady aktivace starší verze byl vázán, například pomocí `useLegacyV2RuntimeActivationPolicy` atribut na [ \<spuštění > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) položka souboru konfigurace s přímým přístupem pomocí Aktivace starší verze rozhraní API, nebo pomocí volání [iclrruntimeinfo::bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="749ff-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="749ff-123">RequestRuntimeLoadedNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="749ff-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="749ff-124">Zpětné volání pro zadanou funkci ukazatel zaručuje, pokud verze CLR je prvním načtení, ale ještě nebyl spuštěn.</span><span class="sxs-lookup"><span data-stu-id="749ff-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="749ff-125">Tato metoda nahrazuje [lockclrversion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="749ff-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="749ff-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="749ff-126">Remarks</span></span>  
 <span data-ttu-id="749ff-127">Jediný způsob, jak získat instanci toto rozhraní je voláním [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkce takto:</span><span class="sxs-lookup"><span data-stu-id="749ff-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="749ff-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="749ff-128">Requirements</span></span>  
 <span data-ttu-id="749ff-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="749ff-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="749ff-130">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="749ff-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="749ff-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="749ff-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="749ff-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="749ff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="749ff-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="749ff-133">See also</span></span>

- [<span data-ttu-id="749ff-134">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="749ff-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="749ff-135">Hostování</span><span class="sxs-lookup"><span data-stu-id="749ff-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
