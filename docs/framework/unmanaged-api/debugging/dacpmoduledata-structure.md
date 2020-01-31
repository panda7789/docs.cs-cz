---
title: DacpModuleData – struktura
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b46a04d67f59c5031b5bd195cef4cc2275e1e5e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793800"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="00c37-102">DacpModuleData – struktura</span><span class="sxs-lookup"><span data-stu-id="00c37-102">DacpModuleData Structure</span></span>

<span data-ttu-id="00c37-103">Definuje přenosovou vyrovnávací paměť pro běhové informace modulu.</span><span class="sxs-lookup"><span data-stu-id="00c37-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="00c37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00c37-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="00c37-105">Členové</span><span class="sxs-lookup"><span data-stu-id="00c37-105">Members</span></span>

| <span data-ttu-id="00c37-106">Člen</span><span class="sxs-lookup"><span data-stu-id="00c37-106">Member</span></span>    | <span data-ttu-id="00c37-107">Popis</span><span class="sxs-lookup"><span data-stu-id="00c37-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="00c37-108">Adresa objektu modulu.</span><span class="sxs-lookup"><span data-stu-id="00c37-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="00c37-109">Ukazatel na soubor přenositelného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="00c37-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="00c37-110">Adresa základu načteného obrázku</span><span class="sxs-lookup"><span data-stu-id="00c37-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="00c37-111">Vyrovnávací paměť datové části pro další informace o modulu používané modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="00c37-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="00c37-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00c37-112">Remarks</span></span>

<span data-ttu-id="00c37-113">Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="00c37-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="00c37-114">Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="00c37-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="00c37-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00c37-115">Requirements</span></span>
<span data-ttu-id="00c37-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00c37-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="00c37-117">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="00c37-117">**Header:** None</span></span>  
<span data-ttu-id="00c37-118">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="00c37-118">**Library:** None</span></span>  
<span data-ttu-id="00c37-119">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="00c37-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="00c37-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00c37-120">See also</span></span>

- [<span data-ttu-id="00c37-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="00c37-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="00c37-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="00c37-122">Debugging Structures</span></span>](debugging-structures.md)
