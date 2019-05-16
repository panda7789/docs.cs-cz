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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 621c5b1e32a1a21c2b0b883249c3b65fadceb5f2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632347"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="edaed-102">ICorDebugManagedCallback::Break – metoda</span><span class="sxs-lookup"><span data-stu-id="edaed-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="edaed-103">Upozorní ladicí program při <xref:System.Reflection.Emit.OpCodes.Break> instrukce v datovém proudu kód provádí.</span><span class="sxs-lookup"><span data-stu-id="edaed-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="edaed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edaed-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="edaed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edaed-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="edaed-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který obsahuje instrukce break.</span><span class="sxs-lookup"><span data-stu-id="edaed-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="edaed-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, které obsahuje instrukce break.</span><span class="sxs-lookup"><span data-stu-id="edaed-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="edaed-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="edaed-108">Requirements</span></span>

<span data-ttu-id="edaed-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edaed-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="edaed-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edaed-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="edaed-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edaed-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="edaed-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edaed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="edaed-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edaed-113">See also</span></span>

- [<span data-ttu-id="edaed-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="edaed-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
