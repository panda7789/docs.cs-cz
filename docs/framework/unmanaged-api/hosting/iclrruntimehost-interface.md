---
title: ICLRRuntimeHost – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f159c0b57f2087b608fac8cbc9b9c64ceb063a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965994"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="d3985-102">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3985-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="d3985-103">Poskytuje podobné funkce jako rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) , které je k dispozici ve .NET Framework verze 1, s následujícími změnami:</span><span class="sxs-lookup"><span data-stu-id="d3985-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="d3985-104">Přidání metody [SetHostControl –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) k nastavení rozhraní pro řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="d3985-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="d3985-105">Vynechání některých metod, které `ICorRuntimeHost`poskytuje.</span><span class="sxs-lookup"><span data-stu-id="d3985-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3985-106">Metody</span><span class="sxs-lookup"><span data-stu-id="d3985-106">Methods</span></span>  
  
|<span data-ttu-id="d3985-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-107">Method</span></span>|<span data-ttu-id="d3985-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d3985-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3985-109">ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="d3985-110">Používá se ve scénářích nasazení ClickOnce založených na manifestech k určení aplikace, která se má aktivovat v nové doméně.</span><span class="sxs-lookup"><span data-stu-id="d3985-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="d3985-111">ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="d3985-112">Určuje, <xref:System.AppDomain> ve kterém se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="d3985-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="d3985-113">ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="d3985-114">Vyvolá zadanou metodu zadaného typu v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3985-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="d3985-115">GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="d3985-116">Načte ukazatel rozhraní typu [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , který můžou hostitelé použít k přizpůsobení aspektů modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="d3985-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="d3985-117">GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="d3985-118">Získá číselný identifikátor <xref:System.AppDomain> aktuálně prováděného.</span><span class="sxs-lookup"><span data-stu-id="d3985-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="d3985-119">SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="d3985-120">Nastaví rozhraní pro řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="d3985-120">Sets the host control interface.</span></span> <span data-ttu-id="d3985-121">Před voláním `SetHostControl` `Start`je nutné zavolat.</span><span class="sxs-lookup"><span data-stu-id="d3985-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="d3985-122">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="d3985-123">Inicializuje modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="d3985-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="d3985-124">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="d3985-125">Zastaví provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="d3985-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="d3985-126">UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="d3985-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="d3985-127">Uvolní <xref:System.AppDomain> , který odpovídá zadanému číselnému identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="d3985-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3985-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3985-128">Remarks</span></span>  
 <span data-ttu-id="d3985-129">Počínaje .NET Framework 4 použijte rozhraní [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) k získání ukazatele na rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) a pak zavolejte metodu [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) , abyste získali ukazatel na `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="d3985-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="d3985-130">V dřívějších verzích .NET Framework hostitel získá ukazatel na `ICLRRuntimeHost` instanci voláním [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="d3985-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="d3985-131">Chcete-li zajistit implementace libovolné technologie, které jsou součástí .NET Framework verze 2,0, je nutné použít `ICLRRuntimeHost` `ICorRuntimeHost`místo.</span><span class="sxs-lookup"><span data-stu-id="d3985-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3985-132">Nevolejte metodu [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním metody [ExecuteApplication –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) pro aktivaci aplikace založené na manifestu.</span><span class="sxs-lookup"><span data-stu-id="d3985-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="d3985-133">`ExecuteApplication` Pokud je `Start` metoda volána jako první, volání metody se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="d3985-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3985-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3985-134">Requirements</span></span>  
 <span data-ttu-id="d3985-135">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3985-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3985-136">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3985-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3985-137">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3985-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3985-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3985-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3985-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3985-139">See also</span></span>

- [<span data-ttu-id="d3985-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="d3985-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="d3985-141">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="d3985-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="d3985-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3985-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d3985-143">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3985-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="d3985-144">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d3985-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d3985-145">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="d3985-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
