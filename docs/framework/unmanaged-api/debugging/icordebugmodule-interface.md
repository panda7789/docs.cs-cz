---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c24d8305e71aac01843155b86fb54fb1e1263d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="46567-102">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="46567-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="46567-103">Představuje běžné modul runtime (CLR) jazyk, který je buď spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="46567-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46567-104">Metody</span><span class="sxs-lookup"><span data-stu-id="46567-104">Methods</span></span>  
  
|<span data-ttu-id="46567-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="46567-105">Method</span></span>|<span data-ttu-id="46567-106">Popis</span><span class="sxs-lookup"><span data-stu-id="46567-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46567-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="46567-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="46567-108">Not implemented.</span></span>|  
|[<span data-ttu-id="46567-109">EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="46567-110">Určuje, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) pro tento modul se nazývají zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="46567-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="46567-111">EnableJITDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="46567-112">Určuje, zda kompilátoru za běhu (JIT) uchovává informace o ladění pro metod v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="46567-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="46567-113">GetAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="46567-114">Získá obsahující sestavení pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="46567-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="46567-115">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="46567-116">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="46567-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="46567-117">GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="46567-118">Získá ICorDebugClass z metadat.</span><span class="sxs-lookup"><span data-stu-id="46567-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="46567-119">GetEditAndContinueSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="46567-120">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="46567-120">Deprecated.</span></span>|  
|[<span data-ttu-id="46567-121">GetFunctionFromRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="46567-122">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="46567-122">Not implemented.</span></span>|  
|[<span data-ttu-id="46567-123">GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="46567-124">Získá funkce, která je zadána token metadat.</span><span class="sxs-lookup"><span data-stu-id="46567-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="46567-125">GetGlobalVariableValue – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="46567-126">Získá objekt hodnoty pro zadaný globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="46567-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="46567-127">GetMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="46567-128">Získá ukazatel rozhraní metadata, která můžete použít k prozkoumání metadata pro modul.</span><span class="sxs-lookup"><span data-stu-id="46567-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="46567-129">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="46567-130">Získá název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="46567-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="46567-131">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="46567-132">Získá obsahující proces pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="46567-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="46567-133">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="46567-134">Získá velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="46567-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="46567-135">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="46567-136">Získá token pro položku tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="46567-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="46567-137">IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="46567-138">Určuje, zda je modul dynamické.</span><span class="sxs-lookup"><span data-stu-id="46567-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="46567-139">IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="46567-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="46567-140">Určuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="46567-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46567-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46567-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46567-142">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="46567-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46567-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46567-143">Requirements</span></span>  
 <span data-ttu-id="46567-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46567-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46567-145">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46567-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46567-146">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46567-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46567-147">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46567-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46567-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="46567-148">See Also</span></span>  
 [<span data-ttu-id="46567-149">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46567-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="46567-150">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="46567-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
