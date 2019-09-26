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
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274297"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="e85b1-102">CLRDATA_IL_ADDRESS_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="e85b1-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="e85b1-103">Definuje mapování IL na adresu.</span><span class="sxs-lookup"><span data-stu-id="e85b1-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e85b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e85b1-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="e85b1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e85b1-105">Members</span></span>

| <span data-ttu-id="e85b1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e85b1-106">Member</span></span>         | <span data-ttu-id="e85b1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e85b1-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="e85b1-108">Posunutí IL pro rozsah obsažených adres</span><span class="sxs-lookup"><span data-stu-id="e85b1-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="e85b1-109">Počáteční adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e85b1-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="e85b1-110">Koncová adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e85b1-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="e85b1-111">Typ dat</span><span class="sxs-lookup"><span data-stu-id="e85b1-111">The type of the data.</span></span> <span data-ttu-id="e85b1-112">Tato hodnota se v tuto chvíli nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e85b1-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="e85b1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e85b1-113">Remarks</span></span>

<span data-ttu-id="e85b1-114">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="e85b1-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e85b1-115">Chcete-li jej použít, definujte strukturu, jak je uvedeno `CLRDATA_ADDRESS` výše, kde je 64-bit unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="e85b1-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="e85b1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e85b1-116">Requirements</span></span>

<span data-ttu-id="e85b1-117">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e85b1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e85b1-118">**Hlaviček** Žádné</span><span class="sxs-lookup"><span data-stu-id="e85b1-118">**Header:** None</span></span>  
<span data-ttu-id="e85b1-119">**Knihovna** Žádné</span><span class="sxs-lookup"><span data-stu-id="e85b1-119">**Library:** None</span></span>   
<span data-ttu-id="e85b1-120">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e85b1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e85b1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e85b1-121">See also</span></span>

- [<span data-ttu-id="e85b1-122">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="e85b1-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e85b1-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="e85b1-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="e85b1-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="e85b1-124">Debugging Structures</span></span>](debugging-structures.md)
