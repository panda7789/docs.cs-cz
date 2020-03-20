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
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178785"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="01cb0-102">ICorDebugILFrame4::GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="01cb0-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="01cb0-103">[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="01cb0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="01cb0-104">Získá ukazatel na kód, který tento rámec zásobníku je provádění.</span><span class="sxs-lookup"><span data-stu-id="01cb0-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01cb0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01cb0-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01cb0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="01cb0-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="01cb0-107">[v] Člen výčtu [ILCodeKind,](ilcodekind-enumeration.md) který určuje, zda je v rámci zahrnut zprostředkující jazyk (IL) definovaný požadavkem ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="01cb0-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="01cb0-108">[out] Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který tento rámec zásobníku je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="01cb0-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01cb0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01cb0-109">Remarks</span></span>  
 <span data-ttu-id="01cb0-110">Tato metoda je podobná [metodě ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) s tím rozdílem, že volitelně přistupuje ke kódu definovanému požadavkem ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="01cb0-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="01cb0-111">Volání této metody `flags` s `ILCODE_ORIGINAL_IL` hodnotou je ekvivalentní volání [GetCode](icordebugframe-getcode-method.md); pokud je metoda instrumentována, její IL nebude přístupná.</span><span class="sxs-lookup"><span data-stu-id="01cb0-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="01cb0-112">`ILCODE_REJIT_IL`umožňuje ladicímu programu přístup k IL definovanému požadavkem ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="01cb0-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="01cb0-113">Pokud IL není instrumentován, `ppCode` je **null** `S_OK`a metoda vrátí .</span><span class="sxs-lookup"><span data-stu-id="01cb0-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01cb0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01cb0-114">Requirements</span></span>  
 <span data-ttu-id="01cb0-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01cb0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01cb0-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01cb0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01cb0-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01cb0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01cb0-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01cb0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01cb0-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="01cb0-119">See also</span></span>

- [<span data-ttu-id="01cb0-120">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01cb0-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="01cb0-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01cb0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="01cb0-122">ReJIT: Návod, jak</span><span class="sxs-lookup"><span data-stu-id="01cb0-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
