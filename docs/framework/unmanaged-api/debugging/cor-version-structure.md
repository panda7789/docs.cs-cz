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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00e58d83c19c3cb6a2e1eb38942500d7f5dc5cf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609292"
---
# <a name="corversion-structure"></a><span data-ttu-id="dfa17-102">COR_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="dfa17-102">COR_VERSION Structure</span></span>
<span data-ttu-id="dfa17-103">Ukládá číslo standardní sestávající ze čtyř částí verze modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="dfa17-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfa17-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="dfa17-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dfa17-105">Members</span></span>  
  
|<span data-ttu-id="dfa17-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dfa17-106">Member</span></span>|<span data-ttu-id="dfa17-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dfa17-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="dfa17-108">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="dfa17-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="dfa17-109">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="dfa17-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="dfa17-110">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfa17-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="dfa17-111">Číslo dílčí sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfa17-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfa17-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfa17-112">Remarks</span></span>  
 <span data-ttu-id="dfa17-113">Pokud číslo verze je 1.0.3705.288, je číslo hlavní verze 1, 0 je číslo podverze, 3705 je číslo sestavení a 288 je číslo dílčí sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfa17-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa17-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfa17-114">Requirements</span></span>  
 <span data-ttu-id="dfa17-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa17-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa17-116">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="dfa17-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="dfa17-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa17-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa17-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa17-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa17-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfa17-119">See also</span></span>

- [<span data-ttu-id="dfa17-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="dfa17-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="dfa17-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="dfa17-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
