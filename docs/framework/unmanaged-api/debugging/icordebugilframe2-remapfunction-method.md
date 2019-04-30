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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92885d2a6514839a864d6a345dd8af8b07b90c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946520"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="d15e1-102">ICorDebugILFrame2::RemapFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="d15e1-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="d15e1-103">Změní funkce se upravila tak, že zadáte nové posun Microsoft intermediate language (MSIL)</span><span class="sxs-lookup"><span data-stu-id="d15e1-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d15e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d15e1-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d15e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d15e1-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="d15e1-106">[in] Rámec zásobníku bylo jakou by měl být umístěn ukazatel na instrukci nové posun jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="d15e1-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="d15e1-107">Tato hodnota musí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="d15e1-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="d15e1-108">Je odpovědností volajícího cílem zajistit platnost této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d15e1-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="d15e1-109">Například posun MSIL není platný, pokud je mimo rozsah funkce.</span><span class="sxs-lookup"><span data-stu-id="d15e1-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d15e1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d15e1-110">Remarks</span></span>  
 <span data-ttu-id="d15e1-111">Při funkce rámec byl upraven, můžete volat ladicí program `RemapFunction` metoda do odkládacího souboru v nejnovější verzi funkce rámce, proto mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="d15e1-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="d15e1-112">Spuštění kódu se začne daným posunem jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="d15e1-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d15e1-113">Volání `RemapFunction`, třeba volání [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), okamžitě skončí platnost všech ladění rozhraní, které se vztahují k vygenerování trasování zásobníku pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="d15e1-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="d15e1-114">Tato rozhraní zahrnují [icordebugchain –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame icordebuginternalframe – a icordebugnativeframe –.</span><span class="sxs-lookup"><span data-stu-id="d15e1-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="d15e1-115">`RemapFunction` Metodu lze volat pouze v kontextu aktuálního rámce a pouze v jednom z následujících případech:</span><span class="sxs-lookup"><span data-stu-id="d15e1-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="d15e1-116">Po přijetí [icordebugmanagedcallback2::functionremapopportunity –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) zpětné volání, které nebylo dosud pokračování.</span><span class="sxs-lookup"><span data-stu-id="d15e1-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="d15e1-117">Když je z důvodu zastaví provádění kódu [icordebugmanagedcallback::editandcontinueremap –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) události pro tento rámec.</span><span class="sxs-lookup"><span data-stu-id="d15e1-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d15e1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d15e1-118">Requirements</span></span>  
 <span data-ttu-id="d15e1-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d15e1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d15e1-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d15e1-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d15e1-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d15e1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d15e1-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d15e1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
