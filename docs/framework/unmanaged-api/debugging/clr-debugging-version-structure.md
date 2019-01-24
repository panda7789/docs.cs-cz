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
ms.openlocfilehash: a4049b0ed25d4c0fda00fe9b0dad5887fa4f6996
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506937"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="58178-102">CLR_DEBUGGING_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="58178-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="58178-103">Určuje verzi modulu common language runtime (CLR) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="58178-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58178-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58178-104">Syntax</span></span>  
  
```  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="58178-105">Členové</span><span class="sxs-lookup"><span data-stu-id="58178-105">Members</span></span>  
  
|<span data-ttu-id="58178-106">Člen</span><span class="sxs-lookup"><span data-stu-id="58178-106">Member</span></span>|<span data-ttu-id="58178-107">Popis</span><span class="sxs-lookup"><span data-stu-id="58178-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="58178-108">Číslo verze struktura</span><span class="sxs-lookup"><span data-stu-id="58178-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="58178-109">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="58178-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="58178-110">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="58178-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="58178-111">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="58178-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="58178-112">Číslo revize.</span><span class="sxs-lookup"><span data-stu-id="58178-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58178-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58178-113">Remarks</span></span>  
 <span data-ttu-id="58178-114">`CLR_DEBUGGING_VERSION` Struktura je stejná jako cor_version – struktura, ale, `CLR_DEBUGGING_VERSION` struktura obsahuje pole Další Struktura verze (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="58178-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="58178-115">V současné době toto pole musí být nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="58178-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58178-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58178-116">Requirements</span></span>  
 <span data-ttu-id="58178-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58178-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58178-118">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="58178-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="58178-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58178-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58178-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58178-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58178-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58178-121">See also</span></span>
- [<span data-ttu-id="58178-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="58178-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="58178-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="58178-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
