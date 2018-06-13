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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a82f092a0f10fd621ac4facdee201fa239e1c1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414526"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="f6571-102">ICorDebugILFrame4::GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f6571-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="f6571-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="f6571-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f6571-104">Získá hodnotu zadaného místní proměnné v této rámce zásobníku převodní jazyk (IL) a volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="f6571-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6571-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6571-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6571-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6571-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="f6571-107">[v] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda proměnné přidali v ReJIT instrumentace profileru je součástí rámečku.</span><span class="sxs-lookup"><span data-stu-id="f6571-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="f6571-108">[v] Index místní proměnné v rámci zásobníku IL.</span><span class="sxs-lookup"><span data-stu-id="f6571-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f6571-109">[out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f6571-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6571-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6571-110">Remarks</span></span>  
 <span data-ttu-id="f6571-111">Tato metoda je podobná [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metoda, s tím rozdílem, že IT oddělení volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="f6571-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="f6571-112">Voláním této metody se `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Pokud je metoda instrumentovány s další místní proměnné, tyto proměnné nelze získat přístup.</span><span class="sxs-lookup"><span data-stu-id="f6571-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="f6571-113">`ILCODE_REJIT_IL` Umožňuje pro přístup k místní proměnné přidali v ReJIT instrumentace profileru ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f6571-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="f6571-114">Pokud není instrumentována IL, vrátí metoda `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="f6571-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6571-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6571-115">Requirements</span></span>  
 <span data-ttu-id="f6571-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6571-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6571-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6571-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6571-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6571-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6571-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6571-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6571-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6571-120">See Also</span></span>  
 [<span data-ttu-id="f6571-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6571-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="f6571-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f6571-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f6571-123">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="f6571-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
