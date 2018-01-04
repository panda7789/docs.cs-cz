---
title: "ICorDebugRegisterSet::GetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fba96f9d86f1df5c0800c8cafb9c7fd1b0a6f8c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="847b3-102">ICorDebugRegisterSet::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="847b3-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="847b3-103">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="847b3-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="847b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="847b3-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="847b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="847b3-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="847b3-106">[v] Velikost v bajtech z `context` pole.</span><span class="sxs-lookup"><span data-stu-id="847b3-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="847b3-107">[ve out] Pole bajtů, které tvoří Win32 `CONTEXT` strukturu pro aktuální platformě.</span><span class="sxs-lookup"><span data-stu-id="847b3-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="847b3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="847b3-108">Remarks</span></span>  
 <span data-ttu-id="847b3-109">Ladicí program by měly volat tuto funkci místo Win32 `GetThreadContext` fungovat, protože vlákno může být ve stavu "napadenému", kde byl dočasně změnit jeho kontextu.</span><span class="sxs-lookup"><span data-stu-id="847b3-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="847b3-110">Je s daty vrácenými Win32 `CONTEXT` strukturu pro aktuální platformě.</span><span class="sxs-lookup"><span data-stu-id="847b3-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="847b3-111">Pro snímky mimo úroveň listu, klienti kontrolou která registruje jsou platné pomocí [icordebugregisterset::getregistersavailable –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="847b3-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="847b3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="847b3-112">Requirements</span></span>  
 <span data-ttu-id="847b3-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="847b3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="847b3-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="847b3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="847b3-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="847b3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="847b3-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="847b3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="847b3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="847b3-117">See Also</span></span>  
 [<span data-ttu-id="847b3-118">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="847b3-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="847b3-119">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="847b3-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
