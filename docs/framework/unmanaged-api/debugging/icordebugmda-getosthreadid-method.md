---
title: ICorDebugMDA::GetOSThreadId – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c38aa9cc891514a7f37dba47402c168060ec3727
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486092"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="7159d-102">ICorDebugMDA::GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="7159d-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="7159d-103">Získá identifikátor vlákna operačního systému (OS), na kterém pomocníka spravovaného ladění (MDA) reprezentovaný [icordebugmda –](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) provádí.</span><span class="sxs-lookup"><span data-stu-id="7159d-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7159d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7159d-104">Syntax</span></span>  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7159d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7159d-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="7159d-106">[out] Ukazatel na identifikátor vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="7159d-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7159d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7159d-107">Remarks</span></span>  
 <span data-ttu-id="7159d-108">Vlákna operačního systému používá místo ICorDebugThread k povolení pro situace, ve kterých se spustí MDA na nativní vlákna nebo na spravovaná vlákna, který ještě nebyl zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7159d-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7159d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7159d-109">Requirements</span></span>  
 <span data-ttu-id="7159d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7159d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7159d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7159d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7159d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7159d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7159d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7159d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7159d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7159d-114">See also</span></span>
- [<span data-ttu-id="7159d-115">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7159d-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="7159d-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7159d-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
