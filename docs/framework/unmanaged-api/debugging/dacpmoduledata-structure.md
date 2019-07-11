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
ms.openlocfilehash: 2e27082ba4c35bc10eb65139b2af6c81c10d79a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739118"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="85f48-102">DacpModuleData – struktura</span><span class="sxs-lookup"><span data-stu-id="85f48-102">DacpModuleData Structure</span></span>

<span data-ttu-id="85f48-103">Definuje přenos vyrovnávací paměť pro informace o modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="85f48-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="85f48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85f48-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="85f48-105">Členové</span><span class="sxs-lookup"><span data-stu-id="85f48-105">Members</span></span>

| <span data-ttu-id="85f48-106">Člen</span><span class="sxs-lookup"><span data-stu-id="85f48-106">Member</span></span>    | <span data-ttu-id="85f48-107">Popis</span><span class="sxs-lookup"><span data-stu-id="85f48-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="85f48-108">Adresa objektu modulu.</span><span class="sxs-lookup"><span data-stu-id="85f48-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="85f48-109">Ukazatel na soubor (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="85f48-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="85f48-110">Je základní adresa načíst obrázek.</span><span class="sxs-lookup"><span data-stu-id="85f48-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="85f48-111">Vyrovnávací paměť datové části pro informace o dalších modulu se používají modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="85f48-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="85f48-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85f48-112">Remarks</span></span>

<span data-ttu-id="85f48-113">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="85f48-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="85f48-114">Pro použití je třeba definujte strukturu jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="85f48-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="85f48-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85f48-115">Requirements</span></span>
<span data-ttu-id="85f48-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85f48-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="85f48-117">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="85f48-117">**Header:** None</span></span>  
<span data-ttu-id="85f48-118">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="85f48-118">**Library:** None</span></span>  
<span data-ttu-id="85f48-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="85f48-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="85f48-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85f48-120">See also</span></span>

- [<span data-ttu-id="85f48-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="85f48-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="85f48-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="85f48-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
