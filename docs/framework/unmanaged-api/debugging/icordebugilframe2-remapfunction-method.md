---
title: ICorDebugILFrame2::RemapFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
ms.openlocfilehash: 43f585417ed52b92c23087c0f02fd188ee09ea7e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210212"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="2700d-102">ICorDebugILFrame2::RemapFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="2700d-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="2700d-103">Přemapuje upravenou funkci zadáním nového posunu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="2700d-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2700d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2700d-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2700d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2700d-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="2700d-106">pro Nový posun MSIL rámce zásobníku, na kterém by měl být umístěn ukazatel na instrukci.</span><span class="sxs-lookup"><span data-stu-id="2700d-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="2700d-107">Tato hodnota musí být bod sekvence.</span><span class="sxs-lookup"><span data-stu-id="2700d-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="2700d-108">Je zodpovědností volajícího, aby zajistila platnost této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2700d-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="2700d-109">Například posun jazyka MSIL není platný, pokud je mimo hranice funkce.</span><span class="sxs-lookup"><span data-stu-id="2700d-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2700d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2700d-110">Remarks</span></span>  
 <span data-ttu-id="2700d-111">Když je upravena funkce rámce, ladicí program může zavolat `RemapFunction` metodu pro prohození v nejnovější verzi funkce rámce, aby ji bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="2700d-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="2700d-112">Spuštění kódu bude zahájeno v daném posunu MSIL.</span><span class="sxs-lookup"><span data-stu-id="2700d-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2700d-113">Volání `RemapFunction` , podobně jako volání [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md), okamžitě zruší platnost všech ladicích rozhraní, která souvisí s generováním trasování zásobníku pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="2700d-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="2700d-114">Mezi tato rozhraní patří [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame a ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="2700d-114">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="2700d-115">`RemapFunction`Metodu lze volat pouze v kontextu aktuálního rámce a pouze v jednom z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="2700d-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="2700d-116">Po přijetí zpětného volání [ICorDebugManagedCallback2:: FunctionRemapOpportunity –](icordebugmanagedcallback2-functionremapopportunity-method.md) , které ještě nepokračovalo.</span><span class="sxs-lookup"><span data-stu-id="2700d-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="2700d-117">Při provádění kódu je zastaveno z důvodu události [ICorDebugManagedCallback:: EditAndContinueRemap –](icordebugmanagedcallback-editandcontinueremap-method.md) pro tento rámec.</span><span class="sxs-lookup"><span data-stu-id="2700d-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2700d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2700d-118">Requirements</span></span>  
 <span data-ttu-id="2700d-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2700d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2700d-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2700d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2700d-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2700d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2700d-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2700d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
