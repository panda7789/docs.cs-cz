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
ms.openlocfilehash: 4528ccd77fed2ea2a9b2d08243ffa1535bfad1ae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274089"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="89039-102">CLR_DEBUGGING_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="89039-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="89039-103">Definuje verzi produktu modulu CLR (Common Language Runtime) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="89039-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89039-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89039-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="89039-105">Členové</span><span class="sxs-lookup"><span data-stu-id="89039-105">Members</span></span>  
  
|<span data-ttu-id="89039-106">Člen</span><span class="sxs-lookup"><span data-stu-id="89039-106">Member</span></span>|<span data-ttu-id="89039-107">Popis</span><span class="sxs-lookup"><span data-stu-id="89039-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="89039-108">Číslo verze struktury</span><span class="sxs-lookup"><span data-stu-id="89039-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="89039-109">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="89039-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="89039-110">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="89039-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="89039-111">Číslo sestavení</span><span class="sxs-lookup"><span data-stu-id="89039-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="89039-112">Číslo revize</span><span class="sxs-lookup"><span data-stu-id="89039-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89039-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89039-113">Remarks</span></span>  
 <span data-ttu-id="89039-114">Struktura je stejná jako struktura COR_VERSION, ale `CLR_DEBUGGING_VERSION` struktura poskytuje další pole verze struktury (`wStructVersion`). `CLR_DEBUGGING_VERSION`</span><span class="sxs-lookup"><span data-stu-id="89039-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="89039-115">V současné době musí být toto pole nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="89039-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89039-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89039-116">Requirements</span></span>  
 <span data-ttu-id="89039-117">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89039-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89039-118">**Hlaviček** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="89039-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="89039-119">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89039-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89039-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89039-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89039-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89039-121">See also</span></span>

- [<span data-ttu-id="89039-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="89039-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="89039-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="89039-123">Debugging</span></span>](index.md)
