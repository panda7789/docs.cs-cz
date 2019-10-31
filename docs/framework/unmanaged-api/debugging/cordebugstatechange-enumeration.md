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
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133727"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="8e17a-102">Výčet CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="8e17a-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="8e17a-103">Popisuje množství dat uložených v mezipaměti, které je nutné zahodit na základě změn procesu.</span><span class="sxs-lookup"><span data-stu-id="8e17a-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e17a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e17a-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="8e17a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8e17a-105">Members</span></span>

| <span data-ttu-id="8e17a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8e17a-106">Member</span></span>            | <span data-ttu-id="8e17a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8e17a-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="8e17a-108">Proces dosáhl nového stavu paměti prostřednictvím dopředné spuštění.</span><span class="sxs-lookup"><span data-stu-id="8e17a-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="8e17a-109">Paměť procesu může být libovolně jiná než dříve.</span><span class="sxs-lookup"><span data-stu-id="8e17a-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8e17a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e17a-110">Remarks</span></span>

 <span data-ttu-id="8e17a-111">Člen `CorDebugStateChange` výčtu je uveden jako argument, pokud ladicí program volá metodu `ProcessStateChanged` buď pomocí [ICorDebugProcess4::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) nebo [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="8e17a-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="8e17a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e17a-112">Requirements</span></span>

 <span data-ttu-id="8e17a-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e17a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="8e17a-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8e17a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="8e17a-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8e17a-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="8e17a-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e17a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8e17a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e17a-117">See also</span></span>

- [<span data-ttu-id="8e17a-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="8e17a-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="8e17a-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="8e17a-119">Debugging</span></span>](index.md)
