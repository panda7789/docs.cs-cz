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
ms.openlocfilehash: 36651de5053e994103f79c9021e8e18e126f91fa
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416069"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="acb90-102">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="acb90-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="acb90-103">Obsahuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP struktury.</span><span class="sxs-lookup"><span data-stu-id="acb90-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="acb90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acb90-104">Syntax</span></span>

```
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="acb90-105">Členové</span><span class="sxs-lookup"><span data-stu-id="acb90-105">Members</span></span>

| <span data-ttu-id="acb90-106">Člen</span><span class="sxs-lookup"><span data-stu-id="acb90-106">Member</span></span>                        | <span data-ttu-id="acb90-107">Popis</span><span class="sxs-lookup"><span data-stu-id="acb90-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="acb90-108">K označení, že se nic jiného vztahuje</span><span class="sxs-lookup"><span data-stu-id="acb90-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="acb90-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acb90-109">Remarks</span></span>

<span data-ttu-id="acb90-110">Tento výčet se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="acb90-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="acb90-111">Pro použití je třeba definujte výčet definované výše ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="acb90-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="acb90-112">Toto je také s aliasem se přiřadila `CLRDATA_ENUM` jak je uvedeno v [běžné typy dat](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="acb90-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="acb90-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acb90-113">Requirements</span></span>

<span data-ttu-id="acb90-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb90-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="acb90-115">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="acb90-115">**Header:** None</span></span>  
<span data-ttu-id="acb90-116">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="acb90-116">**Library:** None</span></span>  
<span data-ttu-id="acb90-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="acb90-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="acb90-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="acb90-118">See Also</span></span>

- [<span data-ttu-id="acb90-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="acb90-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="acb90-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="acb90-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
