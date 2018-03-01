---
title: "ICorDebugILFrame4::GetCodeEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5d1d480014e90d3fea9790b10e0dace5a0847ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="cb3dc-102">ICorDebugILFrame4::GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="cb3dc-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="cb3dc-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="cb3dc-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cb3dc-104">Získá ukazatel na kód, který spouští tento rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3dc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb3dc-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb3dc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb3dc-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="cb3dc-107">[v] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda převodní jazyk (IL) definované profileru ReJIT požadavku je součástí rámečku.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="cb3dc-108">[out] Ukazatel na adresu "ICorDebugCode" objekt, který představuje kód, který spouští tento rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb3dc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb3dc-109">Remarks</span></span>  
 <span data-ttu-id="cb3dc-110">Tato metoda je podobná [icordebugframe::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metoda, s výjimkou toho, aby volitelně přistupuje kódu, které jsou definované profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="cb3dc-111">Voláním této metody se `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je metoda instrumentována, jeho IL nebudou přístupné.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="cb3dc-112">`ILCODE_REJIT_IL`Umožňuje pro přístup k IL definované profileru ReJIT požadavku ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="cb3dc-113">Pokud IL není instrumentována, `ppCode` je **null**, a vrátí metodu `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb3dc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb3dc-114">Requirements</span></span>  
 <span data-ttu-id="cb3dc-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb3dc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3dc-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb3dc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb3dc-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb3dc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb3dc-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb3dc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3dc-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb3dc-119">See Also</span></span>  
 [<span data-ttu-id="cb3dc-120">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb3dc-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="cb3dc-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cb3dc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cb3dc-122">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="cb3dc-122">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
