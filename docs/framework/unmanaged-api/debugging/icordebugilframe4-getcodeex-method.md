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
ms.openlocfilehash: 24be4507e8ad6cde1e9c50582e352f0fc9b12ed3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483746"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="e63f6-102">ICorDebugILFrame4::GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="e63f6-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="e63f6-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e63f6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e63f6-104">Získá ukazatel na kód, který spouští tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e63f6-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e63f6-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e63f6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e63f6-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="e63f6-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, který určuje, zda je v rámci zahrnuta (IL intermediate language) určené profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="e63f6-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="e63f6-108">[out] Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který spouští tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e63f6-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e63f6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e63f6-109">Remarks</span></span>  
 <span data-ttu-id="e63f6-110">Tato metoda je podobný [icordebugframe::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, s tím rozdílem, že se volitelně přistupuje k určené požadavek ReJIT profileru kód.</span><span class="sxs-lookup"><span data-stu-id="e63f6-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="e63f6-111">Volání této metody `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je instrumentováno metodu, jeho IL nebude přístupná.</span><span class="sxs-lookup"><span data-stu-id="e63f6-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="e63f6-112">`ILCODE_REJIT_IL` Umožňuje ladicího programu pro přístup k IL určené profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="e63f6-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="e63f6-113">Pokud není instrumentovaný IL, `ppCode` je **null**, a vrátí metodu `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="e63f6-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e63f6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e63f6-114">Requirements</span></span>  
 <span data-ttu-id="e63f6-115">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e63f6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e63f6-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e63f6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e63f6-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e63f6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e63f6-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e63f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63f6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e63f6-119">See Also</span></span>  
 [<span data-ttu-id="e63f6-120">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e63f6-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="e63f6-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e63f6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e63f6-122">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="e63f6-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
