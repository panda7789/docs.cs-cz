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
ms.openlocfilehash: b855a53c9e4303138d7605bdf108d37bb345b917
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789333"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="85e33-102">CorDebugGuidToTypeMapping – struktura</span><span class="sxs-lookup"><span data-stu-id="85e33-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="85e33-103">Mapuje identifikátor GUID prostředí Windows Runtime na odpovídající objekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="85e33-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85e33-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="85e33-105">Členové</span><span class="sxs-lookup"><span data-stu-id="85e33-105">Members</span></span>  
  
|<span data-ttu-id="85e33-106">Člen</span><span class="sxs-lookup"><span data-stu-id="85e33-106">Member</span></span>|<span data-ttu-id="85e33-107">Popis</span><span class="sxs-lookup"><span data-stu-id="85e33-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="85e33-108">Identifikátor GUID typu prostředí Windows Runtime v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="85e33-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="85e33-109">Ukazatel na objekt ICorDebugType, který poskytuje informace o typu uloženém v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="85e33-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85e33-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85e33-110">Requirements</span></span>  
 <span data-ttu-id="85e33-111">**Platformy:** prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="85e33-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="85e33-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85e33-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85e33-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85e33-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85e33-114">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e33-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85e33-115">See also</span></span>

- [<span data-ttu-id="85e33-116">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="85e33-116">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="85e33-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="85e33-117">Debugging</span></span>](index.md)
