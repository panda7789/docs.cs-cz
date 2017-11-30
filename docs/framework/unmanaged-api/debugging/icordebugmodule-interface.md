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
ms.openlocfilehash: ced01c9c01a32468f371a8e172c878337fb79757
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="3ff45-102">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="3ff45-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="3ff45-103">Představuje běžné modul runtime (CLR) jazyk, který je buď spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="3ff45-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ff45-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3ff45-104">Methods</span></span>  
  
|<span data-ttu-id="3ff45-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-105">Method</span></span>|<span data-ttu-id="3ff45-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3ff45-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ff45-107">Createbreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="3ff45-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3ff45-108">Not implemented.</span></span>|  
|[<span data-ttu-id="3ff45-109">Enableclassloadcallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="3ff45-110">Určuje, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) pro tento modul se nazývají zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="3ff45-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="3ff45-111">Enablejitdebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="3ff45-112">Určuje, zda kompilátoru za běhu (JIT) uchovává informace o ladění pro metod v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="3ff45-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="3ff45-113">Getassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="3ff45-114">Získá obsahující sestavení pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="3ff45-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="3ff45-115">Getbaseaddress – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="3ff45-116">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="3ff45-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="3ff45-117">Getclassfromtoken – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="3ff45-118">Získá ICorDebugClass z metadat.</span><span class="sxs-lookup"><span data-stu-id="3ff45-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="3ff45-119">Geteditandcontinuesnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="3ff45-120">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="3ff45-120">Deprecated.</span></span>|  
|[<span data-ttu-id="3ff45-121">Getfunctionfromrva – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="3ff45-122">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3ff45-122">Not implemented.</span></span>|  
|[<span data-ttu-id="3ff45-123">Getfunctionfromtoken – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="3ff45-124">Získá funkce, která je zadána token metadat.</span><span class="sxs-lookup"><span data-stu-id="3ff45-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="3ff45-125">Getglobalvariablevalue – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="3ff45-126">Získá objekt hodnoty pro zadaný globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="3ff45-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="3ff45-127">Getmetadatainterface – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="3ff45-128">Získá ukazatel rozhraní metadata, která můžete použít k prozkoumání metadata pro modul.</span><span class="sxs-lookup"><span data-stu-id="3ff45-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="3ff45-129">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="3ff45-130">Získá název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="3ff45-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="3ff45-131">Getprocess – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="3ff45-132">Získá obsahující proces pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="3ff45-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="3ff45-133">Getsize – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="3ff45-134">Získá velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="3ff45-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="3ff45-135">Gettoken – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="3ff45-136">Získá token pro položku tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="3ff45-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="3ff45-137">Isdynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="3ff45-138">Určuje, zda je modul dynamické.</span><span class="sxs-lookup"><span data-stu-id="3ff45-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="3ff45-139">Isinmemory – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff45-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="3ff45-140">Určuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="3ff45-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ff45-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ff45-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ff45-142">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3ff45-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ff45-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ff45-143">Requirements</span></span>  
 <span data-ttu-id="3ff45-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ff45-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ff45-145">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ff45-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ff45-146">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ff45-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ff45-147">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ff45-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff45-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ff45-148">See Also</span></span>  
 [<span data-ttu-id="3ff45-149">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ff45-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="3ff45-150">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ff45-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
