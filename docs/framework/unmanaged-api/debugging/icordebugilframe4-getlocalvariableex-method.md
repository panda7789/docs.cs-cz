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
ms.openlocfilehash: 017c14e9170087f3c3c9de64f50d165fc91aa297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782407"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="35cf5-102">ICorDebugILFrame4::GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="35cf5-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="35cf5-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="35cf5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="35cf5-104">Získá hodnotu zadané místní proměnné v rámci tohoto bloku zásobníku pro mezilehlé jazyky (IL) a volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="35cf5-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35cf5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35cf5-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35cf5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="35cf5-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="35cf5-107">pro Člen výčtu [ILCodeKind](ilcodekind-enumeration.md) , který určuje, jestli je do tohoto rámce zahrnutá proměnná přidaná v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="35cf5-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="35cf5-108">pro Index místní proměnné v rámci bloku IL.</span><span class="sxs-lookup"><span data-stu-id="35cf5-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="35cf5-109">mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje načtenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="35cf5-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35cf5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35cf5-110">Remarks</span></span>  
 <span data-ttu-id="35cf5-111">Tato metoda je podobná metodě [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) , s tím rozdílem, že volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="35cf5-111">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="35cf5-112">Volání této metody s hodnotou `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md); Pokud je metoda instrumentovaná pomocí dalších místních proměnných, k těmto proměnným nelze přidružit.</span><span class="sxs-lookup"><span data-stu-id="35cf5-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="35cf5-113">`ILCODE_REJIT_IL` umožňuje ladicímu programu přístup k místním proměnným přidaným v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="35cf5-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="35cf5-114">Pokud není IL instrumentovat, metoda vrátí `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="35cf5-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35cf5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35cf5-115">Requirements</span></span>  
 <span data-ttu-id="35cf5-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35cf5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35cf5-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35cf5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35cf5-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35cf5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35cf5-119">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35cf5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35cf5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35cf5-120">See also</span></span>

- [<span data-ttu-id="35cf5-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35cf5-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="35cf5-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="35cf5-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="35cf5-123">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="35cf5-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
