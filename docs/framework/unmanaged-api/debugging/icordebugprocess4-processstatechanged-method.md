---
title: Metoda ICorDebugProcess4::ProcessStateChanged
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178633"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="52373-102">Metoda ICorDebugProcess4::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="52373-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="52373-103">Upozorní kanál ICorDebug, že ladicí program mimo proces pokračuje v provádění ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="52373-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="52373-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52373-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="52373-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52373-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="52373-106">[v] Člen [cordebugStateChange výčtu](cordebugstatechange-enumeration.md) popisující změnu ve stavu provádění procesu.</span><span class="sxs-lookup"><span data-stu-id="52373-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="52373-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52373-107">Remarks</span></span>

<span data-ttu-id="52373-108">Poskytnutá metoda je součástí `ICorDebugProcess4` rozhraní a odpovídá čtvrtému slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="52373-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="52373-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52373-109">Requirements</span></span>

 <span data-ttu-id="52373-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52373-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="52373-111">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="52373-111">**Header:** None</span></span>

 <span data-ttu-id="52373-112">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="52373-112">**Library:** None</span></span>

 <span data-ttu-id="52373-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52373-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="52373-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="52373-114">See also</span></span>

- [<span data-ttu-id="52373-115">ICorDebugProcess4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52373-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="52373-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52373-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="52373-117">ladění</span><span class="sxs-lookup"><span data-stu-id="52373-117">Debugging</span></span>](index.md)
