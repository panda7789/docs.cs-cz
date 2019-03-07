---
title: ICorDebugMutableDataTarget::ContinueStatusChanged Method
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9d182dbf7371dfdb572b7ab989eb90288b2006a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492553"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="e79e6-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span><span class="sxs-lookup"><span data-stu-id="e79e6-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="e79e6-103">Změní stav pokračování pro zbývající ladění události u zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="e79e6-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e79e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e79e6-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e79e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e79e6-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="e79e6-106">Identifikátor vlákna operačního systému definovaný.</span><span class="sxs-lookup"><span data-stu-id="e79e6-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="e79e6-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje novou požadovaný stav pokračování.</span><span class="sxs-lookup"><span data-stu-id="e79e6-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e79e6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e79e6-108">Remarks</span></span>  
 <span data-ttu-id="e79e6-109">Volání ladicího programu `ContinueStatusChanged` metody volá metodu icordebug –, který vyžaduje aktuální ladicí událost zpracovávat tak, aby se potenciálně liší od způsobu, ve kterém je obvykle zpracovává.</span><span class="sxs-lookup"><span data-stu-id="e79e6-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="e79e6-110">Například, pokud dojde k výjimce nezpracovaných a ladicí program vyžaduje operace, která by zrušit výjimku (například [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo `FuncEval`), toto rozhraní API slouží k vyžádání, že se výjimka bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="e79e6-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e79e6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e79e6-111">Requirements</span></span>  
 <span data-ttu-id="e79e6-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e79e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e79e6-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e79e6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e79e6-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e79e6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e79e6-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e79e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79e6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e79e6-116">See also</span></span>
- [<span data-ttu-id="e79e6-117">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e79e6-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="e79e6-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e79e6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
