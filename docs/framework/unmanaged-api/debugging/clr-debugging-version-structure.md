---
title: CLR_DEBUGGING_VERSION – struktura
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e71a1538e42061c6cb949b22bb63fe6b17a0dfc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741108"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="be300-102">CLR_DEBUGGING_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="be300-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="be300-103">Určuje verzi modulu common language runtime (CLR) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="be300-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be300-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be300-104">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="be300-105">Členové</span><span class="sxs-lookup"><span data-stu-id="be300-105">Members</span></span>  
  
|<span data-ttu-id="be300-106">Člen</span><span class="sxs-lookup"><span data-stu-id="be300-106">Member</span></span>|<span data-ttu-id="be300-107">Popis</span><span class="sxs-lookup"><span data-stu-id="be300-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="be300-108">Číslo verze struktura</span><span class="sxs-lookup"><span data-stu-id="be300-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="be300-109">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="be300-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="be300-110">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="be300-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="be300-111">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="be300-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="be300-112">Číslo revize.</span><span class="sxs-lookup"><span data-stu-id="be300-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be300-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be300-113">Remarks</span></span>  
 <span data-ttu-id="be300-114">`CLR_DEBUGGING_VERSION` Struktura je stejná jako cor_version – struktura, ale, `CLR_DEBUGGING_VERSION` struktura obsahuje pole Další Struktura verze (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="be300-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="be300-115">V současné době toto pole musí být nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="be300-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be300-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be300-116">Requirements</span></span>  
 <span data-ttu-id="be300-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be300-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be300-118">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="be300-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="be300-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be300-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be300-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be300-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be300-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be300-121">See also</span></span>

- [<span data-ttu-id="be300-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="be300-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="be300-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="be300-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
