---
title: "ICLRRuntimeHost – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost
helpviewer_keywords: ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type: apiref
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 332db2680ca23f34893a6c50c5311d73838bc1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="75a2f-102">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75a2f-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="75a2f-103">Poskytuje funkce, které jsou podobné jako [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní, které jsou uvedeny v rozhraní .NET Framework verze 1, s následujícími změnami:</span><span class="sxs-lookup"><span data-stu-id="75a2f-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
-   <span data-ttu-id="75a2f-104">Přidání [sethostcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) metodu a nastavit rozhraní Řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="75a2f-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
-   <span data-ttu-id="75a2f-105">Vynechání některé metody poskytované `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="75a2f-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75a2f-106">Metody</span><span class="sxs-lookup"><span data-stu-id="75a2f-106">Methods</span></span>  
  
|<span data-ttu-id="75a2f-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-107">Method</span></span>|<span data-ttu-id="75a2f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="75a2f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75a2f-109">Executeapplication – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="75a2f-110">Používá ve scénářích nasazení na základě manifest ClickOnce pro zadání aplikací, které chcete aktivovat. v nové doméně.</span><span class="sxs-lookup"><span data-stu-id="75a2f-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="75a2f-111">Executeinappdomain – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="75a2f-112">Určuje <xref:System.AppDomain> ve kterém se má provést zadanou spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="75a2f-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="75a2f-113">Executeindefaultappdomain – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="75a2f-114">Vyvolá zadanou metodu zadaného typu v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="75a2f-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="75a2f-115">Getclrcontrol – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="75a2f-116">Získá ukazatele rozhraní typu [iclrcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , hostitelů můžete přizpůsobit aspekty common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="75a2f-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="75a2f-117">Getcurrentappdomainid – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="75a2f-118">Získá identifikátor číselné <xref:System.AppDomain> , právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="75a2f-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="75a2f-119">Sethostcontrol – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="75a2f-120">Nastaví rozhraní Řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="75a2f-120">Sets the host control interface.</span></span> <span data-ttu-id="75a2f-121">Je třeba volat `SetHostControl` před voláním `Start`.</span><span class="sxs-lookup"><span data-stu-id="75a2f-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="75a2f-122">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="75a2f-123">Inicializuje modulu CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="75a2f-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="75a2f-124">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="75a2f-125">Ukončí provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="75a2f-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="75a2f-126">UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="75a2f-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="75a2f-127">Uvolní <xref:System.AppDomain> , který odpovídá zadané identifikační číslo.</span><span class="sxs-lookup"><span data-stu-id="75a2f-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75a2f-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75a2f-128">Remarks</span></span>  
 <span data-ttu-id="75a2f-129">Počínaje [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], použijte [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) rozhraní získání ukazatele na [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní a pak zavolají [iclrruntimeinfo::getinterface –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) Metoda získání ukazatele na `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="75a2f-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="75a2f-130">V dřívějších verzích rozhraní .NET Framework hostitele získá ukazatel na `ICLRRuntimeHost` instance voláním [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="75a2f-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="75a2f-131">Chcete-li poskytovat implementace některé technologie, které jsou uvedeny v rozhraní .NET Framework verze 2.0, je nutné použít `ICLRRuntimeHost` místo `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="75a2f-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75a2f-132">Nevolejte [spustit](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda před voláním [executeapplication –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metoda aktivace na základě manifest aplikace.</span><span class="sxs-lookup"><span data-stu-id="75a2f-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="75a2f-133">Pokud `Start` metoda je volána nejprve `ExecuteApplication` volání metody, které se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="75a2f-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75a2f-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75a2f-134">Requirements</span></span>  
 <span data-ttu-id="75a2f-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75a2f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75a2f-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75a2f-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75a2f-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75a2f-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75a2f-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75a2f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a2f-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="75a2f-139">See Also</span></span>  
 [<span data-ttu-id="75a2f-140">Corbindtocurrentruntime – funkce</span><span class="sxs-lookup"><span data-stu-id="75a2f-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="75a2f-141">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="75a2f-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="75a2f-142">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75a2f-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="75a2f-143">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75a2f-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="75a2f-144">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="75a2f-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="75a2f-145">Clrruntimehost – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="75a2f-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
