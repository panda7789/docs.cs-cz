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
ms.openlocfilehash: bb760f4923cc3530a28bc68180db743ee468b51d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140909"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="a9f2c-102">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9f2c-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="a9f2c-103">Poskytuje metody, které vracejí konkrétní verzi modulu CLR (Common Language Runtime) na základě jeho čísla verze, vypíše všechny instalované CLRs, vypíše všechny moduly runtime, které jsou načteny v zadaném procesu, zjistí verzi CLR použitou pro zkompilování sestavení, ukončí proces. pomocí čistého vypnutí za běhu a dotazování starší vazby rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="a9f2c-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9f2c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a9f2c-104">Methods</span></span>  
  
|<span data-ttu-id="a9f2c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-105">Method</span></span>|<span data-ttu-id="a9f2c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a9f2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9f2c-107">EnumerateInstalledRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="a9f2c-108">Vrátí výčet obsahující platný ukazatel rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pro každou verzi CLR, která je nainstalována v počítači.</span><span class="sxs-lookup"><span data-stu-id="a9f2c-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="a9f2c-109">EnumerateLoadedRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="a9f2c-110">Vrátí výčet obsahující platný ukazatel rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pro každý modul CLR, který je načten v daném procesu.</span><span class="sxs-lookup"><span data-stu-id="a9f2c-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="a9f2c-111">Tato metoda nahrazuje [GetVersionFromProcess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="a9f2c-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="a9f2c-112">ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="a9f2c-113">Pokusí se řádně vypnout všechny načtené běhové moduly a pak proces ukončí.</span><span class="sxs-lookup"><span data-stu-id="a9f2c-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="a9f2c-114">Nahrazuje funkci [CorExitProcess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a9f2c-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="a9f2c-115">GetRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="a9f2c-116">Získá rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , které odpovídá konkrétní verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="a9f2c-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="a9f2c-117">Tato metoda nahrazuje funkci [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) , která se používá u příznaku [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="a9f2c-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="a9f2c-118">GetVersionFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="a9f2c-119">Získá původní verzi kompilace sestavení .NET Framework (uloženou v metadatech), která má za následek cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="a9f2c-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="a9f2c-120">Tato metoda nahrazuje [GetFileVersion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="a9f2c-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="a9f2c-121">QueryLegacyV2RuntimeBinding – metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="a9f2c-122">Vrátí rozhraní, které představuje modul runtime, ke kterému byly navázány zastaralé Zásady aktivace, například pomocí atributu `useLegacyV2RuntimeActivationPolicy` v položce konfiguračního souboru [\<po spuštění >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , a to přímým použitím starší verze aktivačních rozhraní API nebo volání metody [ICLRRuntimeInfo:: bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9f2c-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="a9f2c-123">RequestRuntimeLoadedNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="a9f2c-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="a9f2c-124">Garantuje zpětné volání na zadaný ukazatel na funkci při prvním načtení verze CLR, ale ještě nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="a9f2c-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="a9f2c-125">Tato metoda nahrazuje [LockClrVersion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="a9f2c-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9f2c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9f2c-126">Remarks</span></span>  
 <span data-ttu-id="a9f2c-127">Jediným způsobem, jak získat instanci tohoto rozhraní, je volání funkce [CLRCreateInstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a9f2c-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a9f2c-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9f2c-128">Requirements</span></span>  
 <span data-ttu-id="a9f2c-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9f2c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f2c-130">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a9f2c-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a9f2c-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9f2c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9f2c-132">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f2c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f2c-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9f2c-133">See also</span></span>

- [<span data-ttu-id="a9f2c-134">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a9f2c-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a9f2c-135">Hostování</span><span class="sxs-lookup"><span data-stu-id="a9f2c-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
