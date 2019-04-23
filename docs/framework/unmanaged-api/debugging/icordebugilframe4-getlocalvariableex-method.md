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
ms.openlocfilehash: c6594bb72ce9cd2fbfa9cdafebc152a90618b810
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193080"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="cd204-102">ICorDebugILFrame4::GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="cd204-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="cd204-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="cd204-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cd204-104">Získá hodnotu místní proměnné zadané v tomto bloku zásobníku (IL intermediate language) a volitelně přistupuje k proměnné přidány v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="cd204-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd204-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd204-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd204-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd204-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="cd204-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, který určuje, zda je proměnná přidán v profileru instrumentace ReJIT zahrnuta v rámci.</span><span class="sxs-lookup"><span data-stu-id="cd204-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="cd204-108">[in] Index lokální proměnné v bloku zásobníku IL.</span><span class="sxs-lookup"><span data-stu-id="cd204-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="cd204-109">[out] Ukazatel na adresu objektu "ICorDebugValue", který představuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cd204-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd204-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd204-110">Remarks</span></span>  
 <span data-ttu-id="cd204-111">Tato metoda je podobný [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody, s tím rozdílem, že se volitelně přistupuje k proměnné přidány v profileru instrumentace ReJIT.</span><span class="sxs-lookup"><span data-stu-id="cd204-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="cd204-112">Volání této metody `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Pokud je metoda neinstrumentují službou další místní proměnné, tyto proměnné není přístupný.</span><span class="sxs-lookup"><span data-stu-id="cd204-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="cd204-113">`ILCODE_REJIT_IL` umožňuje přistupovat k místním proměnným přidán v profileru instrumentace ReJIT ladicí program.</span><span class="sxs-lookup"><span data-stu-id="cd204-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="cd204-114">Pokud není instrumentovaný IL, metoda vrátí `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="cd204-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd204-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd204-115">Requirements</span></span>  
 <span data-ttu-id="cd204-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd204-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd204-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd204-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd204-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd204-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd204-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd204-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd204-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd204-120">See also</span></span>

- [<span data-ttu-id="cd204-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd204-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="cd204-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cd204-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cd204-123">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="cd204-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
