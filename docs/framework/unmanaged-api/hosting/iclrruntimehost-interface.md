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
ms.openlocfilehash: dd1aa4089a981d82ae1403189343694a065a701d
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703660"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="fe605-102">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe605-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="fe605-103">Poskytuje podobné funkce jako rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) , které je k dispozici ve .NET Framework verze 1, s následujícími změnami:</span><span class="sxs-lookup"><span data-stu-id="fe605-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="fe605-104">Přidání metody [SetHostControl –](iclrruntimehost-sethostcontrol-method.md) k nastavení rozhraní pro řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="fe605-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="fe605-105">Vynechání některých metod, které poskytuje `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="fe605-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe605-106">Metody</span><span class="sxs-lookup"><span data-stu-id="fe605-106">Methods</span></span>  
  
|<span data-ttu-id="fe605-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-107">Method</span></span>|<span data-ttu-id="fe605-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fe605-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe605-109">ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="fe605-110">Používá se ve scénářích nasazení ClickOnce založených na manifestech k určení aplikace, která se má aktivovat v nové doméně.</span><span class="sxs-lookup"><span data-stu-id="fe605-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="fe605-111">ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="fe605-112">Určuje, <xref:System.AppDomain> ve kterém se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="fe605-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="fe605-113">ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="fe605-114">Vyvolá zadanou metodu zadaného typu v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe605-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="fe605-115">GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="fe605-116">Načte ukazatel rozhraní typu [ICLRControl](iclrcontrol-interface.md) , který můžou hostitelé použít k přizpůsobení aspektů modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="fe605-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="fe605-117">GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="fe605-118">Získá číselný identifikátor <xref:System.AppDomain> aktuálně prováděného.</span><span class="sxs-lookup"><span data-stu-id="fe605-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="fe605-119">SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="fe605-120">Nastaví rozhraní pro řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="fe605-120">Sets the host control interface.</span></span> <span data-ttu-id="fe605-121">`SetHostControl`Před voláním je nutné zavolat `Start` .</span><span class="sxs-lookup"><span data-stu-id="fe605-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="fe605-122">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="fe605-123">Inicializuje modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="fe605-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="fe605-124">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="fe605-125">Zastaví provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="fe605-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="fe605-126">UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="fe605-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="fe605-127">Uvolní <xref:System.AppDomain> , který odpovídá zadanému číselnému identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="fe605-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe605-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe605-128">Remarks</span></span>  
 <span data-ttu-id="fe605-129">Počínaje .NET Framework 4 použijte rozhraní [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) k získání ukazatele na rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) a pak zavolejte metodu [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) , abyste získali ukazatel na `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="fe605-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="fe605-130">V dřívějších verzích .NET Framework hostitel získá ukazatel na `ICLRRuntimeHost` instanci voláním [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="fe605-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="fe605-131">Chcete-li zajistit implementace libovolné technologie, které jsou součástí .NET Framework verze 2,0, je nutné použít `ICLRRuntimeHost` místo `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="fe605-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fe605-132">Nevolejte metodu [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním metody [ExecuteApplication –](iclrruntimehost-executeapplication-method.md) pro aktivaci aplikace založené na manifestu.</span><span class="sxs-lookup"><span data-stu-id="fe605-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="fe605-133">Pokud `Start` je metoda volána jako první, `ExecuteApplication` volání metody se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="fe605-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe605-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe605-134">Requirements</span></span>  
 <span data-ttu-id="fe605-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe605-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe605-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fe605-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe605-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fe605-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe605-138">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe605-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe605-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe605-139">See also</span></span>

- [<span data-ttu-id="fe605-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="fe605-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="fe605-141">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="fe605-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="fe605-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe605-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="fe605-143">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe605-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="fe605-144">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="fe605-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="fe605-145">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="fe605-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
