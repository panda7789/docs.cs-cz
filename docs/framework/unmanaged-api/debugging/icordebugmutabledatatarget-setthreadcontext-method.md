---
title: 'ICorDebugMutableDataTarget:: SetThreadContext – – metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: a6df6bf030ad339f5d02b95cd191b30db60aa167
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210147"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="7f17c-102">ICorDebugMutableDataTarget:: SetThreadContext – – metoda</span><span class="sxs-lookup"><span data-stu-id="7f17c-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="7f17c-103">Nastaví kontext (hodnoty registru) pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="7f17c-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f17c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f17c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f17c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f17c-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="7f17c-106">pro Identifikátor vlákna definovaného operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="7f17c-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7f17c-107">pro Velikost `pContext` vyrovnávací paměti, která má být zapsána.</span><span class="sxs-lookup"><span data-stu-id="7f17c-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="7f17c-108">pro Ukazatel na bajty, které mají být zapsány.</span><span class="sxs-lookup"><span data-stu-id="7f17c-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f17c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f17c-109">Remarks</span></span>  
 <span data-ttu-id="7f17c-110">`SetThreadContext`Metoda aktualizuje aktuální kontext pro vlákno určené argumentem definovaným operačním systémem `dwThreadID` .</span><span class="sxs-lookup"><span data-stu-id="7f17c-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="7f17c-111">Formát záznamu kontextu je určen platformou určenou metodou [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7f17c-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="7f17c-112">Ve Windows je to [kontextová](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) struktura.</span><span class="sxs-lookup"><span data-stu-id="7f17c-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f17c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f17c-113">Requirements</span></span>  
 <span data-ttu-id="7f17c-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f17c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f17c-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7f17c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f17c-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7f17c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f17c-117">**Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f17c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f17c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f17c-118">See also</span></span>

- [<span data-ttu-id="7f17c-119">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f17c-119">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="7f17c-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f17c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
