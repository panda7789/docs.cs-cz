---
title: CLRDataSourceType Enumeration
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d26cf45a0243d61757af5d9d0c00cf135ae15bdf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740867"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="c7704-102">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="c7704-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="c7704-103">Obsahuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP struktury.</span><span class="sxs-lookup"><span data-stu-id="c7704-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c7704-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7704-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="c7704-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c7704-105">Members</span></span>

| <span data-ttu-id="c7704-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c7704-106">Member</span></span>                        | <span data-ttu-id="c7704-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c7704-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="c7704-108">K označení, že se nic jiného vztahuje</span><span class="sxs-lookup"><span data-stu-id="c7704-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="c7704-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7704-109">Remarks</span></span>

<span data-ttu-id="c7704-110">Tento výčet se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="c7704-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c7704-111">Pro použití je třeba definujte výčet definované výše ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="c7704-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="c7704-112">Toto je také s aliasem se přiřadila `CLRDATA_ENUM` jak je uvedeno v [běžné typy dat](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="c7704-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c7704-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7704-113">Requirements</span></span>

<span data-ttu-id="c7704-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7704-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c7704-115">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="c7704-115">**Header:** None</span></span>  
<span data-ttu-id="c7704-116">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="c7704-116">**Library:** None</span></span>  
<span data-ttu-id="c7704-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7704-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c7704-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7704-118">See also</span></span>

- [<span data-ttu-id="c7704-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="c7704-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c7704-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7704-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
