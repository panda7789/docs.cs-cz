---
title: Výčet CorDebugStateChange
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a29022d3ebad37322aef9826f10689d2b5b06b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221131"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="aef36-102">Výčet CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="aef36-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="aef36-103">Popisuje množství dat uložených v mezipaměti, který musí být odstraněn podle změn do procesu.</span><span class="sxs-lookup"><span data-stu-id="aef36-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="aef36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aef36-104">Syntax</span></span>

```
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="aef36-105">Členové</span><span class="sxs-lookup"><span data-stu-id="aef36-105">Members</span></span>

| <span data-ttu-id="aef36-106">Člen</span><span class="sxs-lookup"><span data-stu-id="aef36-106">Member</span></span>            | <span data-ttu-id="aef36-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aef36-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="aef36-108">Proces byl dosažen nový stav paměti prostřednictvím dopředné spuštění.</span><span class="sxs-lookup"><span data-stu-id="aef36-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="aef36-109">Paměť procesu může být libovolně jiný než dříve.</span><span class="sxs-lookup"><span data-stu-id="aef36-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="aef36-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aef36-110">Remarks</span></span>

 <span data-ttu-id="aef36-111">Členem `CorDebugStateChange` výčtu je zadaný jako argument při volání ladicího programu `ProcessStateChanged` metoda buď pomocí [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) nebo [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="aef36-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="aef36-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aef36-112">Requirements</span></span>

 <span data-ttu-id="aef36-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aef36-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="aef36-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aef36-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="aef36-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aef36-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="aef36-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef36-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aef36-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aef36-117">See also</span></span>

- [<span data-ttu-id="aef36-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="aef36-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="aef36-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="aef36-119">Debugging</span></span>](index.md)
