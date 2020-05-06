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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795687"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="86e31-102">Výčet CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="86e31-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="86e31-103">Popisuje množství dat uložených v mezipaměti, které je nutné zahodit na základě změn procesu.</span><span class="sxs-lookup"><span data-stu-id="86e31-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="86e31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86e31-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="86e31-105">Členové</span><span class="sxs-lookup"><span data-stu-id="86e31-105">Members</span></span>

| <span data-ttu-id="86e31-106">Člen</span><span class="sxs-lookup"><span data-stu-id="86e31-106">Member</span></span>            | <span data-ttu-id="86e31-107">Popis</span><span class="sxs-lookup"><span data-stu-id="86e31-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="86e31-108">Proces dosáhl nového stavu paměti prostřednictvím dopředné spuštění.</span><span class="sxs-lookup"><span data-stu-id="86e31-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="86e31-109">Paměť procesu může být libovolně jiná než dříve.</span><span class="sxs-lookup"><span data-stu-id="86e31-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="86e31-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86e31-110">Remarks</span></span>

 <span data-ttu-id="86e31-111">Člen `CorDebugStateChange` výčtu je uveden jako argument, pokud ladicí program volá `ProcessStateChanged` metodu buď pomocí [ICorDebugProcess4::P rocessStateChanged](icordebugprocess4-processstatechanged-method.md) nebo [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="86e31-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="86e31-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86e31-112">Requirements</span></span>

 <span data-ttu-id="86e31-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e31-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="86e31-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86e31-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="86e31-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="86e31-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="86e31-116">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e31-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="86e31-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="86e31-117">See also</span></span>

- [<span data-ttu-id="86e31-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="86e31-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="86e31-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="86e31-119">Debugging</span></span>](index.md)
