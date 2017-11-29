---
title: "ICorDebugMutableDataTarget::ContinueStatusChanged – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2f4f3890f2cfb2e3b017b8c7d0705d8c8e063957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="89c8c-102">ICorDebugMutableDataTarget::ContinueStatusChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="89c8c-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="89c8c-103">Změní stav pokračování události nezpracovaných ladění na zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="89c8c-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89c8c-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89c8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89c8c-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="89c8c-106">Identifikátor vlákno definované operačního systému.</span><span class="sxs-lookup"><span data-stu-id="89c8c-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="89c8c-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)hodnotu, která představuje nový požadovaný stav pokračování.</span><span class="sxs-lookup"><span data-stu-id="89c8c-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89c8c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89c8c-108">Remarks</span></span>  
 <span data-ttu-id="89c8c-109">Ladicí program volání `ContinueStatusChanged` metoda při volání metody ICorDebug, vyžaduje aktuální událost ladění zpracovávat způsobem, který je potenciálně liší od způsobu, ve kterém se za normálních okolností by ošetřit.</span><span class="sxs-lookup"><span data-stu-id="89c8c-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="89c8c-110">Například, pokud dojde k výjimce nezpracovaných a ladicí program požadavky operace, která by zrušit výjimku (například [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo `FuncEval`), toto rozhraní API slouží k vyžádání, že se výjimka zrušena.</span><span class="sxs-lookup"><span data-stu-id="89c8c-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89c8c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89c8c-111">Requirements</span></span>  
 <span data-ttu-id="89c8c-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89c8c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89c8c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89c8c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89c8c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89c8c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89c8c-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89c8c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89c8c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="89c8c-116">See Also</span></span>  
 [<span data-ttu-id="89c8c-117">ICorDebugMutableDataTarget rozhraní</span><span class="sxs-lookup"><span data-stu-id="89c8c-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="89c8c-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="89c8c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
