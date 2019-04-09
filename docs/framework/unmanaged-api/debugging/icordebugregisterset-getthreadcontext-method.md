---
title: ICorDebugRegisterSet::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fecbcff0fd124b94aeeecf82e23d9875c34ebb9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091574"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="31655-102">ICorDebugRegisterSet::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="31655-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="31655-103">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="31655-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31655-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31655-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31655-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31655-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="31655-106">[in] Velikost v bajtech, nástroje `context` pole.</span><span class="sxs-lookup"><span data-stu-id="31655-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="31655-107">[out v] Pole bajtů, které tvoří Win32 `CONTEXT` strukturu pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="31655-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31655-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31655-108">Remarks</span></span>  
 <span data-ttu-id="31655-109">Ladicí program by měly volat tuto funkci místo Win32 `GetThreadContext` fungovat, protože vlákno může být ve stavu "napadenému", kde byl dočasně změní jeho kontextu.</span><span class="sxs-lookup"><span data-stu-id="31655-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="31655-110">Data vrácená je Win32 `CONTEXT` strukturu pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="31655-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="31655-111">Pro snímky mimo úroveň listu, klienti s kontrolou registrů, které jsou platné pomocí [icordebugregisterset::getregistersavailable –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="31655-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31655-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31655-112">Requirements</span></span>  
 <span data-ttu-id="31655-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31655-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31655-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31655-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31655-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31655-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="31655-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="31655-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="31655-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31655-117">See also</span></span>

- [<span data-ttu-id="31655-118">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31655-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="31655-119">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31655-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
