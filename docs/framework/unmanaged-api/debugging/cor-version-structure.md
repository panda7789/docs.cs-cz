---
title: COR_VERSION – struktura
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
ms.openlocfilehash: cc9a67e16635209c3bf303e97dc3e5938943a653
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099095"
---
# <a name="cor_version-structure"></a><span data-ttu-id="c30db-102">COR_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="c30db-102">COR_VERSION Structure</span></span>
<span data-ttu-id="c30db-103">Ukládá standardní číslo verze se čtyřmi částmi modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c30db-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c30db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c30db-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="c30db-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c30db-105">Members</span></span>  
  
|<span data-ttu-id="c30db-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c30db-106">Member</span></span>|<span data-ttu-id="c30db-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c30db-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="c30db-108">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="c30db-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="c30db-109">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="c30db-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="c30db-110">Číslo sestavení</span><span class="sxs-lookup"><span data-stu-id="c30db-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="c30db-111">Číslo dílčího sestavení</span><span class="sxs-lookup"><span data-stu-id="c30db-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c30db-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c30db-112">Remarks</span></span>  
 <span data-ttu-id="c30db-113">Pokud je číslo verze 1.0.3705.288, 1 je hlavní číslo verze, 0 je číslo dílčí verze, 3705 je číslo sestavení a 288 je číslo dílčího sestavení.</span><span class="sxs-lookup"><span data-stu-id="c30db-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c30db-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c30db-114">Requirements</span></span>  
 <span data-ttu-id="c30db-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c30db-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c30db-116">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="c30db-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c30db-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c30db-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c30db-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c30db-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30db-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c30db-119">See also</span></span>

- [<span data-ttu-id="c30db-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="c30db-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c30db-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="c30db-121">Debugging</span></span>](index.md)
