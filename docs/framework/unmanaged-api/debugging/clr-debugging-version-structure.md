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
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132422"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="ca941-102">CLR_DEBUGGING_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="ca941-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="ca941-103">Definuje verzi produktu modulu CLR (Common Language Runtime) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="ca941-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca941-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca941-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ca941-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ca941-105">Members</span></span>  
  
|<span data-ttu-id="ca941-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ca941-106">Member</span></span>|<span data-ttu-id="ca941-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ca941-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="ca941-108">Číslo verze struktury</span><span class="sxs-lookup"><span data-stu-id="ca941-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="ca941-109">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="ca941-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="ca941-110">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="ca941-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="ca941-111">Číslo sestavení</span><span class="sxs-lookup"><span data-stu-id="ca941-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="ca941-112">Číslo revize</span><span class="sxs-lookup"><span data-stu-id="ca941-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca941-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca941-113">Remarks</span></span>  
 <span data-ttu-id="ca941-114">Struktura `CLR_DEBUGGING_VERSION` je stejná jako struktura COR_VERSION, ale struktura `CLR_DEBUGGING_VERSION` poskytuje další pole verze struktury (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="ca941-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="ca941-115">V současné době musí být toto pole nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="ca941-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca941-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca941-116">Requirements</span></span>  
 <span data-ttu-id="ca941-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca941-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca941-118">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="ca941-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ca941-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ca941-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca941-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca941-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca941-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca941-121">See also</span></span>

- [<span data-ttu-id="ca941-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="ca941-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ca941-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="ca941-123">Debugging</span></span>](index.md)
