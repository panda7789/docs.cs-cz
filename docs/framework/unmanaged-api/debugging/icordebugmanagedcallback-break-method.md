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
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212461"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="41689-102">ICorDebugManagedCallback::Break – metoda</span><span class="sxs-lookup"><span data-stu-id="41689-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="41689-103">Upozorní ladicí program, když <xref:System.Reflection.Emit.OpCodes.Break> je proveden pokyn v datovém proudu kódu.</span><span class="sxs-lookup"><span data-stu-id="41689-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="41689-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41689-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="41689-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41689-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="41689-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující instrukci Break.</span><span class="sxs-lookup"><span data-stu-id="41689-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="41689-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, které obsahuje instrukci Break.</span><span class="sxs-lookup"><span data-stu-id="41689-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="41689-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41689-108">Requirements</span></span>

<span data-ttu-id="41689-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41689-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="41689-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41689-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="41689-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41689-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="41689-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41689-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="41689-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="41689-113">See also</span></span>

- [<span data-ttu-id="41689-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41689-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
