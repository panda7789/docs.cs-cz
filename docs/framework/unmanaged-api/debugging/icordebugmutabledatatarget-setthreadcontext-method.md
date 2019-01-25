---
title: ICorDebugMutableDataTarget::SetThreadContext Method
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee2ee66a5129bcf5f6c7c6881e50264b3c41773d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664470"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="2b11d-102">ICorDebugMutableDataTarget::SetThreadContext Method</span><span class="sxs-lookup"><span data-stu-id="2b11d-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="2b11d-103">Nastaví kontext (hodnot registru) pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="2b11d-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b11d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b11d-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b11d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b11d-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="2b11d-106">[in] Identifikátor vlákna operačního systému definovaný.</span><span class="sxs-lookup"><span data-stu-id="2b11d-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2b11d-107">[in] Velikost `pContext` vyrovnávací paměti k zapsání.</span><span class="sxs-lookup"><span data-stu-id="2b11d-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="2b11d-108">[in] Ukazatel na počet bajtů k zápisu.</span><span class="sxs-lookup"><span data-stu-id="2b11d-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b11d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b11d-109">Remarks</span></span>  
 <span data-ttu-id="2b11d-110">`SetThreadContext` Metoda aktualizuje aktuální kontext pro vlákno určené parametrem operačního systému definovaný `dwThreadID` argument.</span><span class="sxs-lookup"><span data-stu-id="2b11d-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="2b11d-111">Formát záznamu o kontextu je určen podle platformy indikován [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2b11d-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="2b11d-112">Na Windows, jde [kontextu](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) struktury.</span><span class="sxs-lookup"><span data-stu-id="2b11d-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b11d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b11d-113">Requirements</span></span>  
 <span data-ttu-id="2b11d-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b11d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b11d-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b11d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b11d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b11d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b11d-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b11d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b11d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b11d-118">See also</span></span>
- [<span data-ttu-id="2b11d-119">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b11d-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="2b11d-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2b11d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
