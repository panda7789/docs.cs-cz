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
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179191"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="5d04d-102">DacpModuleData – struktura</span><span class="sxs-lookup"><span data-stu-id="5d04d-102">DacpModuleData Structure</span></span>

<span data-ttu-id="5d04d-103">Definuje vyrovnávací paměť přenosu pro informace modulu za běhu.</span><span class="sxs-lookup"><span data-stu-id="5d04d-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5d04d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d04d-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="5d04d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5d04d-105">Members</span></span>

| <span data-ttu-id="5d04d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5d04d-106">Member</span></span>    | <span data-ttu-id="5d04d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5d04d-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="5d04d-108">Adresa objektu modulu.</span><span class="sxs-lookup"><span data-stu-id="5d04d-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="5d04d-109">Ukazatel na přenosný spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="5d04d-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="5d04d-110">Adresa základny načteného obrázku.</span><span class="sxs-lookup"><span data-stu-id="5d04d-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="5d04d-111">Vyrovnávací paměť datové části pro další informace o modulu používané modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="5d04d-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5d04d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d04d-112">Remarks</span></span>

<span data-ttu-id="5d04d-113">Tato struktura žije uvnitř runtime a není vystavena prostřednictvím žádné záhlaví nebo soubory knihovny.</span><span class="sxs-lookup"><span data-stu-id="5d04d-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="5d04d-114">Chcete-li jej použít, definujte strukturu, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="5d04d-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d04d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d04d-115">Requirements</span></span>
<span data-ttu-id="5d04d-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d04d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5d04d-117">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="5d04d-117">**Header:** None</span></span>  
<span data-ttu-id="5d04d-118">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="5d04d-118">**Library:** None</span></span>  
<span data-ttu-id="5d04d-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5d04d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5d04d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d04d-120">See also</span></span>

- [<span data-ttu-id="5d04d-121">ladění</span><span class="sxs-lookup"><span data-stu-id="5d04d-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="5d04d-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="5d04d-122">Debugging Structures</span></span>](debugging-structures.md)
