---
title: CLRDATA_ADDRESS_RANGE – struktura
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274300"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="a79d2-102">CLRDATA_ADDRESS_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="a79d2-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="a79d2-103">Definuje rozsah adres.</span><span class="sxs-lookup"><span data-stu-id="a79d2-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a79d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a79d2-104">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="a79d2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a79d2-105">Members</span></span>

| <span data-ttu-id="a79d2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a79d2-106">Member</span></span>         | <span data-ttu-id="a79d2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a79d2-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="a79d2-108">Počáteční adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="a79d2-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="a79d2-109">Koncová adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="a79d2-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="a79d2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a79d2-110">Remarks</span></span>

<span data-ttu-id="a79d2-111">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="a79d2-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a79d2-112">Chcete-li jej použít, definujte strukturu, jak je uvedeno `CLRDATA_ADDRESS` výše, kde je 64-bit unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="a79d2-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a79d2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a79d2-113">Requirements</span></span>

<span data-ttu-id="a79d2-114">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a79d2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a79d2-115">**Hlaviček** Žádné</span><span class="sxs-lookup"><span data-stu-id="a79d2-115">**Header:** None</span></span>  
<span data-ttu-id="a79d2-116">**Knihovna** Žádné</span><span class="sxs-lookup"><span data-stu-id="a79d2-116">**Library:** None</span></span>  
<span data-ttu-id="a79d2-117">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a79d2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a79d2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a79d2-118">See also</span></span>

- [<span data-ttu-id="a79d2-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="a79d2-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="a79d2-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="a79d2-120">Debugging Structures</span></span>](debugging-structures.md)
