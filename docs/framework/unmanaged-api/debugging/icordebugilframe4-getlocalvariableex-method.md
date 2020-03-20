---
title: ICorDebugILFrame4::GetLocalVariableEx – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178769"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="9e948-102">ICorDebugILFrame4::GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="9e948-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="9e948-103">[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="9e948-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9e948-104">Získá hodnotu zadané místní proměnné v tomto rámci zásobníku zprostředkující jazyk (IL) a volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="9e948-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e948-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e948-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e948-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e948-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="9e948-107">[v] Člen výčtu [ILCodeKind,](ilcodekind-enumeration.md) který určuje, zda je v rámci zahrnuta proměnná přidaná v instrumentaci ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="9e948-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="9e948-108">[v] Index místní proměnné v rámci zásobníku IL.</span><span class="sxs-lookup"><span data-stu-id="9e948-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9e948-109">[out] Ukazatel na adresu objektu "ICorDebugValue", který představuje načtenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9e948-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e948-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e948-110">Remarks</span></span>  
 <span data-ttu-id="9e948-111">Tato metoda je podobná [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) metoda, s tím rozdílem, že volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="9e948-111">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="9e948-112">Volání této metody `flags` s `ILCODE_ORIGINAL_IL` hodnotou je ekvivalentní volání [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); pokud je metoda instrumentována dalšími místními proměnnými, nelze k těmto proměnným získat přístup.</span><span class="sxs-lookup"><span data-stu-id="9e948-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="9e948-113">`ILCODE_REJIT_IL`umožňuje ladicímu programu přístup k místním proměnným přidaným v instrumentaci ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="9e948-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="9e948-114">Pokud NENÍ vybavena nástrojem, metoda `E_INVALIDARG`vrátí .</span><span class="sxs-lookup"><span data-stu-id="9e948-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e948-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e948-115">Requirements</span></span>  
 <span data-ttu-id="9e948-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e948-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e948-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e948-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e948-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e948-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e948-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e948-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e948-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e948-120">See also</span></span>

- [<span data-ttu-id="9e948-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e948-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="9e948-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e948-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9e948-123">ReJIT: Návod, jak</span><span class="sxs-lookup"><span data-stu-id="9e948-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
