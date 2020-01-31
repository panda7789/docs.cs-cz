---
title: Struktura DacpGetModuleAddress
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789205"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="a282c-102">Struktura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="a282c-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="a282c-103">Definuje kontejner pro požadavek na adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="a282c-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a282c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a282c-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="a282c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a282c-105">Members</span></span>

| <span data-ttu-id="a282c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a282c-106">Member</span></span>      | <span data-ttu-id="a282c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a282c-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="a282c-108">Ukazatel na modul.</span><span class="sxs-lookup"><span data-stu-id="a282c-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="a282c-109">Metody</span><span class="sxs-lookup"><span data-stu-id="a282c-109">Methods</span></span>

| <span data-ttu-id="a282c-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="a282c-110">Method</span></span>                                                                                               | <span data-ttu-id="a282c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a282c-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="a282c-112">Požadavek</span><span class="sxs-lookup"><span data-stu-id="a282c-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="a282c-113">Provede požadavek na naplnění struktury z dané běhové struktury.</span><span class="sxs-lookup"><span data-stu-id="a282c-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a282c-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a282c-114">Remarks</span></span>

<span data-ttu-id="a282c-115">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="a282c-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a282c-116">Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="a282c-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a282c-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a282c-117">Requirements</span></span>
<span data-ttu-id="a282c-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a282c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a282c-119">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="a282c-119">**Header:** None</span></span>  
<span data-ttu-id="a282c-120">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="a282c-120">**Library:** None</span></span>  
<span data-ttu-id="a282c-121">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a282c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a282c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a282c-122">See also</span></span>

- [<span data-ttu-id="a282c-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="a282c-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="a282c-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="a282c-124">Debugging Structures</span></span>](debugging-structures.md)
