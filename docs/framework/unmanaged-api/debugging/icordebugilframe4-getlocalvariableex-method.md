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
ms.openlocfilehash: fb2744493d89a57ffc78e194f8c1e4a6dcf9f7c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090920"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="1890a-102">ICorDebugILFrame4::GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="1890a-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="1890a-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="1890a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1890a-104">Získá hodnotu zadané místní proměnné v rámci tohoto bloku zásobníku pro mezilehlé jazyky (IL) a volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="1890a-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1890a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1890a-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1890a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1890a-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="1890a-107">pro Člen výčtu [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , který určuje, jestli je do tohoto rámce zahrnutá proměnná přidaná v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="1890a-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="1890a-108">pro Index místní proměnné v rámci bloku IL.</span><span class="sxs-lookup"><span data-stu-id="1890a-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1890a-109">mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje načtenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1890a-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1890a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1890a-110">Remarks</span></span>  
 <span data-ttu-id="1890a-111">Tato metoda je podobná metodě [GetLocalVariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) , s tím rozdílem, že volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="1890a-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="1890a-112">Volání této metody s hodnotou `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání [GetLocalVariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Pokud je metoda instrumentovaná pomocí dalších místních proměnných, k těmto proměnným nelze přidružit.</span><span class="sxs-lookup"><span data-stu-id="1890a-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="1890a-113">`ILCODE_REJIT_IL` umožňuje ladicímu programu přístup k místním proměnným přidaným v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="1890a-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="1890a-114">Pokud není IL instrumentovat, metoda vrátí `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="1890a-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1890a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1890a-115">Requirements</span></span>  
 <span data-ttu-id="1890a-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1890a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1890a-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1890a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1890a-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1890a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1890a-119">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1890a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1890a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1890a-120">See also</span></span>

- [<span data-ttu-id="1890a-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1890a-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="1890a-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1890a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1890a-123">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="1890a-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
