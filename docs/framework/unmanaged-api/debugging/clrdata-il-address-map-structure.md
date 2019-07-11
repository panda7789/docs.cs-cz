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
ms.openlocfilehash: 2f34ae3e6687027aeb75e7ea169487fc8cbda466
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741030"
---
# <a name="clrdatailaddressmap-structure"></a><span data-ttu-id="cde13-102">CLRDATA_IL_ADDRESS_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="cde13-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="cde13-103">Definuje mapování adresy IL.</span><span class="sxs-lookup"><span data-stu-id="cde13-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cde13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cde13-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="cde13-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cde13-105">Members</span></span>

| <span data-ttu-id="cde13-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cde13-106">Member</span></span>         | <span data-ttu-id="cde13-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cde13-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="cde13-108">Posun IL pro rozsah adres omezením</span><span class="sxs-lookup"><span data-stu-id="cde13-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="cde13-109">Počáteční adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cde13-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="cde13-110">Koncová adresa rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cde13-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="cde13-111">Typ data.</span><span class="sxs-lookup"><span data-stu-id="cde13-111">The type of the data.</span></span> <span data-ttu-id="cde13-112">Tato hodnota není aktuálně používá.</span><span class="sxs-lookup"><span data-stu-id="cde13-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="cde13-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cde13-113">Remarks</span></span>

<span data-ttu-id="cde13-114">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="cde13-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cde13-115">Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="cde13-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="cde13-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cde13-116">Requirements</span></span>

<span data-ttu-id="cde13-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cde13-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cde13-118">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="cde13-118">**Header:** None</span></span>  
<span data-ttu-id="cde13-119">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="cde13-119">**Library:** None</span></span>   
<span data-ttu-id="cde13-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cde13-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cde13-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cde13-121">See also</span></span>

- [<span data-ttu-id="cde13-122">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="cde13-122">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="cde13-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="cde13-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cde13-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="cde13-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
