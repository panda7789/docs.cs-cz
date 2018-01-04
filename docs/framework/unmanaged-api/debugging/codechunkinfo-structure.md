---
title: "Codechunkinfo – – Struktura1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CodeChunkInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: CodeChunkInfo
helpviewer_keywords: CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7b3b858d645f01f58ba0b67465b22dd05282656
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="20cf8-102">Codechunkinfo – – Struktura1</span><span class="sxs-lookup"><span data-stu-id="20cf8-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="20cf8-103">Představuje jeden blok kódu v paměti.</span><span class="sxs-lookup"><span data-stu-id="20cf8-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20cf8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20cf8-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="20cf8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="20cf8-105">Members</span></span>  
  
|<span data-ttu-id="20cf8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="20cf8-106">Member</span></span>|<span data-ttu-id="20cf8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="20cf8-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="20cf8-108">A `CORDB_ADDRESS` hodnotu, která určuje počáteční adresa bloku.</span><span class="sxs-lookup"><span data-stu-id="20cf8-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="20cf8-109">Velikost v bajtech, bloku.</span><span class="sxs-lookup"><span data-stu-id="20cf8-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20cf8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20cf8-110">Remarks</span></span>  
 <span data-ttu-id="20cf8-111">U jednoho bloku kódu je oblasti nativního kódu, který je součástí objektu kódu, jako je například funkce.</span><span class="sxs-lookup"><span data-stu-id="20cf8-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20cf8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20cf8-112">Requirements</span></span>  
 <span data-ttu-id="20cf8-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20cf8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20cf8-114">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="20cf8-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="20cf8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20cf8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20cf8-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20cf8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20cf8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="20cf8-117">See Also</span></span>  
 [<span data-ttu-id="20cf8-118">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="20cf8-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="20cf8-119">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="20cf8-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="20cf8-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="20cf8-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
