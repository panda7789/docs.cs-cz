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
ms.openlocfilehash: 49290a37ca7ea101e3c8b458a5daa4995cb3beee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610042"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="c6900-102">CorDebugGuidToTypeMapping – struktura</span><span class="sxs-lookup"><span data-stu-id="c6900-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="c6900-103">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID na jeho odpovídající objekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="c6900-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6900-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6900-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="c6900-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c6900-105">Members</span></span>  
  
|<span data-ttu-id="c6900-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c6900-106">Member</span></span>|<span data-ttu-id="c6900-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c6900-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="c6900-108">Identifikátor GUID v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="c6900-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="c6900-109">Ukazatel na objekt ICorDebugType, který poskytuje informace o typu v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c6900-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6900-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6900-110">Requirements</span></span>  
 <span data-ttu-id="c6900-111">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6900-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="c6900-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6900-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6900-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6900-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6900-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6900-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6900-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6900-115">See also</span></span>
- [<span data-ttu-id="c6900-116">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="c6900-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="c6900-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="c6900-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
