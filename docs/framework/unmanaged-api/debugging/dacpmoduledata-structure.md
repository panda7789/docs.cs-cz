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
ms.openlocfilehash: 752d87c5f4a6b8d854a06be8962ee754cdd4622d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131999"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="cdfa5-102">DacpModuleData – struktura</span><span class="sxs-lookup"><span data-stu-id="cdfa5-102">DacpModuleData Structure</span></span>

<span data-ttu-id="cdfa5-103">Definuje přenos vyrovnávací paměť pro informace o modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cdfa5-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cdfa5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdfa5-104">Syntax</span></span>

```
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="cdfa5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cdfa5-105">Members</span></span>

| <span data-ttu-id="cdfa5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cdfa5-106">Member</span></span>    | <span data-ttu-id="cdfa5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cdfa5-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="cdfa5-108">Adresa objektu modulu.</span><span class="sxs-lookup"><span data-stu-id="cdfa5-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="cdfa5-109">Ukazatel na soubor (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="cdfa5-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="cdfa5-110">Je základní adresa načíst obrázek.</span><span class="sxs-lookup"><span data-stu-id="cdfa5-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="cdfa5-111">Vyrovnávací paměť datové části pro informace o dalších modulu se používají modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="cdfa5-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cdfa5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdfa5-112">Remarks</span></span>

<span data-ttu-id="cdfa5-113">Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="cdfa5-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cdfa5-114">Pro použití je třeba definujte strukturu jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="cdfa5-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdfa5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdfa5-115">Requirements</span></span>
<span data-ttu-id="cdfa5-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdfa5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cdfa5-117">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="cdfa5-117">**Header:** None</span></span>  
<span data-ttu-id="cdfa5-118">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="cdfa5-118">**Library:** None</span></span>  
**<span data-ttu-id="cdfa5-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cdfa5-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="cdfa5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdfa5-120">See also</span></span>

- [<span data-ttu-id="cdfa5-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="cdfa5-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cdfa5-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="cdfa5-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
