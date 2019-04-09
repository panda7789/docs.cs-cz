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
ms.openlocfilehash: cbea6c0562c68ae5d18247dc97bc53eb9dfbfd7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104102"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="a1d30-102">Struktura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="a1d30-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="a1d30-103">Definuje kontejner pro žádost o adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="a1d30-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a1d30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1d30-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="a1d30-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a1d30-105">Members</span></span>

| <span data-ttu-id="a1d30-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a1d30-106">Member</span></span>      | <span data-ttu-id="a1d30-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1d30-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="a1d30-108">Ukazatel na modul.</span><span class="sxs-lookup"><span data-stu-id="a1d30-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="a1d30-109">Metody</span><span class="sxs-lookup"><span data-stu-id="a1d30-109">Methods</span></span>

| <span data-ttu-id="a1d30-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1d30-110">Method</span></span>                                                                                               | <span data-ttu-id="a1d30-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a1d30-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="a1d30-112">Request</span><span class="sxs-lookup"><span data-stu-id="a1d30-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="a1d30-113">Provede požadavek na naplnit struktura ze struktury daného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a1d30-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a1d30-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1d30-114">Remarks</span></span>

<span data-ttu-id="a1d30-115">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="a1d30-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a1d30-116">Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="a1d30-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1d30-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1d30-117">Requirements</span></span>
<span data-ttu-id="a1d30-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1d30-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a1d30-119">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="a1d30-119">**Header:** None</span></span>  
<span data-ttu-id="a1d30-120">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="a1d30-120">**Library:** None</span></span>  
**<span data-ttu-id="a1d30-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a1d30-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="a1d30-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1d30-122">See also</span></span>

- [<span data-ttu-id="a1d30-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="a1d30-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="a1d30-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="a1d30-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
