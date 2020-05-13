---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged – metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 49f517c0c09771ce86e43b801f6d7fce695d907a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213306"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="34550-102">ICorDebugMutableDataTarget:: ContinueStatusChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="34550-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="34550-103">Změní stav pokračování pro nedokončenou událost ladění v zadaném vlákně.</span><span class="sxs-lookup"><span data-stu-id="34550-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34550-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34550-104">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34550-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34550-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="34550-106">Identifikátor vlákna definovaného operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="34550-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="34550-107">Hodnota [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) , která představuje nový požadovaný stav pokračování.</span><span class="sxs-lookup"><span data-stu-id="34550-107">A [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34550-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34550-108">Remarks</span></span>  
 <span data-ttu-id="34550-109">Ladicí program volá `ContinueStatusChanged` metodu při volání metody ICorDebug, která vyžaduje, aby byla aktuální událost ladění zpracována způsobem, který se může lišit od způsobu, jakým by byl normálně zpracován.</span><span class="sxs-lookup"><span data-stu-id="34550-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="34550-110">Například pokud existuje nevyřízená výjimka a ladicí program požaduje operaci, která by zrušila výjimku (například [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) nebo `FuncEval` ), toto rozhraní API se používá k vyžádání zrušení výjimky.</span><span class="sxs-lookup"><span data-stu-id="34550-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34550-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34550-111">Requirements</span></span>  
 <span data-ttu-id="34550-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34550-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34550-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34550-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34550-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34550-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34550-115">**Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34550-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34550-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="34550-116">See also</span></span>

- [<span data-ttu-id="34550-117">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34550-117">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="34550-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34550-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
