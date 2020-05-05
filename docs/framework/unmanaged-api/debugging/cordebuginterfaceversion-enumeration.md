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
ms.openlocfilehash: ae65c60440a90959006cd8db94dda479e80613d4
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795804"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="7de4f-102">CorDebugInterfaceVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="7de4f-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="7de4f-103">Určuje rozhraní, verzi .NET Framework nebo verzi .NET Framework, ve které bylo rozhraní zavedeno.</span><span class="sxs-lookup"><span data-stu-id="7de4f-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7de4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7de4f-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7de4f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7de4f-105">Members</span></span>  
 <span data-ttu-id="7de4f-106">Následující tabulka obsahuje odkazy z každé hodnoty výčtu na odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7de4f-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="7de4f-107">Kromě toho tabulka indikuje první verzi .NET Framework, v níž bylo rozhraní podporováno.</span><span class="sxs-lookup"><span data-stu-id="7de4f-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="7de4f-108">Člen</span><span class="sxs-lookup"><span data-stu-id="7de4f-108">Member</span></span>|<span data-ttu-id="7de4f-109">Určuje</span><span class="sxs-lookup"><span data-stu-id="7de4f-109">Specifies</span></span>|<span data-ttu-id="7de4f-110">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7de4f-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="7de4f-111">Verze .NET Framework není platná.</span><span class="sxs-lookup"><span data-stu-id="7de4f-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="7de4f-112">Verze .NET Framework, včetně všech aktualizací Service Pack, je 1,0.</span><span class="sxs-lookup"><span data-stu-id="7de4f-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="7de4f-113">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="7de4f-114">Verze .NET Framework, včetně všech aktualizací Service Pack, je 1,1.</span><span class="sxs-lookup"><span data-stu-id="7de4f-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="7de4f-115">1.1</span><span class="sxs-lookup"><span data-stu-id="7de4f-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="7de4f-116">Verze .NET Framework, včetně všech aktualizací Service Pack, je 2,0.</span><span class="sxs-lookup"><span data-stu-id="7de4f-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="7de4f-117">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="7de4f-118">Verze .NET Framework, včetně všech aktualizací Service Pack, je 4.</span><span class="sxs-lookup"><span data-stu-id="7de4f-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="7de4f-119">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="7de4f-120">Verze .NET Framework, včetně všech aktualizací Service Pack, je 4,5.</span><span class="sxs-lookup"><span data-stu-id="7de4f-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="7de4f-121">4.5</span><span class="sxs-lookup"><span data-stu-id="7de4f-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="7de4f-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="7de4f-122">ICorDebugManagedCallback</span></span>](icordebugmanagedcallback-interface.md)|<span data-ttu-id="7de4f-123">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="7de4f-124">ICorDebugUnmanagedCallback –</span><span class="sxs-lookup"><span data-stu-id="7de4f-124">ICorDebugUnmanagedCallback</span></span>](icordebugunmanagedcallback-interface.md)|<span data-ttu-id="7de4f-125">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="7de4f-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="7de4f-126">ICorDebug</span></span>](icordebug-interface.md)|<span data-ttu-id="7de4f-127">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="7de4f-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="7de4f-128">ICorDebugController</span></span>](icordebugcontroller-interface.md)|<span data-ttu-id="7de4f-129">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="7de4f-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="7de4f-130">ICorDebugAppDomain</span></span>](icordebugappdomain-interface.md)|<span data-ttu-id="7de4f-131">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="7de4f-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="7de4f-132">ICorDebugAssembly</span></span>](icordebugassembly-interface.md)|<span data-ttu-id="7de4f-133">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="7de4f-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="7de4f-134">ICorDebugProcess</span></span>](icordebugprocess-interface.md)|<span data-ttu-id="7de4f-135">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="7de4f-136">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7de4f-136">ICorDebugBreakpoint</span></span>](icordebugbreakpoint-interface.md)|<span data-ttu-id="7de4f-137">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="7de4f-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7de4f-138">ICorDebugFunctionBreakpoint</span></span>](icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="7de4f-139">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="7de4f-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7de4f-140">ICorDebugModuleBreakpoint</span></span>](icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="7de4f-141">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="7de4f-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7de4f-142">ICorDebugValueBreakpoint</span></span>](icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="7de4f-143">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="7de4f-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="7de4f-144">ICorDebugStepper</span></span>](icordebugstepper-interface.md)|<span data-ttu-id="7de4f-145">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="7de4f-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="7de4f-146">ICorDebugRegisterSet</span></span>](icordebugregisterset-interface.md)|<span data-ttu-id="7de4f-147">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="7de4f-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="7de4f-148">ICorDebugThread</span></span>](icordebugthread-interface.md)|<span data-ttu-id="7de4f-149">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="7de4f-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="7de4f-150">ICorDebugChain</span></span>](icordebugchain-interface.md)|<span data-ttu-id="7de4f-151">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="7de4f-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="7de4f-152">ICorDebugFrame</span></span>](icordebugframe-interface.md)|<span data-ttu-id="7de4f-153">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="7de4f-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="7de4f-154">ICorDebugILFrame</span></span>](icordebugilframe-interface.md)|<span data-ttu-id="7de4f-155">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="7de4f-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="7de4f-156">ICorDebugNativeFrame</span></span>](icordebugnativeframe-interface.md)|<span data-ttu-id="7de4f-157">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="7de4f-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="7de4f-158">ICorDebugModule</span></span>](icordebugmodule-interface.md)|<span data-ttu-id="7de4f-159">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="7de4f-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="7de4f-160">ICorDebugFunction</span></span>](icordebugfunction-interface1.md)|<span data-ttu-id="7de4f-161">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="7de4f-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="7de4f-162">ICorDebugCode</span></span>](icordebugcode-interface1.md)|<span data-ttu-id="7de4f-163">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="7de4f-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="7de4f-164">ICorDebugClass</span></span>](icordebugclass-interface.md)|<span data-ttu-id="7de4f-165">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="7de4f-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="7de4f-166">ICorDebugEval</span></span>](icordebugeval-interface.md)|<span data-ttu-id="7de4f-167">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="7de4f-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-168">ICorDebugValue</span></span>](icordebugvalue-interface.md)|<span data-ttu-id="7de4f-169">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="7de4f-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-170">ICorDebugGenericValue</span></span>](icordebuggenericvalue-interface.md)|<span data-ttu-id="7de4f-171">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="7de4f-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-172">ICorDebugReferenceValue</span></span>](icordebugreferencevalue-interface.md)|<span data-ttu-id="7de4f-173">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="7de4f-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-174">ICorDebugHeapValue</span></span>](icordebugheapvalue-interface.md)|<span data-ttu-id="7de4f-175">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="7de4f-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-176">ICorDebugObjectValue</span></span>](icordebugobjectvalue-interface.md)|<span data-ttu-id="7de4f-177">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="7de4f-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-178">ICorDebugBoxValue</span></span>](icordebugboxvalue-interface.md)|<span data-ttu-id="7de4f-179">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="7de4f-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-180">ICorDebugStringValue</span></span>](icordebugstringvalue-interface.md)|<span data-ttu-id="7de4f-181">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="7de4f-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-182">ICorDebugArrayValue</span></span>](icordebugarrayvalue-interface.md)|<span data-ttu-id="7de4f-183">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="7de4f-184">ICorDebugContext –</span><span class="sxs-lookup"><span data-stu-id="7de4f-184">ICorDebugContext</span></span>](icordebugcontext-interface.md)|<span data-ttu-id="7de4f-185">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="7de4f-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-186">ICorDebugEnum</span></span>](icordebugenum-interface1.md)|<span data-ttu-id="7de4f-187">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="7de4f-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-188">ICorDebugObjectEnum</span></span>](icordebugobjectenum-interface.md)|<span data-ttu-id="7de4f-189">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="7de4f-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-190">ICorDebugBreakpointEnum</span></span>](icordebugbreakpointenum-interface.md)|<span data-ttu-id="7de4f-191">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="7de4f-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-192">ICorDebugStepperEnum</span></span>](icordebugstepperenum-interface.md)|<span data-ttu-id="7de4f-193">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="7de4f-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-194">ICorDebugProcessEnum</span></span>](icordebugprocessenum-interface.md)|<span data-ttu-id="7de4f-195">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="7de4f-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-196">ICorDebugThreadEnum</span></span>](icordebugthreadenum-interface1.md)|<span data-ttu-id="7de4f-197">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="7de4f-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-198">ICorDebugFrameEnum</span></span>](icordebugframeenum-interface.md)|<span data-ttu-id="7de4f-199">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="7de4f-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-200">ICorDebugChainEnum</span></span>](icordebugchainenum-interface.md)|<span data-ttu-id="7de4f-201">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="7de4f-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-202">ICorDebugModuleEnum</span></span>](icordebugmoduleenum-interface.md)|<span data-ttu-id="7de4f-203">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="7de4f-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-204">ICorDebugValueEnum</span></span>](icordebugvalueenum-interface.md)|<span data-ttu-id="7de4f-205">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="7de4f-206">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-206">ICorDebugCodeEnum</span></span>](icordebugcodeenum-interface.md)|<span data-ttu-id="7de4f-207">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="7de4f-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-208">ICorDebugTypeEnum</span></span>](icordebugtypeenum-interface.md)|<span data-ttu-id="7de4f-209">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="7de4f-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-210">ICorDebugErrorInfoEnum</span></span>](icordebugerrorinfoenum-interface.md)|<span data-ttu-id="7de4f-211">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="7de4f-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-212">ICorDebugAppDomainEnum</span></span>](icordebugappdomainenum-interface.md)|<span data-ttu-id="7de4f-213">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="7de4f-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="7de4f-214">ICorDebugAssemblyEnum</span></span>](icordebugassemblyenum-interface.md)|<span data-ttu-id="7de4f-215">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="7de4f-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="7de4f-216">ICorDebugEditAndContinueErrorInfo</span></span>](icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="7de4f-217">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="7de4f-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="7de4f-218">ICorDebugEditAndContinueSnapshot</span></span>](icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="7de4f-219">1.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="7de4f-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="7de4f-220">ICorDebugManagedCallback2</span></span>](icordebugmanagedcallback2-interface.md)|<span data-ttu-id="7de4f-221">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="7de4f-222">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="7de4f-222">ICorDebugAppDomain2</span></span>](icordebugappdomain2-interface.md)|<span data-ttu-id="7de4f-223">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="7de4f-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="7de4f-224">ICorDebugProcess2</span></span>](icordebugprocess2-interface1.md)|<span data-ttu-id="7de4f-225">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="7de4f-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="7de4f-226">ICorDebugStepper2</span></span>](icordebugstepper2-interface1.md)|<span data-ttu-id="7de4f-227">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="7de4f-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="7de4f-228">ICorDebugRegisterSet2</span></span>](icordebugregisterset2-interface.md)|<span data-ttu-id="7de4f-229">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="7de4f-230">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="7de4f-230">ICorDebugThread2</span></span>](icordebugthread2-interface.md)|<span data-ttu-id="7de4f-231">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="7de4f-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="7de4f-232">ICorDebugILFrame2</span></span>](icordebugilframe2-interface.md)|<span data-ttu-id="7de4f-233">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="7de4f-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="7de4f-234">ICorDebugModule2</span></span>](icordebugmodule2-interface.md)|<span data-ttu-id="7de4f-235">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="7de4f-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="7de4f-236">ICorDebugFunction2</span></span>](icordebugfunction2-interface.md)|<span data-ttu-id="7de4f-237">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="7de4f-238">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="7de4f-238">ICorDebugCode2</span></span>](icordebugcode2-interface.md)|<span data-ttu-id="7de4f-239">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="7de4f-240">ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="7de4f-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="7de4f-241">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="7de4f-242">ICorDebugValue2</span><span class="sxs-lookup"><span data-stu-id="7de4f-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="7de4f-243">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="7de4f-244">"ICorDebugEval2".</span><span class="sxs-lookup"><span data-stu-id="7de4f-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="7de4f-245">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="7de4f-246">ICorDebugObjectValue2</span><span class="sxs-lookup"><span data-stu-id="7de4f-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="7de4f-247">2.0</span><span class="sxs-lookup"><span data-stu-id="7de4f-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="7de4f-248">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="7de4f-248">ICorDebugThread3</span></span>](icordebugthread3-interface.md)|<span data-ttu-id="7de4f-249">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="7de4f-250">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="7de4f-250">ICorDebugThread4</span></span>](icordebugthread4-interface.md)|<span data-ttu-id="7de4f-251">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="7de4f-252">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="7de4f-252">ICorDebugStackWalk</span></span>](icordebugstackwalk-interface.md)|<span data-ttu-id="7de4f-253">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="7de4f-254">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="7de4f-254">ICorDebugNativeFrame2</span></span>](icordebugnativeframe2-interface.md)|<span data-ttu-id="7de4f-255">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="7de4f-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="7de4f-256">ICorDebugInternalFrame2</span></span>](icordebuginternalframe2-interface.md)|<span data-ttu-id="7de4f-257">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="7de4f-258">ICorDebugRuntimeUnwindableFrame –</span><span class="sxs-lookup"><span data-stu-id="7de4f-258">ICorDebugRuntimeUnwindableFrame</span></span>](icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="7de4f-259">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="7de4f-260">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7de4f-260">ICorDebugHeapValue3 Interface</span></span>](icordebugheapvalue3-interface.md)|<span data-ttu-id="7de4f-261">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="7de4f-262">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7de4f-262">ICorDebugBlockingObjectEnum Interface</span></span>](icordebugblockingobjectenum-interface.md)|<span data-ttu-id="7de4f-263">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="7de4f-264">Icordebugvalue3 –</span><span class="sxs-lookup"><span data-stu-id="7de4f-264">ICorDebugValue3</span></span>](icordebugvalue3-interface.md)|<span data-ttu-id="7de4f-265">4</span><span class="sxs-lookup"><span data-stu-id="7de4f-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="7de4f-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="7de4f-266">ICorDebugComObjectValue</span></span>](icordebugcomobjectvalue-interface.md)|<span data-ttu-id="7de4f-267">4.5</span><span class="sxs-lookup"><span data-stu-id="7de4f-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="7de4f-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="7de4f-268">ICorDebugAppDomain3</span></span>](icordebugappdomain3-interface.md)|<span data-ttu-id="7de4f-269">4.5</span><span class="sxs-lookup"><span data-stu-id="7de4f-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="7de4f-270">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="7de4f-270">ICorDebugCode3</span></span>](icordebugcode3-interface.md)|<span data-ttu-id="7de4f-271">4.5</span><span class="sxs-lookup"><span data-stu-id="7de4f-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="7de4f-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="7de4f-272">ICorDebugILFrame3</span></span>](icordebugilframe3-interface.md)|<span data-ttu-id="7de4f-273">4.5</span><span class="sxs-lookup"><span data-stu-id="7de4f-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="7de4f-274">Verze .NET Framework, včetně všech aktualizací Service Pack, je nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="7de4f-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="7de4f-275">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7de4f-275">Remarks</span></span>  
 <span data-ttu-id="7de4f-276">Ladicí program může pomocí `CorDebugInterfaceVersion` výčtu ve funkci [CreateDebuggingInterfaceFromVersion –](../hosting/createdebugginginterfacefromversion-function.md) určit nejvyšší verzi .NET Framework, kterou ladicí program podporuje.</span><span class="sxs-lookup"><span data-stu-id="7de4f-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="7de4f-277">Názvy rozhraní</span><span class="sxs-lookup"><span data-stu-id="7de4f-277">Interface Names</span></span>  
 <span data-ttu-id="7de4f-278">Číslo, které se zobrazí na konci názvů rozhraní v rozhraní API pro ladění (například "3" v `ICorDebugThread3`), určuje verzi rozhraní, nikoli verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7de4f-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="7de4f-279">Všechny názvy rozhraní v rozhraní API pro ladění obsahují čísla verzí kromě rozhraní zavedených ve verzi .NET Framework 1.</span><span class="sxs-lookup"><span data-stu-id="7de4f-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="7de4f-280">Jakékoli korespondence mezi čísly verzí rozhraní and.NET čísly verze Frameworku jsou koincidenty.</span><span class="sxs-lookup"><span data-stu-id="7de4f-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="7de4f-281">Rozhraní, která byla představena ve .NET Framework verze 1,0, neobsahují čísla, protože jsou implicitně verze 1.</span><span class="sxs-lookup"><span data-stu-id="7de4f-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="7de4f-282">.NET Framework verze 1,1 používá rozhraní verze 1,0 a nezavádí žádná nová rozhraní ladění.</span><span class="sxs-lookup"><span data-stu-id="7de4f-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="7de4f-283">Rozhraní pro ladění 14 představená ve verzi .NET Framework 2,0 jsou logická rozšíření jejich protějšků verze 1 a v názvech obsahují číslo "2".</span><span class="sxs-lookup"><span data-stu-id="7de4f-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="7de4f-284">.NET Framework verze 3,0 a 3,5 používají existující rozhraní .NET Framework 2,0 a nezavádí žádná nová rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7de4f-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="7de4f-285">.NET Framework 4 zavádí kombinaci verzí rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7de4f-285">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="7de4f-286">Například `ICorDebugThread3` a `ICorDebugThread4` se zobrazí jako třetí a čtvrté verze `ICorDebugThread` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7de4f-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="7de4f-287">.NET Framework 4 také zavádí první verzi `ICorDebugStackWalk` rozhraní a druhou verzi `ICorDebugNativeFrame` rozhraní (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="7de4f-287">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7de4f-288">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7de4f-288">Requirements</span></span>  
 <span data-ttu-id="7de4f-289">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7de4f-289">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7de4f-290">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7de4f-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7de4f-291">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7de4f-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7de4f-292">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7de4f-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de4f-293">Viz také</span><span class="sxs-lookup"><span data-stu-id="7de4f-293">See also</span></span>

- [<span data-ttu-id="7de4f-294">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="7de4f-294">Debugging Enumerations</span></span>](debugging-enumerations.md)
