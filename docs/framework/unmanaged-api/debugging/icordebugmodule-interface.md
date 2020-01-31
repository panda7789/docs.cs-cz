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
ms.openlocfilehash: c573e6b768aee1e8b681dcf2e828dc24d409025b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793018"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="b00d0-102">ICorDebugModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b00d0-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="b00d0-103">Představuje modul modulu CLR (Common Language Runtime), což je spustitelný soubor nebo knihovna DLL (Dynamic-Link Library).</span><span class="sxs-lookup"><span data-stu-id="b00d0-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b00d0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b00d0-104">Methods</span></span>  
  
|<span data-ttu-id="b00d0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-105">Method</span></span>|<span data-ttu-id="b00d0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b00d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b00d0-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="b00d0-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="b00d0-108">Not implemented.</span></span>|  
|[<span data-ttu-id="b00d0-109">EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="b00d0-110">Určuje, zda jsou pro tento modul volána zpětná volání [ICorDebugManagedCallback:: LoadClass –](icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](icordebugmanagedcallback-unloadclass-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b00d0-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="b00d0-111">EnableJITDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="b00d0-112">Určuje, zda kompilátor JIT (just-in-time) zachovává ladicí informace pro metody v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="b00d0-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="b00d0-113">GetAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="b00d0-114">Získá nadřazené sestavení pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="b00d0-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="b00d0-115">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="b00d0-116">Získá základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="b00d0-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="b00d0-117">GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="b00d0-118">Získá ICorDebugClass z metadat.</span><span class="sxs-lookup"><span data-stu-id="b00d0-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="b00d0-119">GetEditAndContinueSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="b00d0-120">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="b00d0-120">Deprecated.</span></span>|  
|[<span data-ttu-id="b00d0-121">GetFunctionFromRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="b00d0-122">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="b00d0-122">Not implemented.</span></span>|  
|[<span data-ttu-id="b00d0-123">GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="b00d0-124">Získá funkci, která je určena tokenem metadat.</span><span class="sxs-lookup"><span data-stu-id="b00d0-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="b00d0-125">GetGlobalVariableValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="b00d0-126">Získá objekt hodnoty pro zadanou globální proměnnou.</span><span class="sxs-lookup"><span data-stu-id="b00d0-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="b00d0-127">GetMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="b00d0-128">Získá ukazatel rozhraní metadat, který lze použít k prohlédnutí metadat pro modul.</span><span class="sxs-lookup"><span data-stu-id="b00d0-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="b00d0-129">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="b00d0-130">Získá název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="b00d0-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="b00d0-131">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="b00d0-132">Získá obsahující proces pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="b00d0-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="b00d0-133">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="b00d0-134">Získá velikost modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b00d0-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="b00d0-135">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="b00d0-136">Získá token pro položku tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="b00d0-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="b00d0-137">IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="b00d0-138">Určuje, zda je modul dynamický.</span><span class="sxs-lookup"><span data-stu-id="b00d0-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="b00d0-139">IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="b00d0-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="b00d0-140">Určuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="b00d0-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b00d0-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b00d0-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b00d0-142">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b00d0-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b00d0-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b00d0-143">Requirements</span></span>  
 <span data-ttu-id="b00d0-144">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b00d0-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b00d0-145">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b00d0-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b00d0-146">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b00d0-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b00d0-147">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b00d0-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00d0-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b00d0-148">See also</span></span>

- [<span data-ttu-id="b00d0-149">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b00d0-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="b00d0-150">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b00d0-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
