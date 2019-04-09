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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162329"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="4ad42-102">ICorDebugILFrame4::GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="4ad42-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="4ad42-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="4ad42-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4ad42-104">Získá ukazatel na kód, který spouští tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4ad42-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad42-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ad42-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ad42-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ad42-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="4ad42-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, který určuje, zda je v rámci zahrnuta (IL intermediate language) určené profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="4ad42-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="4ad42-108">[out] Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který spouští tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4ad42-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ad42-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ad42-109">Remarks</span></span>  
 <span data-ttu-id="4ad42-110">Tato metoda je podobný [icordebugframe::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, s tím rozdílem, že se volitelně přistupuje k určené požadavek ReJIT profileru kód.</span><span class="sxs-lookup"><span data-stu-id="4ad42-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="4ad42-111">Volání této metody `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je instrumentováno metodu, jeho IL nebude přístupná.</span><span class="sxs-lookup"><span data-stu-id="4ad42-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> `ILCODE_REJIT_IL` <span data-ttu-id="4ad42-112">Umožňuje ladicího programu pro přístup k IL určené profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="4ad42-112">allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="4ad42-113">Pokud není instrumentovaný IL, `ppCode` je **null**, a vrátí metodu `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="4ad42-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad42-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ad42-114">Requirements</span></span>  
 <span data-ttu-id="4ad42-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ad42-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad42-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ad42-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ad42-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ad42-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4ad42-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4ad42-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4ad42-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ad42-119">See also</span></span>

- [<span data-ttu-id="4ad42-120">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="4ad42-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="4ad42-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ad42-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4ad42-122">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="4ad42-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
