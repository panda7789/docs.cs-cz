---
title: ICorDebugILFrame4::GetCodeEx – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d61981d26d21ec1e5e24093817586ebf45b129e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988478"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="ca982-102">ICorDebugILFrame4::GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ca982-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="ca982-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ca982-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ca982-104">Získá ukazatel na kód, který spouští tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ca982-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca982-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca982-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca982-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca982-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="ca982-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, který určuje, zda je v rámci zahrnuta (IL intermediate language) určené profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="ca982-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="ca982-108">[out] Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který spouští tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ca982-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca982-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca982-109">Remarks</span></span>  
 <span data-ttu-id="ca982-110">Tato metoda je podobný [icordebugframe::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, s tím rozdílem, že se volitelně přistupuje k určené požadavek ReJIT profileru kód.</span><span class="sxs-lookup"><span data-stu-id="ca982-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="ca982-111">Volání této metody `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je instrumentováno metodu, jeho IL nebude přístupná.</span><span class="sxs-lookup"><span data-stu-id="ca982-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="ca982-112">`ILCODE_REJIT_IL` Umožňuje ladicího programu pro přístup k IL určené profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="ca982-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="ca982-113">Pokud není instrumentovaný IL, `ppCode` je **null**, a vrátí metodu `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="ca982-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca982-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca982-114">Requirements</span></span>  
 <span data-ttu-id="ca982-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca982-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca982-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca982-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca982-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca982-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca982-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca982-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca982-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca982-119">See also</span></span>

- [<span data-ttu-id="ca982-120">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca982-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="ca982-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ca982-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ca982-122">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="ca982-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
