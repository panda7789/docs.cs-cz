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
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739595"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="f79df-102">Výčet CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="f79df-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="f79df-103">Popisuje množství dat uložených v mezipaměti, který musí být odstraněn podle změn do procesu.</span><span class="sxs-lookup"><span data-stu-id="f79df-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="f79df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f79df-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="f79df-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f79df-105">Members</span></span>

| <span data-ttu-id="f79df-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f79df-106">Member</span></span>            | <span data-ttu-id="f79df-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f79df-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="f79df-108">Proces byl dosažen nový stav paměti prostřednictvím dopředné spuštění.</span><span class="sxs-lookup"><span data-stu-id="f79df-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="f79df-109">Paměť procesu může být libovolně jiný než dříve.</span><span class="sxs-lookup"><span data-stu-id="f79df-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f79df-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f79df-110">Remarks</span></span>

 <span data-ttu-id="f79df-111">Členem `CorDebugStateChange` výčtu je zadaný jako argument při volání ladicího programu `ProcessStateChanged` metoda buď pomocí [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) nebo [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="f79df-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="f79df-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f79df-112">Requirements</span></span>

 <span data-ttu-id="f79df-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f79df-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="f79df-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f79df-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="f79df-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f79df-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="f79df-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f79df-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f79df-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f79df-117">See also</span></span>

- [<span data-ttu-id="f79df-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="f79df-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="f79df-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="f79df-119">Debugging</span></span>](index.md)
