---
title: DacpReJitData Structure
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a2850add9acb2f7c5297ac6956e349c9277be291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122795"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="94661-102">DacpReJitData Structure</span><span class="sxs-lookup"><span data-stu-id="94661-102">DacpReJitData Structure</span></span>

<span data-ttu-id="94661-103">Definuje základní informace o dané metody instrumentována profileru.</span><span class="sxs-lookup"><span data-stu-id="94661-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="94661-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94661-104">Syntax</span></span>

```
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="94661-105">Členové</span><span class="sxs-lookup"><span data-stu-id="94661-105">Members</span></span>

| <span data-ttu-id="94661-106">Člen</span><span class="sxs-lookup"><span data-stu-id="94661-106">Member</span></span>           | <span data-ttu-id="94661-107">Popis</span><span class="sxs-lookup"><span data-stu-id="94661-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="94661-108">Číslo revize ReJit pro metodu.</span><span class="sxs-lookup"><span data-stu-id="94661-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="94661-109">Příznak označující aktuální stav metody instrumentace ReJit pro danou verzi.</span><span class="sxs-lookup"><span data-stu-id="94661-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="94661-110">Základní adresa rejitted implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="94661-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="94661-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94661-111">Remarks</span></span>

<span data-ttu-id="94661-112">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="94661-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="94661-113">Pro použití je třeba definujte strukturu jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="94661-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="94661-114">Struktura musí být také definován pomocí `ms_struct` balení, není-li pomocí kompilátorů Microsoft.</span><span class="sxs-lookup"><span data-stu-id="94661-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="94661-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94661-115">Requirements</span></span>
<span data-ttu-id="94661-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94661-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="94661-117">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="94661-117">**Header:** None</span></span>  
<span data-ttu-id="94661-118">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="94661-118">**Library:** None</span></span>  
<span data-ttu-id="94661-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="94661-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="94661-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94661-120">See also</span></span>

- [<span data-ttu-id="94661-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="94661-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="94661-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="94661-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
