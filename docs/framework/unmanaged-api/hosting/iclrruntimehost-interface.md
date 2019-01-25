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
ms.openlocfilehash: a3dc77cc799342ec0cd10f86d37541ec0a4d7822
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646091"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="a220a-102">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a220a-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="a220a-103">Poskytuje funkce podobné [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní v rozhraní .NET Framework verze 1, s následujícími změnami:</span><span class="sxs-lookup"><span data-stu-id="a220a-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
-   <span data-ttu-id="a220a-104">Přidání [sethostcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) metody nastavte ovládací prvek rozhraní hostitele.</span><span class="sxs-lookup"><span data-stu-id="a220a-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
-   <span data-ttu-id="a220a-105">Vynechání některé metody poskytované `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="a220a-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a220a-106">Metody</span><span class="sxs-lookup"><span data-stu-id="a220a-106">Methods</span></span>  
  
|<span data-ttu-id="a220a-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-107">Method</span></span>|<span data-ttu-id="a220a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a220a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a220a-109">ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="a220a-110">Použít ve scénářích nasazení na bázi manifest ClickOnce k určení aktivovat v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a220a-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="a220a-111">ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="a220a-112">Určuje, <xref:System.AppDomain> v, který se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a220a-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="a220a-113">ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="a220a-114">Vyvolá zadanou metodu zadaného typu v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="a220a-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="a220a-115">GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="a220a-116">Získá ukazatel rozhraní typu [iclrcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , hostitelů můžete použít k přizpůsobení aspekty modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a220a-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="a220a-117">GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="a220a-118">Získá číselný identifikátor <xref:System.AppDomain> , který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="a220a-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="a220a-119">SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="a220a-120">Nastaví ovládací prvek rozhraní hostitele.</span><span class="sxs-lookup"><span data-stu-id="a220a-120">Sets the host control interface.</span></span> <span data-ttu-id="a220a-121">Je nutné volat `SetHostControl` před voláním `Start`.</span><span class="sxs-lookup"><span data-stu-id="a220a-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="a220a-122">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="a220a-123">Inicializuje modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="a220a-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="a220a-124">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="a220a-125">Zastaví provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="a220a-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="a220a-126">UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="a220a-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="a220a-127">Uvolní <xref:System.AppDomain> , který odpovídá zadané číselný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="a220a-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a220a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a220a-128">Remarks</span></span>  
 <span data-ttu-id="a220a-129">Počínaje [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], použijte [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) rozhraní pro získání ukazatele na [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní a následně zavolat [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodu k získání ukazatele na `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="a220a-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="a220a-130">V dřívějších verzích rozhraní .NET Framework, hostitel získá ukazatel `ICLRRuntimeHost` instance voláním [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="a220a-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="a220a-131">Chcete-li poskytnout implementace některého z technologie v rozhraní .NET Framework verze 2.0, je nutné použít `ICLRRuntimeHost` místo `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="a220a-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a220a-132">Nevolejte [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním metody [executeapplication –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metodu aktivace manifest aplikace.</span><span class="sxs-lookup"><span data-stu-id="a220a-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="a220a-133">Pokud `Start` metoda je volána nejprve `ExecuteApplication` volání metody se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="a220a-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a220a-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a220a-134">Requirements</span></span>  
 <span data-ttu-id="a220a-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a220a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a220a-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a220a-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a220a-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a220a-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a220a-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a220a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a220a-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a220a-139">See also</span></span>
- [<span data-ttu-id="a220a-140">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="a220a-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="a220a-141">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="a220a-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="a220a-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a220a-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a220a-143">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a220a-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="a220a-144">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a220a-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a220a-145">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="a220a-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
