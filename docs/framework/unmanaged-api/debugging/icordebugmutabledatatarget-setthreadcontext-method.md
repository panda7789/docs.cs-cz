---
title: 'ICorDebugMutableDataTarget:: SetThreadContext – – metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 2c9e508c7a4059fee4e1cce6eb28e6de7b2fff6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132708"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="a9759-102">ICorDebugMutableDataTarget:: SetThreadContext – – metoda</span><span class="sxs-lookup"><span data-stu-id="a9759-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="a9759-103">Nastaví kontext (hodnoty registru) pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="a9759-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9759-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9759-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9759-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9759-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="a9759-106">pro Identifikátor vlákna definovaného operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="a9759-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a9759-107">pro Velikost vyrovnávací paměti pro `pContext`, která se má zapsat.</span><span class="sxs-lookup"><span data-stu-id="a9759-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="a9759-108">pro Ukazatel na bajty, které mají být zapsány.</span><span class="sxs-lookup"><span data-stu-id="a9759-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9759-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9759-109">Remarks</span></span>  
 <span data-ttu-id="a9759-110">Metoda `SetThreadContext` aktualizuje aktuální kontext pro vlákno určené `dwThreadID` argumentem definovaným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="a9759-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="a9759-111">Formát záznamu kontextu je určen platformou určenou metodou [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9759-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="a9759-112">Ve Windows je to [kontextová](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) struktura.</span><span class="sxs-lookup"><span data-stu-id="a9759-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9759-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9759-113">Requirements</span></span>  
 <span data-ttu-id="a9759-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9759-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9759-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9759-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9759-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a9759-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9759-117">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9759-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9759-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9759-118">See also</span></span>

- [<span data-ttu-id="a9759-119">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9759-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="a9759-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a9759-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
