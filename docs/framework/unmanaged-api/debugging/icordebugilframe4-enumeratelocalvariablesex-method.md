---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f9d20eda8684a9a5ae43c6240d0f8a9722c4d97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076832"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="68996-102">ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="68996-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="68996-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="68996-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="68996-104">Získá enumerátor pro místní proměnné v rámci a volitelně obsahuje proměnné, které jsou přidány v profileru instrumentace ReJIT.</span><span class="sxs-lookup"><span data-stu-id="68996-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68996-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68996-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68996-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="68996-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="68996-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda proměnné přidány v profileru instrumentace ReJIT jsou zahrnuty v rámci.</span><span class="sxs-lookup"><span data-stu-id="68996-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="68996-108">[out] Ukazatel na adresu "Icordebugvalueenum –" objekt enumerátoru pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="68996-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68996-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68996-109">Remarks</span></span>  
 <span data-ttu-id="68996-110">Tato metoda je podobný [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) metody, s tím rozdílem, že se volitelně přistupuje k proměnné přidány v profileru instrumentace ReJIT.</span><span class="sxs-lookup"><span data-stu-id="68996-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="68996-111">Nastavení `flags` k `ILCODE_ORIGINAL_IL` je ekvivalentní volání [icordebugilframe::enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="68996-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="68996-112">Nastavení `flags` k `ILCODE_REJIT_IL` umožňuje přistupovat k místním proměnným přidán v profileru instrumentace ReJIT ladicí program.</span><span class="sxs-lookup"><span data-stu-id="68996-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="68996-113">Pokud není instrumentovaný převodní jazyk (IL), je prázdný výčet a metoda vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="68996-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="68996-114">Enumerátor nemusí zahrnovat všechny místní proměnné v metodě spuštěné, protože některé z nich nesmí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="68996-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68996-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68996-115">Requirements</span></span>  
 <span data-ttu-id="68996-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68996-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68996-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68996-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68996-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68996-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68996-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68996-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68996-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68996-120">See also</span></span>

- [<span data-ttu-id="68996-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68996-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="68996-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="68996-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="68996-123">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="68996-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
