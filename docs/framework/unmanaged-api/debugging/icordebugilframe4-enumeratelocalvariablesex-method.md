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
ms.openlocfilehash: 69a7501d9b887b9504067409356bf302c47466e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090256"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="18e44-102">ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="18e44-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="18e44-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="18e44-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="18e44-104">Získá enumerátor pro místní proměnnou v rámci a volitelně zahrnuje proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="18e44-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e44-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18e44-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18e44-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="18e44-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="18e44-107">pro Člen výčtu [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , který určuje, jestli jsou proměnné přidané v profileru ReJIT instrumentace zahrnuté do snímku.</span><span class="sxs-lookup"><span data-stu-id="18e44-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="18e44-108">mimo Ukazatel na adresu objektu "ICorDebugValueEnum", který je enumerátorem místních proměnných v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="18e44-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18e44-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18e44-109">Remarks</span></span>  
 <span data-ttu-id="18e44-110">Tato metoda se podobá metodě [EnumerateLocalVariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) , s tím rozdílem, že volitelně přistupuje k proměnným přidaným v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="18e44-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="18e44-111">Nastavení `flags` na `ILCODE_ORIGINAL_IL` je ekvivalentní volání [ICorDebugILFrame:: EnumerateLocalVariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="18e44-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="18e44-112">Nastavení `flags` `ILCODE_REJIT_IL` umožňuje ladicímu programu přístup k místním proměnným přidaným v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="18e44-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="18e44-113">Pokud není proinstrumentované rozhraní IL (Intermediate Language), je výčet prázdný a metoda vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="18e44-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="18e44-114">Enumerátor nesmí obsahovat všechny místní proměnné v běžící metodě, protože některé z nich nemusí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="18e44-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18e44-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18e44-115">Requirements</span></span>  
 <span data-ttu-id="18e44-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18e44-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18e44-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="18e44-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18e44-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="18e44-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18e44-119">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18e44-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e44-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18e44-120">See also</span></span>

- [<span data-ttu-id="18e44-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18e44-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="18e44-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="18e44-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="18e44-123">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="18e44-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
