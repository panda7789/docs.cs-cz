---
title: CodeChunkInfo – struktura
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58c9d4c66af0bb9f4e66d17b18ac78ef8271bc31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072659"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="d975a-102">CodeChunkInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="d975a-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="d975a-103">Představuje jediný neodkazovaný blok kódu v paměti.</span><span class="sxs-lookup"><span data-stu-id="d975a-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d975a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d975a-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="d975a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d975a-105">Members</span></span>  
  
|<span data-ttu-id="d975a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d975a-106">Member</span></span>|<span data-ttu-id="d975a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d975a-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="d975a-108">A `CORDB_ADDRESS` hodnotu, která určuje počáteční adresu bloků.</span><span class="sxs-lookup"><span data-stu-id="d975a-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="d975a-109">Velikost v bajtech, bloků.</span><span class="sxs-lookup"><span data-stu-id="d975a-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d975a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d975a-110">Remarks</span></span>  
 <span data-ttu-id="d975a-111">Jediný neodkazovaný blok kódu je oblast nativní kód, který je součástí objektu kódu, jako je například funkce.</span><span class="sxs-lookup"><span data-stu-id="d975a-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d975a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d975a-112">Requirements</span></span>  
 <span data-ttu-id="d975a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d975a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d975a-114">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="d975a-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d975a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d975a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d975a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d975a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d975a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d975a-117">See also</span></span>

- [<span data-ttu-id="d975a-118">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="d975a-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="d975a-119">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="d975a-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="d975a-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="d975a-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
