---
title: Struktura CLRDATA_ADDRESS_RANGE
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
ms.openlocfilehash: 484ca79483fc4a5d8f0d1cf2cd5a961c297249e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654799"
---
# <a name="clrdataaddressrange-structure"></a><span data-ttu-id="e7300-102">Struktura CLRDATA_ADDRESS_RANGE</span><span class="sxs-lookup"><span data-stu-id="e7300-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="e7300-103">Definuje rozsah adres.</span><span class="sxs-lookup"><span data-stu-id="e7300-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e7300-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7300-104">Syntax</span></span>

```
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="e7300-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e7300-105">Members</span></span>

| <span data-ttu-id="e7300-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e7300-106">Member</span></span>         | <span data-ttu-id="e7300-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e7300-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="e7300-108">Počáteční adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e7300-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="e7300-109">Koncová adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e7300-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="e7300-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7300-110">Remarks</span></span>

<span data-ttu-id="e7300-111">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="e7300-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e7300-112">Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="e7300-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7300-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7300-113">Requirements</span></span>

<span data-ttu-id="e7300-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7300-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e7300-115">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="e7300-115">**Header:** None</span></span>  
<span data-ttu-id="e7300-116">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="e7300-116">**Library:** None</span></span>  
<span data-ttu-id="e7300-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e7300-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e7300-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7300-118">See also</span></span>

- [<span data-ttu-id="e7300-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="e7300-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e7300-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="e7300-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
