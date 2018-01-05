---
title: "ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c82ecd9045deb772e31e549bf1050f85b148fd0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="6cacd-102">ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="6cacd-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="6cacd-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="6cacd-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6cacd-104">Získá enumerátor pro místní proměnné v rámečku a volitelně obsahuje proměnné přidali v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="6cacd-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cacd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cacd-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cacd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cacd-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="6cacd-107">[v] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda proměnné přidali v ReJIT instrumentace profileru jsou zahrnuty do rámečku.</span><span class="sxs-lookup"><span data-stu-id="6cacd-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="6cacd-108">[out] Ukazatel na adresu "ICorDebugValueEnum" objekt, který je enumerátor pro místní proměnné do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="6cacd-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cacd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cacd-109">Remarks</span></span>  
 <span data-ttu-id="6cacd-110">Tato metoda je podobná [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) metoda, s tím rozdílem, že IT oddělení volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="6cacd-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="6cacd-111">Nastavení `flags` k `ILCODE_ORIGINAL_IL` je ekvivalentní volání [icordebugilframe::enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="6cacd-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="6cacd-112">Nastavení `flags` k `ILCODE_REJIT_IL` umožňuje ladicího programu pro přístup k místní proměnné přidali v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="6cacd-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="6cacd-113">Pokud není instrumentována převodní jazyk (IL), je prázdný výčet a vrátí metoda `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="6cacd-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="6cacd-114">Enumerátor nemusí zahrnovat všechny místní proměnné v metodě spuštěné, vzhledem k tomu, že některé z nich nemusí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="6cacd-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cacd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cacd-115">Requirements</span></span>  
 <span data-ttu-id="6cacd-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cacd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cacd-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cacd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cacd-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cacd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cacd-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cacd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cacd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cacd-120">See Also</span></span>  
 [<span data-ttu-id="6cacd-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cacd-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="6cacd-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6cacd-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6cacd-123">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="6cacd-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
