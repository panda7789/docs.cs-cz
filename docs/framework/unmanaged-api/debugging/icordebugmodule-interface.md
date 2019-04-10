---
title: ICorDebugModule – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 257011562a9ea687ef70b842c6d47219283e158e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225635"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="56450-102">ICorDebugModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56450-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="56450-103">Představuje společný modul runtime (CLR) jazyk, který je spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="56450-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56450-104">Metody</span><span class="sxs-lookup"><span data-stu-id="56450-104">Methods</span></span>  
  
|<span data-ttu-id="56450-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="56450-105">Method</span></span>|<span data-ttu-id="56450-106">Popis</span><span class="sxs-lookup"><span data-stu-id="56450-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56450-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="56450-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="56450-108">Not implemented.</span></span>|  
|[<span data-ttu-id="56450-109">EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="56450-110">Určuje, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání jsou volány pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="56450-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="56450-111">EnableJITDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="56450-112">Určuje, zda kompilátor just-in-time (JIT) uchovává informace o ladění pro metody v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="56450-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="56450-113">GetAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="56450-114">Získá obsahující sestavení pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="56450-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="56450-115">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="56450-116">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="56450-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="56450-117">GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="56450-118">Získá ICorDebugClass z metadat.</span><span class="sxs-lookup"><span data-stu-id="56450-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="56450-119">GetEditAndContinueSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="56450-120">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="56450-120">Deprecated.</span></span>|  
|[<span data-ttu-id="56450-121">GetFunctionFromRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="56450-122">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="56450-122">Not implemented.</span></span>|  
|[<span data-ttu-id="56450-123">GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="56450-124">Získá funkce, která je určená tokenem metadat.</span><span class="sxs-lookup"><span data-stu-id="56450-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="56450-125">GetGlobalVariableValue – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="56450-126">Získá objekt hodnoty pro zadaný globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="56450-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="56450-127">GetMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="56450-128">Získá metadata ukazatel rozhraní, který lze použít pro přezkoumání metadat pro modul.</span><span class="sxs-lookup"><span data-stu-id="56450-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="56450-129">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="56450-130">Získá název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="56450-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="56450-131">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="56450-132">Získá nadřazený proces pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="56450-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="56450-133">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="56450-134">Získá velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="56450-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="56450-135">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="56450-136">Získá token pro záznam tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="56450-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="56450-137">IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="56450-138">Určuje, zda se jedná o dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="56450-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="56450-139">IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="56450-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="56450-140">Označuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="56450-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56450-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56450-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56450-142">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="56450-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56450-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56450-143">Requirements</span></span>  
 <span data-ttu-id="56450-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56450-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56450-145">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56450-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56450-146">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56450-146">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="56450-147">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56450-147">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56450-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56450-148">See also</span></span>

- [<span data-ttu-id="56450-149">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56450-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="56450-150">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56450-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
