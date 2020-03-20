---
title: CLRDATA_IL_ADDRESS_MAP – struktura
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179367"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="b68c1-102">CLRDATA_IL_ADDRESS_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="b68c1-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="b68c1-103">Definuje IL pro mapování adres.</span><span class="sxs-lookup"><span data-stu-id="b68c1-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b68c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b68c1-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="b68c1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b68c1-105">Members</span></span>

| <span data-ttu-id="b68c1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b68c1-106">Member</span></span>         | <span data-ttu-id="b68c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b68c1-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="b68c1-108">Il posun pro oblast obsažené adresy</span><span class="sxs-lookup"><span data-stu-id="b68c1-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="b68c1-109">Počáteční adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b68c1-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="b68c1-110">Koncová adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b68c1-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="b68c1-111">Typ dat.</span><span class="sxs-lookup"><span data-stu-id="b68c1-111">The type of the data.</span></span> <span data-ttu-id="b68c1-112">Tato hodnota se v současné době nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b68c1-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="b68c1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b68c1-113">Remarks</span></span>

<span data-ttu-id="b68c1-114">Tato struktura žije uvnitř runtime a není vystavena prostřednictvím žádné záhlaví nebo soubory knihovny.</span><span class="sxs-lookup"><span data-stu-id="b68c1-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b68c1-115">Chcete-li jej použít, definujte `CLRDATA_ADDRESS` strukturu, jak je uvedeno výše, kde je 64bitové nepodepsané celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b68c1-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="b68c1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b68c1-116">Requirements</span></span>

<span data-ttu-id="b68c1-117">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68c1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b68c1-118">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="b68c1-118">**Header:** None</span></span>  
<span data-ttu-id="b68c1-119">**Knihovna:** Žádné **verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b68c1-119">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b68c1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b68c1-120">See also</span></span>

- [<span data-ttu-id="b68c1-121">Výčet clrdatasourcetype</span><span class="sxs-lookup"><span data-stu-id="b68c1-121">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b68c1-122">ladění</span><span class="sxs-lookup"><span data-stu-id="b68c1-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="b68c1-123">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="b68c1-123">Debugging Structures</span></span>](debugging-structures.md)
