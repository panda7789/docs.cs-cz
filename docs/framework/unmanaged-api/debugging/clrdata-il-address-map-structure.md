---
title: CLRDATA_IL_ADDRESS_MAP Structure
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
ms.openlocfilehash: 94ebef007cf2893b63383aa4657d382728d3c759
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416073"
---
# <a name="clrdatailaddressmap-structure"></a><span data-ttu-id="3deeb-102">CLRDATA_IL_ADDRESS_MAP Structure</span><span class="sxs-lookup"><span data-stu-id="3deeb-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="3deeb-103">Definuje mapování adresy IL.</span><span class="sxs-lookup"><span data-stu-id="3deeb-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3deeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3deeb-104">Syntax</span></span>

```
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="3deeb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3deeb-105">Members</span></span>

| <span data-ttu-id="3deeb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3deeb-106">Member</span></span>         | <span data-ttu-id="3deeb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3deeb-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="3deeb-108">Posun IL pro rozsah adres omezením</span><span class="sxs-lookup"><span data-stu-id="3deeb-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="3deeb-109">Počáteční adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="3deeb-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="3deeb-110">Koncová adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="3deeb-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="3deeb-111">Typ data.</span><span class="sxs-lookup"><span data-stu-id="3deeb-111">The type of the data.</span></span> <span data-ttu-id="3deeb-112">Tato hodnota není aktuálně používá.</span><span class="sxs-lookup"><span data-stu-id="3deeb-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="3deeb-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3deeb-113">Remarks</span></span>

<span data-ttu-id="3deeb-114">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="3deeb-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3deeb-115">Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="3deeb-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="3deeb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3deeb-116">Requirements</span></span>

<span data-ttu-id="3deeb-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3deeb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3deeb-118">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3deeb-118">**Header:** None</span></span>  
<span data-ttu-id="3deeb-119">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3deeb-119">**Library:** None</span></span>   
<span data-ttu-id="3deeb-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3deeb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3deeb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3deeb-121">See Also</span></span>

- [<span data-ttu-id="3deeb-122">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="3deeb-122">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="3deeb-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="3deeb-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3deeb-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="3deeb-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
