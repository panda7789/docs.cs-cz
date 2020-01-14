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
ms.openlocfilehash: 5b3950a0c134afc23d51d05bca24c151bcff77ec
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937847"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="8afce-102">ICorDebugILFrame4::GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="8afce-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="8afce-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="8afce-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8afce-104">Získá ukazatel na kód, který tento rámec zásobníku provádí.</span><span class="sxs-lookup"><span data-stu-id="8afce-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8afce-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8afce-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8afce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8afce-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="8afce-107">pro Člen výčtu [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , který určuje, zda je do rámce zahrnut převodní jazyk (IL) definovaný požadavkem ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="8afce-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="8afce-108">mimo Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který tento rámec zásobníku provádí.</span><span class="sxs-lookup"><span data-stu-id="8afce-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8afce-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8afce-109">Remarks</span></span>  
 <span data-ttu-id="8afce-110">Tato metoda je podobná metodě [ICorDebugFrame:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) s tím rozdílem, že volitelně přistupuje k kódu definovanému požadavkem ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="8afce-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="8afce-111">Volání této metody s hodnotou `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání metody [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je metoda instrumentovaná, její IL nebude přístupná.</span><span class="sxs-lookup"><span data-stu-id="8afce-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="8afce-112">`ILCODE_REJIT_IL` umožňuje ladicímu programu přístup k IL definovanému požadavkem ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="8afce-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="8afce-113">Pokud úroveň IL není instrumentovaná, `ppCode` je **null**a metoda vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="8afce-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8afce-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8afce-114">Requirements</span></span>  
 <span data-ttu-id="8afce-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8afce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8afce-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8afce-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8afce-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8afce-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8afce-118">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8afce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8afce-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8afce-119">See also</span></span>

- [<span data-ttu-id="8afce-120">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8afce-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="8afce-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8afce-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8afce-122">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="8afce-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
