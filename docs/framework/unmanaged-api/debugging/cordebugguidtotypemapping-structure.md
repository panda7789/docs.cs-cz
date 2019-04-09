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
ms.openlocfilehash: 9dc7093edaf12e801a1e1adc52b0be823ff92b91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079913"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="752e8-102">CorDebugGuidToTypeMapping – struktura</span><span class="sxs-lookup"><span data-stu-id="752e8-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="752e8-103">Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID na jeho odpovídající objekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="752e8-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="752e8-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="752e8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="752e8-105">Members</span></span>  
  
|<span data-ttu-id="752e8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="752e8-106">Member</span></span>|<span data-ttu-id="752e8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="752e8-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="752e8-108">Identifikátor GUID v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="752e8-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="752e8-109">Ukazatel na objekt ICorDebugType, který poskytuje informace o typu v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="752e8-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="752e8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="752e8-110">Requirements</span></span>  
 <span data-ttu-id="752e8-111">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="752e8-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="752e8-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="752e8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="752e8-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="752e8-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="752e8-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="752e8-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="752e8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="752e8-115">See also</span></span>

- [<span data-ttu-id="752e8-116">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="752e8-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="752e8-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="752e8-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
