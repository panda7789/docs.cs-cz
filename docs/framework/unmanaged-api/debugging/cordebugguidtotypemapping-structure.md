---
title: CorDebugGuidToTypeMapping – struktura
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e1b19d6340f559e6f8b7e0f7bc042a10df16c3
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025999"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="ec027-102">CorDebugGuidToTypeMapping – struktura</span><span class="sxs-lookup"><span data-stu-id="ec027-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="ec027-103">Mapuje na jeho odpovídající objekt ICorDebugType identifikátor GUID Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="ec027-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec027-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec027-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="ec027-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ec027-105">Members</span></span>  
  
|<span data-ttu-id="ec027-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ec027-106">Member</span></span>|<span data-ttu-id="ec027-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ec027-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="ec027-108">Identifikátor GUID v mezipaměti typ Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="ec027-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="ec027-109">Ukazatel na objekt ICorDebugType, který poskytuje informace o typu v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ec027-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec027-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec027-110">Requirements</span></span>  
 <span data-ttu-id="ec027-111">**Platformy:** Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="ec027-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="ec027-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec027-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec027-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec027-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec027-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec027-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec027-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec027-115">See also</span></span>

- [<span data-ttu-id="ec027-116">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="ec027-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="ec027-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="ec027-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
