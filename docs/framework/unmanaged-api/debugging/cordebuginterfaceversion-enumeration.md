---
title: CorDebugInterfaceVersion – výčet
ms.date: 03/30/2017
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
ms.openlocfilehash: cfdcfc69400fccf824d019f3904aeca76b6b37a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098132"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="b85cf-102">CorDebugInterfaceVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="b85cf-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="b85cf-103">Určuje rozhraní, verzi .NET Framework nebo verzi .NET Framework, ve které bylo rozhraní zavedeno.</span><span class="sxs-lookup"><span data-stu-id="b85cf-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b85cf-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="b85cf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b85cf-105">Members</span></span>  
 <span data-ttu-id="b85cf-106">Následující tabulka obsahuje odkazy z každé hodnoty výčtu na odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b85cf-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="b85cf-107">Kromě toho tabulka indikuje první verzi .NET Framework, v níž bylo rozhraní podporováno.</span><span class="sxs-lookup"><span data-stu-id="b85cf-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="b85cf-108">Člen</span><span class="sxs-lookup"><span data-stu-id="b85cf-108">Member</span></span>|<span data-ttu-id="b85cf-109">Určuje</span><span class="sxs-lookup"><span data-stu-id="b85cf-109">Specifies</span></span>|<span data-ttu-id="b85cf-110">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b85cf-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="b85cf-111">Verze .NET Framework není platná.</span><span class="sxs-lookup"><span data-stu-id="b85cf-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="b85cf-112">Verze .NET Framework, včetně všech aktualizací Service Pack, je 1,0.</span><span class="sxs-lookup"><span data-stu-id="b85cf-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="b85cf-113">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="b85cf-114">Verze .NET Framework, včetně všech aktualizací Service Pack, je 1,1.</span><span class="sxs-lookup"><span data-stu-id="b85cf-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="b85cf-115">1.1</span><span class="sxs-lookup"><span data-stu-id="b85cf-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="b85cf-116">Verze .NET Framework, včetně všech aktualizací Service Pack, je 2,0.</span><span class="sxs-lookup"><span data-stu-id="b85cf-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="b85cf-117">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="b85cf-118">Verze .NET Framework, včetně všech aktualizací Service Pack, je 4.</span><span class="sxs-lookup"><span data-stu-id="b85cf-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="b85cf-119">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="b85cf-120">Verze .NET Framework, včetně všech aktualizací Service Pack, je 4,5.</span><span class="sxs-lookup"><span data-stu-id="b85cf-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="b85cf-121">4.5</span><span class="sxs-lookup"><span data-stu-id="b85cf-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="b85cf-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b85cf-122">ICorDebugManagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|<span data-ttu-id="b85cf-123">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="b85cf-124">ICorDebugUnmanagedCallback –</span><span class="sxs-lookup"><span data-stu-id="b85cf-124">ICorDebugUnmanagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|<span data-ttu-id="b85cf-125">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="b85cf-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="b85cf-126">ICorDebug</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|<span data-ttu-id="b85cf-127">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="b85cf-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="b85cf-128">ICorDebugController</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|<span data-ttu-id="b85cf-129">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="b85cf-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="b85cf-130">ICorDebugAppDomain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|<span data-ttu-id="b85cf-131">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="b85cf-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="b85cf-132">ICorDebugAssembly</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|<span data-ttu-id="b85cf-133">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="b85cf-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="b85cf-134">ICorDebugProcess</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|<span data-ttu-id="b85cf-135">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="b85cf-136">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b85cf-136">ICorDebugBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|<span data-ttu-id="b85cf-137">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="b85cf-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b85cf-138">ICorDebugFunctionBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="b85cf-139">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="b85cf-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b85cf-140">ICorDebugModuleBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="b85cf-141">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="b85cf-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b85cf-142">ICorDebugValueBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="b85cf-143">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="b85cf-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="b85cf-144">ICorDebugStepper</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|<span data-ttu-id="b85cf-145">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="b85cf-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="b85cf-146">ICorDebugRegisterSet</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|<span data-ttu-id="b85cf-147">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="b85cf-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="b85cf-148">ICorDebugThread</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|<span data-ttu-id="b85cf-149">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="b85cf-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="b85cf-150">ICorDebugChain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|<span data-ttu-id="b85cf-151">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="b85cf-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="b85cf-152">ICorDebugFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|<span data-ttu-id="b85cf-153">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="b85cf-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="b85cf-154">ICorDebugILFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|<span data-ttu-id="b85cf-155">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="b85cf-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="b85cf-156">ICorDebugNativeFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|<span data-ttu-id="b85cf-157">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="b85cf-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="b85cf-158">ICorDebugModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|<span data-ttu-id="b85cf-159">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="b85cf-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="b85cf-160">ICorDebugFunction</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|<span data-ttu-id="b85cf-161">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="b85cf-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="b85cf-162">ICorDebugCode</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|<span data-ttu-id="b85cf-163">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="b85cf-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="b85cf-164">ICorDebugClass</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|<span data-ttu-id="b85cf-165">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="b85cf-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="b85cf-166">ICorDebugEval</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|<span data-ttu-id="b85cf-167">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="b85cf-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-168">ICorDebugValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|<span data-ttu-id="b85cf-169">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="b85cf-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-170">ICorDebugGenericValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|<span data-ttu-id="b85cf-171">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="b85cf-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-172">ICorDebugReferenceValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|<span data-ttu-id="b85cf-173">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="b85cf-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-174">ICorDebugHeapValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|<span data-ttu-id="b85cf-175">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="b85cf-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-176">ICorDebugObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|<span data-ttu-id="b85cf-177">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="b85cf-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-178">ICorDebugBoxValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|<span data-ttu-id="b85cf-179">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="b85cf-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-180">ICorDebugStringValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|<span data-ttu-id="b85cf-181">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="b85cf-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-182">ICorDebugArrayValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|<span data-ttu-id="b85cf-183">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="b85cf-184">ICorDebugContext –</span><span class="sxs-lookup"><span data-stu-id="b85cf-184">ICorDebugContext</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|<span data-ttu-id="b85cf-185">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="b85cf-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-186">ICorDebugEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|<span data-ttu-id="b85cf-187">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="b85cf-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-188">ICorDebugObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|<span data-ttu-id="b85cf-189">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="b85cf-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-190">ICorDebugBreakpointEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|<span data-ttu-id="b85cf-191">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="b85cf-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-192">ICorDebugStepperEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|<span data-ttu-id="b85cf-193">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="b85cf-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-194">ICorDebugProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|<span data-ttu-id="b85cf-195">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="b85cf-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-196">ICorDebugThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|<span data-ttu-id="b85cf-197">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="b85cf-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-198">ICorDebugFrameEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|<span data-ttu-id="b85cf-199">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="b85cf-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-200">ICorDebugChainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|<span data-ttu-id="b85cf-201">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="b85cf-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-202">ICorDebugModuleEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|<span data-ttu-id="b85cf-203">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="b85cf-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-204">ICorDebugValueEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|<span data-ttu-id="b85cf-205">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="b85cf-206">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-206">ICorDebugCodeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|<span data-ttu-id="b85cf-207">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="b85cf-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-208">ICorDebugTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|<span data-ttu-id="b85cf-209">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="b85cf-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-210">ICorDebugErrorInfoEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|<span data-ttu-id="b85cf-211">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="b85cf-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-212">ICorDebugAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|<span data-ttu-id="b85cf-213">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="b85cf-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="b85cf-214">ICorDebugAssemblyEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|<span data-ttu-id="b85cf-215">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="b85cf-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="b85cf-216">ICorDebugEditAndContinueErrorInfo</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="b85cf-217">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="b85cf-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="b85cf-218">ICorDebugEditAndContinueSnapshot</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="b85cf-219">1.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="b85cf-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="b85cf-220">ICorDebugManagedCallback2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|<span data-ttu-id="b85cf-221">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="b85cf-222">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="b85cf-222">ICorDebugAppDomain2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|<span data-ttu-id="b85cf-223">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="b85cf-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="b85cf-224">ICorDebugProcess2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|<span data-ttu-id="b85cf-225">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="b85cf-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="b85cf-226">ICorDebugStepper2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|<span data-ttu-id="b85cf-227">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="b85cf-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="b85cf-228">ICorDebugRegisterSet2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|<span data-ttu-id="b85cf-229">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="b85cf-230">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="b85cf-230">ICorDebugThread2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|<span data-ttu-id="b85cf-231">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="b85cf-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="b85cf-232">ICorDebugILFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|<span data-ttu-id="b85cf-233">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="b85cf-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="b85cf-234">ICorDebugModule2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|<span data-ttu-id="b85cf-235">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="b85cf-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="b85cf-236">ICorDebugFunction2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|<span data-ttu-id="b85cf-237">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="b85cf-238">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="b85cf-238">ICorDebugCode2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|<span data-ttu-id="b85cf-239">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="b85cf-240">ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="b85cf-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="b85cf-241">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="b85cf-242">ICorDebugValue2</span><span class="sxs-lookup"><span data-stu-id="b85cf-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="b85cf-243">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="b85cf-244">"ICorDebugEval2".</span><span class="sxs-lookup"><span data-stu-id="b85cf-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="b85cf-245">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="b85cf-246">ICorDebugObjectValue2</span><span class="sxs-lookup"><span data-stu-id="b85cf-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="b85cf-247">2.0</span><span class="sxs-lookup"><span data-stu-id="b85cf-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="b85cf-248">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="b85cf-248">ICorDebugThread3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|<span data-ttu-id="b85cf-249">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="b85cf-250">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="b85cf-250">ICorDebugThread4</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|<span data-ttu-id="b85cf-251">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="b85cf-252">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="b85cf-252">ICorDebugStackWalk</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|<span data-ttu-id="b85cf-253">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="b85cf-254">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="b85cf-254">ICorDebugNativeFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|<span data-ttu-id="b85cf-255">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="b85cf-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="b85cf-256">ICorDebugInternalFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|<span data-ttu-id="b85cf-257">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="b85cf-258">ICorDebugRuntimeUnwindableFrame –</span><span class="sxs-lookup"><span data-stu-id="b85cf-258">ICorDebugRuntimeUnwindableFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="b85cf-259">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="b85cf-260">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b85cf-260">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|<span data-ttu-id="b85cf-261">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="b85cf-262">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b85cf-262">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|<span data-ttu-id="b85cf-263">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="b85cf-264">Icordebugvalue3 –</span><span class="sxs-lookup"><span data-stu-id="b85cf-264">ICorDebugValue3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|<span data-ttu-id="b85cf-265">4</span><span class="sxs-lookup"><span data-stu-id="b85cf-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="b85cf-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="b85cf-266">ICorDebugComObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|<span data-ttu-id="b85cf-267">4.5</span><span class="sxs-lookup"><span data-stu-id="b85cf-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="b85cf-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="b85cf-268">ICorDebugAppDomain3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|<span data-ttu-id="b85cf-269">4.5</span><span class="sxs-lookup"><span data-stu-id="b85cf-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="b85cf-270">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="b85cf-270">ICorDebugCode3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|<span data-ttu-id="b85cf-271">4.5</span><span class="sxs-lookup"><span data-stu-id="b85cf-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="b85cf-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="b85cf-272">ICorDebugILFrame3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|<span data-ttu-id="b85cf-273">4.5</span><span class="sxs-lookup"><span data-stu-id="b85cf-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="b85cf-274">Verze .NET Framework, včetně všech aktualizací Service Pack, je nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="b85cf-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="b85cf-275">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b85cf-275">Remarks</span></span>  
 <span data-ttu-id="b85cf-276">Ladicí program může použít výčet `CorDebugInterfaceVersion` ve funkci [CreateDebuggingInterfaceFromVersion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) k určení nejvyšší verze .NET Framework, kterou ladicí program podporuje.</span><span class="sxs-lookup"><span data-stu-id="b85cf-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="b85cf-277">Názvy rozhraní</span><span class="sxs-lookup"><span data-stu-id="b85cf-277">Interface Names</span></span>  
 <span data-ttu-id="b85cf-278">Číslo, které se zobrazí na konci názvů rozhraní v rozhraní API pro ladění (například "3" v `ICorDebugThread3`) určuje verzi rozhraní, nikoli verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b85cf-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="b85cf-279">Všechny názvy rozhraní v rozhraní API pro ladění obsahují čísla verzí kromě rozhraní zavedených ve verzi .NET Framework 1.</span><span class="sxs-lookup"><span data-stu-id="b85cf-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="b85cf-280">Jakékoli korespondence mezi čísly verzí rozhraní and.NET čísly verze Frameworku jsou koincidenty.</span><span class="sxs-lookup"><span data-stu-id="b85cf-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="b85cf-281">Rozhraní, která byla představena ve .NET Framework verze 1,0, neobsahují čísla, protože jsou implicitně verze 1.</span><span class="sxs-lookup"><span data-stu-id="b85cf-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="b85cf-282">.NET Framework verze 1,1 používá rozhraní verze 1,0 a nezavádí žádná nová rozhraní ladění.</span><span class="sxs-lookup"><span data-stu-id="b85cf-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="b85cf-283">Rozhraní pro ladění 14 představená ve verzi .NET Framework 2,0 jsou logická rozšíření jejich protějšků verze 1 a v názvech obsahují číslo "2".</span><span class="sxs-lookup"><span data-stu-id="b85cf-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="b85cf-284">.NET Framework verze 3,0 a 3,5 používají existující rozhraní .NET Framework 2,0 a nezavádí žádná nová rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b85cf-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="b85cf-285">.NET Framework 4 zavádí kombinaci verzí rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b85cf-285">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="b85cf-286">Například `ICorDebugThread3` a `ICorDebugThread4` se zobrazí jako třetí a čtvrtá verze rozhraní `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="b85cf-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="b85cf-287">.NET Framework 4 také zavádí první verzi rozhraní `ICorDebugStackWalk` a druhou verzi `ICorDebugNativeFrame` rozhraní (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="b85cf-287">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b85cf-288">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b85cf-288">Requirements</span></span>  
 <span data-ttu-id="b85cf-289">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b85cf-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b85cf-290">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b85cf-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b85cf-291">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b85cf-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b85cf-292">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b85cf-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85cf-293">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b85cf-293">See also</span></span>

- [<span data-ttu-id="b85cf-294">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="b85cf-294">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
