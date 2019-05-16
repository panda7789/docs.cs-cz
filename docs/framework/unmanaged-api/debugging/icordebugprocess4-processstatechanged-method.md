---
title: ICorDebugProcess4::ProcessStateChanged Method
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
ms.openlocfilehash: 5e3a6714489e2051a09b5855ab9f911ef2f57450
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632289"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="f8b29-102">ICorDebugProcess4::ProcessStateChanged Method</span><span class="sxs-lookup"><span data-stu-id="f8b29-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="f8b29-103">Upozorní ICorDebug kanálu, že je vzdálený ladicí program procesu pokračovat v provádění od laděného objektu.</span><span class="sxs-lookup"><span data-stu-id="f8b29-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8b29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8b29-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="f8b29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8b29-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="f8b29-106">[in] Člen [výčet CorDebugStateChange](cordebugstatechange-enumeration.md) popisující změnu stavu spuštění procesu.</span><span class="sxs-lookup"><span data-stu-id="f8b29-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8b29-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8b29-107">Remarks</span></span>

<span data-ttu-id="f8b29-108">Zadaná metoda je součástí `ICorDebugProcess4` rozhraní a odpovídá čtvrtý pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="f8b29-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8b29-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8b29-109">Requirements</span></span>

 <span data-ttu-id="f8b29-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8b29-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="f8b29-111">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="f8b29-111">**Header:** None</span></span>

 <span data-ttu-id="f8b29-112">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="f8b29-112">**Library:** None</span></span>
 
 <span data-ttu-id="f8b29-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8b29-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f8b29-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8b29-114">See also</span></span>

- [<span data-ttu-id="f8b29-115">ICorDebugProcess4 Interface</span><span class="sxs-lookup"><span data-stu-id="f8b29-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="f8b29-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f8b29-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f8b29-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="f8b29-117">Debugging</span></span>](index.md)
