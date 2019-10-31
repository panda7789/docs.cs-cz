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
ms.openlocfilehash: e9846234f8217b822860c2400a54a91a651a0a56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129819"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="a8de4-102">ICorDebugMDA::GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="a8de4-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="a8de4-103">Načte identifikátor vlákna operačního systému (OS), na kterém je spuštěný pomocník spravovaného ladění (MDA) reprezentovaný [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a8de4-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8de4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8de4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8de4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8de4-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="a8de4-106">mimo Ukazatel na identifikátor vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="a8de4-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8de4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8de4-107">Remarks</span></span>  
 <span data-ttu-id="a8de4-108">Vlákno OS se používá místo ICorDebugThread a umožňuje v situacích, ve kterých je spuštěný MDA, buď v nativním vlákně, nebo ve spravovaném vlákně, které ještě nezadalo spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a8de4-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8de4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8de4-109">Requirements</span></span>  
 <span data-ttu-id="a8de4-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8de4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8de4-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8de4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8de4-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a8de4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8de4-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8de4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8de4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8de4-114">See also</span></span>

- [<span data-ttu-id="a8de4-115">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8de4-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="a8de4-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a8de4-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
