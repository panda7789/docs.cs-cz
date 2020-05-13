---
title: ICorDebugProcess4::P rocessStateChanged – metoda
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213566"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="5353c-102">ICorDebugProcess4::P rocessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="5353c-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="5353c-103">Upozorní kanál ICorDebug, že proces ladicího programu mimo proces pokračuje v provádění laděného objektu.</span><span class="sxs-lookup"><span data-stu-id="5353c-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="5353c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5353c-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="5353c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5353c-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="5353c-106">pro Člen [výčtu CorDebugStateChange](cordebugstatechange-enumeration.md) popisující změnu stavu provádění procesu.</span><span class="sxs-lookup"><span data-stu-id="5353c-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="5353c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5353c-107">Remarks</span></span>

<span data-ttu-id="5353c-108">Poskytnutá metoda je součástí `ICorDebugProcess4` rozhraní a odpovídá čtvrtému slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="5353c-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5353c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5353c-109">Requirements</span></span>

 <span data-ttu-id="5353c-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5353c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="5353c-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="5353c-111">**Header:** None</span></span>

 <span data-ttu-id="5353c-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="5353c-112">**Library:** None</span></span>

 <span data-ttu-id="5353c-113">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5353c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5353c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5353c-114">See also</span></span>

- [<span data-ttu-id="5353c-115">ICorDebugProcess4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5353c-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="5353c-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5353c-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5353c-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="5353c-117">Debugging</span></span>](index.md)
