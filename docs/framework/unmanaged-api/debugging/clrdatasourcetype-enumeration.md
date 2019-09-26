---
title: Výčet CLRDataSourceType
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
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274098"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="83ad7-102">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="83ad7-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="83ad7-103">Poskytuje hodnoty, které jsou používány strukturou CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="83ad7-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="83ad7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83ad7-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="83ad7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="83ad7-105">Members</span></span>

| <span data-ttu-id="83ad7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="83ad7-106">Member</span></span>                        | <span data-ttu-id="83ad7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="83ad7-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="83ad7-108">Označení, že neplatí nic jiného</span><span class="sxs-lookup"><span data-stu-id="83ad7-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="83ad7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83ad7-109">Remarks</span></span>

<span data-ttu-id="83ad7-110">Tento výčet je v modulu runtime a není vystavený prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="83ad7-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="83ad7-111">Chcete-li jej použít, definujte výčet definovaný výše v kódu.</span><span class="sxs-lookup"><span data-stu-id="83ad7-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="83ad7-112">To je také alias na `CLRDATA_ENUM` to, jak je uvedeno v [Common data types](../common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="83ad7-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="83ad7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83ad7-113">Requirements</span></span>

<span data-ttu-id="83ad7-114">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83ad7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="83ad7-115">**Hlaviček** Žádné</span><span class="sxs-lookup"><span data-stu-id="83ad7-115">**Header:** None</span></span>  
<span data-ttu-id="83ad7-116">**Knihovna** Žádné</span><span class="sxs-lookup"><span data-stu-id="83ad7-116">**Library:** None</span></span>  
<span data-ttu-id="83ad7-117">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="83ad7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="83ad7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83ad7-118">See also</span></span>

- [<span data-ttu-id="83ad7-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="83ad7-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="83ad7-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="83ad7-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
