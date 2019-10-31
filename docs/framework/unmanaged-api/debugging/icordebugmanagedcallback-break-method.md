---
title: ICorDebugManagedCallback::Break – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: efc9de050e34867c14f8e85e091e2b959c30f213
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122588"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="c8cbe-102">ICorDebugManagedCallback::Break – metoda</span><span class="sxs-lookup"><span data-stu-id="c8cbe-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="c8cbe-103">Upozorní ladicí program, když se spustí instrukce <xref:System.Reflection.Emit.OpCodes.Break> v datovém proudu kódu.</span><span class="sxs-lookup"><span data-stu-id="c8cbe-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8cbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8cbe-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="c8cbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8cbe-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="c8cbe-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující instrukci Break.</span><span class="sxs-lookup"><span data-stu-id="c8cbe-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="c8cbe-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, které obsahuje instrukci Break.</span><span class="sxs-lookup"><span data-stu-id="c8cbe-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="c8cbe-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8cbe-108">Requirements</span></span>

<span data-ttu-id="c8cbe-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8cbe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="c8cbe-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c8cbe-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="c8cbe-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c8cbe-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c8cbe-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8cbe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c8cbe-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8cbe-113">See also</span></span>

- [<span data-ttu-id="c8cbe-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8cbe-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
