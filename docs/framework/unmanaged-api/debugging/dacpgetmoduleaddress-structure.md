---
title: DacpGetModuleAddress – struktura
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
ms.openlocfilehash: e460264e2393858c028ba51aec4a4f2c01649994
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860823"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="3c485-102">DacpGetModuleAddress – struktura</span><span class="sxs-lookup"><span data-stu-id="3c485-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="3c485-103">Definuje kontejner pro požadavek na adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="3c485-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3c485-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c485-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="3c485-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3c485-105">Members</span></span>

| <span data-ttu-id="3c485-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3c485-106">Member</span></span>      | <span data-ttu-id="3c485-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3c485-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="3c485-108">Ukazatel na modul.</span><span class="sxs-lookup"><span data-stu-id="3c485-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="3c485-109">Metody</span><span class="sxs-lookup"><span data-stu-id="3c485-109">Methods</span></span>

| <span data-ttu-id="3c485-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c485-110">Method</span></span>                                                                                               | <span data-ttu-id="3c485-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3c485-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="3c485-112">Žádost</span><span class="sxs-lookup"><span data-stu-id="3c485-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="3c485-113">Provede požadavek na naplnění struktury z dané běhové struktury.</span><span class="sxs-lookup"><span data-stu-id="3c485-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3c485-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c485-114">Remarks</span></span>

<span data-ttu-id="3c485-115">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="3c485-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3c485-116">Chcete-li jej použít, definujte strukturu, jak je uvedeno `CLRDATA_ADDRESS` výše, kde je 64-bit unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="3c485-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="3c485-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c485-117">Requirements</span></span>
<span data-ttu-id="3c485-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c485-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3c485-119">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="3c485-119">**Header:** None</span></span>  
<span data-ttu-id="3c485-120">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="3c485-120">**Library:** None</span></span>  
<span data-ttu-id="3c485-121">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3c485-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3c485-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c485-122">See also</span></span>

- [<span data-ttu-id="3c485-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="3c485-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="3c485-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="3c485-124">Debugging Structures</span></span>](debugging-structures.md)
