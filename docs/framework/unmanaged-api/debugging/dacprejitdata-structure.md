---
title: DacpReJitData – struktura
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
ms.openlocfilehash: 46031f29da6916eeaeea863ebef6924a720d7155
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793819"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="7e945-102">DacpReJitData – struktura</span><span class="sxs-lookup"><span data-stu-id="7e945-102">DacpReJitData Structure</span></span>

<span data-ttu-id="7e945-103">Definuje základní informace o dané metodě instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="7e945-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7e945-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e945-104">Syntax</span></span>

```cpp
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

## <a name="members"></a><span data-ttu-id="7e945-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7e945-105">Members</span></span>

| <span data-ttu-id="7e945-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7e945-106">Member</span></span>           | <span data-ttu-id="7e945-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7e945-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="7e945-108">Číslo revize ReJit pro metodu.</span><span class="sxs-lookup"><span data-stu-id="7e945-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="7e945-109">Příznak označující aktuální stav instrumentace ReJit metody pro danou verzi.</span><span class="sxs-lookup"><span data-stu-id="7e945-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="7e945-110">Základní adresa implementace rejitted metody.</span><span class="sxs-lookup"><span data-stu-id="7e945-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="7e945-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e945-111">Remarks</span></span>

<span data-ttu-id="7e945-112">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="7e945-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="7e945-113">Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="7e945-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="7e945-114">Pokud nepoužíváte kompilátory od Microsoftu, musí být struktura také definovaná pomocí `ms_struct` balení.</span><span class="sxs-lookup"><span data-stu-id="7e945-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e945-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e945-115">Requirements</span></span>
<span data-ttu-id="7e945-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e945-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7e945-117">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="7e945-117">**Header:** None</span></span>  
<span data-ttu-id="7e945-118">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="7e945-118">**Library:** None</span></span>  
<span data-ttu-id="7e945-119">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7e945-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7e945-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e945-120">See also</span></span>

- [<span data-ttu-id="7e945-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="7e945-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="7e945-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="7e945-122">Debugging Structures</span></span>](debugging-structures.md)
