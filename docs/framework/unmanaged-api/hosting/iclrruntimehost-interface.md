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
ms.openlocfilehash: 72caac0aafe7f9c5919057a6ad2565258aec6a50
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504069"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="0b40e-102">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b40e-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="0b40e-103">Poskytuje podobné funkce jako rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) , které je k dispozici ve .NET Framework verze 1, s následujícími změnami:</span><span class="sxs-lookup"><span data-stu-id="0b40e-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="0b40e-104">Přidání metody [SetHostControl –](iclrruntimehost-sethostcontrol-method.md) k nastavení rozhraní pro řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="0b40e-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="0b40e-105">Vynechání některých metod, které poskytuje `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="0b40e-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b40e-106">Metody</span><span class="sxs-lookup"><span data-stu-id="0b40e-106">Methods</span></span>  
  
|<span data-ttu-id="0b40e-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-107">Method</span></span>|<span data-ttu-id="0b40e-108">Description</span><span class="sxs-lookup"><span data-stu-id="0b40e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b40e-109">ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="0b40e-110">Používá se ve scénářích nasazení ClickOnce založených na manifestech k určení aplikace, která se má aktivovat v nové doméně.</span><span class="sxs-lookup"><span data-stu-id="0b40e-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="0b40e-111">ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="0b40e-112">Určuje, <xref:System.AppDomain> ve kterém se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0b40e-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="0b40e-113">ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="0b40e-114">Vyvolá zadanou metodu zadaného typu v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="0b40e-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="0b40e-115">GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="0b40e-116">Načte ukazatel rozhraní typu [ICLRControl](iclrcontrol-interface.md) , který můžou hostitelé použít k přizpůsobení aspektů modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="0b40e-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="0b40e-117">GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="0b40e-118">Získá číselný identifikátor <xref:System.AppDomain> aktuálně prováděného.</span><span class="sxs-lookup"><span data-stu-id="0b40e-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="0b40e-119">SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="0b40e-120">Nastaví rozhraní pro řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="0b40e-120">Sets the host control interface.</span></span> <span data-ttu-id="0b40e-121">`SetHostControl`Před voláním je nutné zavolat `Start` .</span><span class="sxs-lookup"><span data-stu-id="0b40e-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="0b40e-122">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="0b40e-123">Inicializuje modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="0b40e-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="0b40e-124">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="0b40e-125">Zastaví provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="0b40e-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="0b40e-126">UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="0b40e-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="0b40e-127">Uvolní <xref:System.AppDomain> , který odpovídá zadanému číselnému identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="0b40e-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b40e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b40e-128">Remarks</span></span>  
 <span data-ttu-id="0b40e-129">Počínaje .NET Framework 4 použijte rozhraní [ICLRMetaHost](iclrmetahost-interface.md) k získání ukazatele na rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) a pak zavolejte metodu [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) , abyste získali ukazatel na `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="0b40e-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="0b40e-130">V dřívějších verzích .NET Framework hostitel získá ukazatel na `ICLRRuntimeHost` instanci voláním [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="0b40e-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="0b40e-131">Chcete-li zajistit implementace libovolné technologie, které jsou součástí .NET Framework verze 2,0, je nutné použít `ICLRRuntimeHost` místo `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="0b40e-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0b40e-132">Nevolejte metodu [Start](iclrruntimehost-start-method.md) před voláním metody [ExecuteApplication –](iclrruntimehost-executeapplication-method.md) pro aktivaci aplikace založené na manifestu.</span><span class="sxs-lookup"><span data-stu-id="0b40e-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="0b40e-133">Pokud `Start` je metoda volána jako první, `ExecuteApplication` volání metody se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="0b40e-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b40e-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b40e-134">Requirements</span></span>  
 <span data-ttu-id="0b40e-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b40e-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b40e-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0b40e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b40e-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b40e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b40e-138">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b40e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b40e-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b40e-139">See also</span></span>

- [<span data-ttu-id="0b40e-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="0b40e-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="0b40e-141">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="0b40e-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="0b40e-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b40e-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="0b40e-143">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b40e-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="0b40e-144">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0b40e-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0b40e-145">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="0b40e-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
