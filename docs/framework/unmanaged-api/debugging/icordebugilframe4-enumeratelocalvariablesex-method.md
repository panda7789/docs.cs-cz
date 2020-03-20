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
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178806"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="66256-102">ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="66256-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="66256-103">[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="66256-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="66256-104">Získá čítač výčtu pro místní proměnné v rámci a volitelně zahrnuje proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="66256-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66256-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66256-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66256-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="66256-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="66256-107">[v] Člen výčtu [ILCodeKind,](ilcodekind-enumeration.md) který určuje, zda jsou v rámci zahrnuty proměnné přidané v instrumentaci ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="66256-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="66256-108">[out] Ukazatel na adresu objektu "ICorDebugValueEnum", který je čítatelem pro místní proměnné v tomto rámci.</span><span class="sxs-lookup"><span data-stu-id="66256-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66256-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66256-109">Remarks</span></span>  
 <span data-ttu-id="66256-110">Tato metoda je podobná [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) metoda, s tím rozdílem, že volitelně přistupuje proměnné přidané v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="66256-110">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="66256-111">Nastavení `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="66256-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="66256-112">Nastavení `flags` `ILCODE_REJIT_IL` umožňuje ladicí program pro přístup k místním proměnným přidaným v instrumentaci ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="66256-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="66256-113">Pokud zprostředkující jazyk (IL) není instrumentovaný, výčet je `S_OK`prázdný a metoda vrátí .</span><span class="sxs-lookup"><span data-stu-id="66256-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="66256-114">Čítač nemusí obsahovat všechny místní proměnné v běžící metodě, protože některé z nich nemusí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="66256-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66256-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66256-115">Requirements</span></span>  
 <span data-ttu-id="66256-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66256-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66256-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66256-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66256-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66256-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66256-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66256-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66256-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="66256-120">See also</span></span>

- [<span data-ttu-id="66256-121">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66256-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="66256-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66256-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="66256-123">ReJIT: Návod, jak</span><span class="sxs-lookup"><span data-stu-id="66256-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
