---
title: "CorDebugInterfaceVersion – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b5d28e6def34c9263d519c2eeb9cc432656bd1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="83858-102">CorDebugInterfaceVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="83858-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="83858-103">Určuje rozhraní, verze rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve kterém byla zavedena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="83858-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83858-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83858-104">Syntax</span></span>  
  
```  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo   
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot   
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="83858-105">Členové</span><span class="sxs-lookup"><span data-stu-id="83858-105">Members</span></span>  
 <span data-ttu-id="83858-106">Následující tabulka obsahuje odkazy od každé hodnoty výčtu odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="83858-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="83858-107">Kromě toho tabulka udává první verzi rozhraní .NET Framework, který rozhraní je podporován v.</span><span class="sxs-lookup"><span data-stu-id="83858-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="83858-108">Člen</span><span class="sxs-lookup"><span data-stu-id="83858-108">Member</span></span>|<span data-ttu-id="83858-109">Určuje</span><span class="sxs-lookup"><span data-stu-id="83858-109">Specifies</span></span>|<span data-ttu-id="83858-110">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="83858-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="83858-111">Verze rozhraní .NET Framework je neplatný.</span><span class="sxs-lookup"><span data-stu-id="83858-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="83858-112">Verze rozhraní .NET Framework, včetně všech jeho aktualizace service Pack, je 1.0.</span><span class="sxs-lookup"><span data-stu-id="83858-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="83858-113">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="83858-114">Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 1.1.</span><span class="sxs-lookup"><span data-stu-id="83858-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="83858-115">1.1</span><span class="sxs-lookup"><span data-stu-id="83858-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="83858-116">Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 2.0.</span><span class="sxs-lookup"><span data-stu-id="83858-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="83858-117">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="83858-118">Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 4.</span><span class="sxs-lookup"><span data-stu-id="83858-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="83858-119">4</span><span class="sxs-lookup"><span data-stu-id="83858-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="83858-120">Verze rozhraní .NET Framework, včetně všech aktualizací service Pack, je 4.5.</span><span class="sxs-lookup"><span data-stu-id="83858-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="83858-121">4.5</span><span class="sxs-lookup"><span data-stu-id="83858-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="83858-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="83858-122">ICorDebugManagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|<span data-ttu-id="83858-123">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="83858-124">Icordebugunmanagedcallback –</span><span class="sxs-lookup"><span data-stu-id="83858-124">ICorDebugUnmanagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|<span data-ttu-id="83858-125">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="83858-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="83858-126">ICorDebug</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|<span data-ttu-id="83858-127">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="83858-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="83858-128">ICorDebugController</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|<span data-ttu-id="83858-129">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="83858-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="83858-130">ICorDebugAppDomain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|<span data-ttu-id="83858-131">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="83858-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="83858-132">ICorDebugAssembly</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|<span data-ttu-id="83858-133">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="83858-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="83858-134">ICorDebugProcess</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|<span data-ttu-id="83858-135">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="83858-136">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="83858-136">ICorDebugBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|<span data-ttu-id="83858-137">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="83858-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="83858-138">ICorDebugFunctionBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="83858-139">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="83858-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="83858-140">ICorDebugModuleBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="83858-141">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="83858-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="83858-142">ICorDebugValueBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="83858-143">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="83858-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="83858-144">ICorDebugStepper</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|<span data-ttu-id="83858-145">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="83858-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="83858-146">ICorDebugRegisterSet</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|<span data-ttu-id="83858-147">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="83858-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="83858-148">ICorDebugThread</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|<span data-ttu-id="83858-149">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="83858-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="83858-150">ICorDebugChain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|<span data-ttu-id="83858-151">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="83858-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="83858-152">ICorDebugFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|<span data-ttu-id="83858-153">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="83858-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="83858-154">ICorDebugILFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|<span data-ttu-id="83858-155">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="83858-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="83858-156">ICorDebugNativeFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|<span data-ttu-id="83858-157">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="83858-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="83858-158">ICorDebugModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|<span data-ttu-id="83858-159">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="83858-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="83858-160">ICorDebugFunction</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|<span data-ttu-id="83858-161">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="83858-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="83858-162">ICorDebugCode</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|<span data-ttu-id="83858-163">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="83858-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="83858-164">ICorDebugClass</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|<span data-ttu-id="83858-165">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="83858-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="83858-166">ICorDebugEval</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|<span data-ttu-id="83858-167">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="83858-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="83858-168">ICorDebugValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|<span data-ttu-id="83858-169">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="83858-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="83858-170">ICorDebugGenericValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|<span data-ttu-id="83858-171">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="83858-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="83858-172">ICorDebugReferenceValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|<span data-ttu-id="83858-173">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="83858-174">Icordebugheapvalue –</span><span class="sxs-lookup"><span data-stu-id="83858-174">ICorDebugHeapValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|<span data-ttu-id="83858-175">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="83858-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="83858-176">ICorDebugObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|<span data-ttu-id="83858-177">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="83858-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="83858-178">ICorDebugBoxValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|<span data-ttu-id="83858-179">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="83858-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="83858-180">ICorDebugStringValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|<span data-ttu-id="83858-181">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="83858-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="83858-182">ICorDebugArrayValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|<span data-ttu-id="83858-183">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="83858-184">Icordebugcontext –</span><span class="sxs-lookup"><span data-stu-id="83858-184">ICorDebugContext</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|<span data-ttu-id="83858-185">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="83858-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="83858-186">ICorDebugEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|<span data-ttu-id="83858-187">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="83858-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="83858-188">ICorDebugObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|<span data-ttu-id="83858-189">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="83858-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="83858-190">ICorDebugBreakpointEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|<span data-ttu-id="83858-191">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="83858-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="83858-192">ICorDebugStepperEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|<span data-ttu-id="83858-193">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="83858-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="83858-194">ICorDebugProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|<span data-ttu-id="83858-195">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="83858-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="83858-196">ICorDebugThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|<span data-ttu-id="83858-197">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="83858-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="83858-198">ICorDebugFrameEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|<span data-ttu-id="83858-199">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="83858-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="83858-200">ICorDebugChainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|<span data-ttu-id="83858-201">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="83858-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="83858-202">ICorDebugModuleEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|<span data-ttu-id="83858-203">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="83858-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="83858-204">ICorDebugValueEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|<span data-ttu-id="83858-205">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="83858-206">Icordebugcodeenum –</span><span class="sxs-lookup"><span data-stu-id="83858-206">ICorDebugCodeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|<span data-ttu-id="83858-207">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="83858-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="83858-208">ICorDebugTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|<span data-ttu-id="83858-209">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="83858-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="83858-210">ICorDebugErrorInfoEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|<span data-ttu-id="83858-211">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="83858-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="83858-212">ICorDebugAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|<span data-ttu-id="83858-213">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="83858-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="83858-214">ICorDebugAssemblyEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|<span data-ttu-id="83858-215">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="83858-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="83858-216">ICorDebugEditAndContinueErrorInfo</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="83858-217">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="83858-218">Icordebugeditandcontinuesnapshot –</span><span class="sxs-lookup"><span data-stu-id="83858-218">ICorDebugEditAndContinueSnapshot</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="83858-219">1.0</span><span class="sxs-lookup"><span data-stu-id="83858-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="83858-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="83858-220">ICorDebugManagedCallback2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|<span data-ttu-id="83858-221">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="83858-222">Icordebugappdomain2 –</span><span class="sxs-lookup"><span data-stu-id="83858-222">ICorDebugAppDomain2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|<span data-ttu-id="83858-223">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="83858-224">Icordebugprocess2 –</span><span class="sxs-lookup"><span data-stu-id="83858-224">ICorDebugProcess2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|<span data-ttu-id="83858-225">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="83858-226">Icordebugstepper2 –</span><span class="sxs-lookup"><span data-stu-id="83858-226">ICorDebugStepper2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|<span data-ttu-id="83858-227">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="83858-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="83858-228">ICorDebugRegisterSet2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|<span data-ttu-id="83858-229">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="83858-230">Icordebugthread2 –</span><span class="sxs-lookup"><span data-stu-id="83858-230">ICorDebugThread2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|<span data-ttu-id="83858-231">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="83858-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="83858-232">ICorDebugILFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|<span data-ttu-id="83858-233">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="83858-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="83858-234">ICorDebugModule2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|<span data-ttu-id="83858-235">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="83858-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="83858-236">ICorDebugFunction2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|<span data-ttu-id="83858-237">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="83858-238">Icordebugcode2 –</span><span class="sxs-lookup"><span data-stu-id="83858-238">ICorDebugCode2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|<span data-ttu-id="83858-239">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="83858-240">"ICorDebugClass2"</span><span class="sxs-lookup"><span data-stu-id="83858-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="83858-241">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="83858-242">Icordebugvalue2 "–"</span><span class="sxs-lookup"><span data-stu-id="83858-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="83858-243">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="83858-244">"ICorDebugEval2".</span><span class="sxs-lookup"><span data-stu-id="83858-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="83858-245">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="83858-246">Icordebugobjectvalue2 "–"</span><span class="sxs-lookup"><span data-stu-id="83858-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="83858-247">2.0</span><span class="sxs-lookup"><span data-stu-id="83858-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="83858-248">Icordebugthread3 –</span><span class="sxs-lookup"><span data-stu-id="83858-248">ICorDebugThread3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|<span data-ttu-id="83858-249">4</span><span class="sxs-lookup"><span data-stu-id="83858-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="83858-250">Icordebugthread4 –</span><span class="sxs-lookup"><span data-stu-id="83858-250">ICorDebugThread4</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|<span data-ttu-id="83858-251">4</span><span class="sxs-lookup"><span data-stu-id="83858-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="83858-252">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="83858-252">ICorDebugStackWalk</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|<span data-ttu-id="83858-253">4</span><span class="sxs-lookup"><span data-stu-id="83858-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="83858-254">Icordebugnativeframe2 –</span><span class="sxs-lookup"><span data-stu-id="83858-254">ICorDebugNativeFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|<span data-ttu-id="83858-255">4</span><span class="sxs-lookup"><span data-stu-id="83858-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="83858-256">Icordebuginternalframe2 –</span><span class="sxs-lookup"><span data-stu-id="83858-256">ICorDebugInternalFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|<span data-ttu-id="83858-257">4</span><span class="sxs-lookup"><span data-stu-id="83858-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="83858-258">Icordebugruntimeunwindableframe –</span><span class="sxs-lookup"><span data-stu-id="83858-258">ICorDebugRuntimeUnwindableFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="83858-259">4</span><span class="sxs-lookup"><span data-stu-id="83858-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="83858-260">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83858-260">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|<span data-ttu-id="83858-261">4</span><span class="sxs-lookup"><span data-stu-id="83858-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="83858-262">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83858-262">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|<span data-ttu-id="83858-263">4</span><span class="sxs-lookup"><span data-stu-id="83858-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="83858-264">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="83858-264">ICorDebugValue3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|<span data-ttu-id="83858-265">4</span><span class="sxs-lookup"><span data-stu-id="83858-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="83858-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="83858-266">ICorDebugComObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|<span data-ttu-id="83858-267">4.5</span><span class="sxs-lookup"><span data-stu-id="83858-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="83858-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="83858-268">ICorDebugAppDomain3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|<span data-ttu-id="83858-269">4.5</span><span class="sxs-lookup"><span data-stu-id="83858-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="83858-270">Icordebugcode3 –</span><span class="sxs-lookup"><span data-stu-id="83858-270">ICorDebugCode3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|<span data-ttu-id="83858-271">4.5</span><span class="sxs-lookup"><span data-stu-id="83858-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="83858-272">Icordebugilframe3 –</span><span class="sxs-lookup"><span data-stu-id="83858-272">ICorDebugILFrame3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|<span data-ttu-id="83858-273">4.5</span><span class="sxs-lookup"><span data-stu-id="83858-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="83858-274">Verze rozhraní .NET Framework, včetně všech jeho aktualizace service Pack, je na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="83858-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="83858-275">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83858-275">Remarks</span></span>  
 <span data-ttu-id="83858-276">Ladicí program můžete použít `CorDebugInterfaceVersion` výčet ve [createdebugginginterfacefromversion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkce určit nejvyšší verzi rozhraní .NET Framework, který podporuje ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="83858-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="83858-277">Názvy rozhraní</span><span class="sxs-lookup"><span data-stu-id="83858-277">Interface Names</span></span>  
 <span data-ttu-id="83858-278">Číslo, které se zobrazí na konci rozhraní názvů v rozhraní API pro ladění (například "3" v `ICorDebugThread3`) určuje verzi rozhraní, nikoli na verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83858-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="83858-279">Názvy všech rozhraní v rozhraní API pro ladění obsahují čísla verzí, s výjimkou rozhraní, které byly zavedeny v rozhraní .NET Framework verze 1.</span><span class="sxs-lookup"><span data-stu-id="83858-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="83858-280">Všechny propojeni čísla verzí rozhraní verze čísla and.NET Framework je náhodný.</span><span class="sxs-lookup"><span data-stu-id="83858-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
-   <span data-ttu-id="83858-281">Rozhraní, které byly zavedeny v rozhraní .NET Framework verze 1.0 nebudou obsahovat čísla, protože jsou všechny implicitně verze 1.</span><span class="sxs-lookup"><span data-stu-id="83858-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
-   <span data-ttu-id="83858-282">Rozhraní .NET Framework verze 1.1 používá verzi 1.0 rozhraní a nezavádí žádné nové ladění rozhraní.</span><span class="sxs-lookup"><span data-stu-id="83858-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
-   <span data-ttu-id="83858-283">14 ladění rozhraní byla zavedená v rozhraní .NET Framework verze 2.0 jsou logické rozšíření jejich verze 1 svými protějšky a zahrnout číslo "2" do jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="83858-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
-   <span data-ttu-id="83858-284">Verze rozhraní .NET Framework 3.0 a 3.5 použít existující rozhraní .NET Framework 2.0 a Nezavádět žádné nové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="83858-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
-   <span data-ttu-id="83858-285">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Zavádí směs verze rozhraní.</span><span class="sxs-lookup"><span data-stu-id="83858-285">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] introduces a mix of interface versions.</span></span> <span data-ttu-id="83858-286">Například pro obě `ICorDebugThread3` a `ICorDebugThread4` zobrazí jako verze třetí a čtvrtý `ICorDebugThread` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="83858-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="83858-287">[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Také představuje první verzi `ICorDebugStackWalk` rozhraní a druhá verze `ICorDebugNativeFrame` rozhraní (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="83858-287">The [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83858-288">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83858-288">Requirements</span></span>  
 <span data-ttu-id="83858-289">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83858-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83858-290">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83858-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83858-291">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83858-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83858-292">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83858-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83858-293">Viz také</span><span class="sxs-lookup"><span data-stu-id="83858-293">See Also</span></span>  
 [<span data-ttu-id="83858-294">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="83858-294">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
