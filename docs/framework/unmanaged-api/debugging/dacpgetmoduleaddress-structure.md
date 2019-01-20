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
ms.openlocfilehash: ca9ce04e9a4770d46f88e10785f4dafd044c9212
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416072"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="b316f-102">Struktura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="b316f-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="b316f-103">Definuje kontejner pro žádost o adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="b316f-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b316f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b316f-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="b316f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b316f-105">Members</span></span>

| <span data-ttu-id="b316f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b316f-106">Member</span></span>      | <span data-ttu-id="b316f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b316f-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="b316f-108">Ukazatel na modul.</span><span class="sxs-lookup"><span data-stu-id="b316f-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="b316f-109">Metody</span><span class="sxs-lookup"><span data-stu-id="b316f-109">Methods</span></span>

| <span data-ttu-id="b316f-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="b316f-110">Method</span></span>                                                                                               | <span data-ttu-id="b316f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b316f-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="b316f-112">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b316f-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="b316f-113">Provede požadavek na naplnit struktura ze struktury daného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b316f-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b316f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b316f-114">Remarks</span></span>

<span data-ttu-id="b316f-115">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="b316f-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b316f-116">Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="b316f-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="b316f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b316f-117">Requirements</span></span>
<span data-ttu-id="b316f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b316f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b316f-119">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="b316f-119">**Header:** None</span></span>  
<span data-ttu-id="b316f-120">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="b316f-120">**Library:** None</span></span>  
<span data-ttu-id="b316f-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b316f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b316f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b316f-122">See Also</span></span>
- [<span data-ttu-id="b316f-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="b316f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="b316f-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="b316f-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
