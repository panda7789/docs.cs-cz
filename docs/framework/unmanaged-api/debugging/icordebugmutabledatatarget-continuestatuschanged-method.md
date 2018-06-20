---
title: ICorDebugMutableDataTarget::ContinueStatusChanged – metoda
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d2560aa484c6965047b2fdaf2c539b8ab675bc8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207700"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="22d66-102">ICorDebugMutableDataTarget::ContinueStatusChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="22d66-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="22d66-103">Změní stav pokračování události nezpracovaných ladění na zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="22d66-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d66-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22d66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22d66-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="22d66-106">Identifikátor vlákno definované operačního systému.</span><span class="sxs-lookup"><span data-stu-id="22d66-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="22d66-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje nový požadovaný stav pokračování.</span><span class="sxs-lookup"><span data-stu-id="22d66-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22d66-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22d66-108">Remarks</span></span>  
 <span data-ttu-id="22d66-109">Ladicí program volání `ContinueStatusChanged` metoda při volání metody ICorDebug, vyžaduje aktuální událost ladění zpracovávat způsobem, který je potenciálně liší od způsobu, ve kterém se za normálních okolností by ošetřit.</span><span class="sxs-lookup"><span data-stu-id="22d66-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="22d66-110">Například, pokud dojde k výjimce nezpracovaných a ladicí program požadavky operace, která by zrušit výjimku (například [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo `FuncEval`), toto rozhraní API slouží k vyžádání, že se výjimka zrušena.</span><span class="sxs-lookup"><span data-stu-id="22d66-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d66-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22d66-111">Requirements</span></span>  
 <span data-ttu-id="22d66-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d66-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d66-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22d66-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22d66-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22d66-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22d66-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d66-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="22d66-116">See Also</span></span>  
 [<span data-ttu-id="22d66-117">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d66-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="22d66-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="22d66-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
