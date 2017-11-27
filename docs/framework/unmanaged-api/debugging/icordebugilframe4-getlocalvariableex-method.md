---
title: "ICorDebugILFrame4::GetLocalVariableEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetCodeEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eca9919555d0ee7c4398ecff51f9a6ee3936a41b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="6a299-102">ICorDebugILFrame4::GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="6a299-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="6a299-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="6a299-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6a299-104">Získá hodnotu zadaného místní proměnné v této rámce zásobníku převodní jazyk (IL) a volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="6a299-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a299-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a299-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a299-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a299-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="6a299-107">[v] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda proměnné přidali v ReJIT instrumentace profileru je součástí rámečku.</span><span class="sxs-lookup"><span data-stu-id="6a299-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="6a299-108">[v] Index místní proměnné v rámci zásobníku IL.</span><span class="sxs-lookup"><span data-stu-id="6a299-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6a299-109">[out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6a299-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a299-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a299-110">Remarks</span></span>  
 <span data-ttu-id="6a299-111">Tato metoda je podobná [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metoda, s tím rozdílem, že IT oddělení volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="6a299-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="6a299-112">Voláním této metody se `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Pokud je metoda instrumentovány s další místní proměnné, tyto proměnné nelze získat přístup.</span><span class="sxs-lookup"><span data-stu-id="6a299-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="6a299-113">`ILCODE_REJIT_IL`Umožňuje pro přístup k místní proměnné přidali v ReJIT instrumentace profileru ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="6a299-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="6a299-114">Pokud není instrumentována IL, vrátí metoda `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="6a299-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a299-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a299-115">Requirements</span></span>  
 <span data-ttu-id="6a299-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a299-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a299-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a299-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a299-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a299-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a299-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a299-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a299-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a299-120">See Also</span></span>  
 [<span data-ttu-id="6a299-121">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="6a299-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="6a299-122">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a299-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6a299-123">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="6a299-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
