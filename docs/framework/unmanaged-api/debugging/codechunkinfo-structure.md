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
ms.openlocfilehash: 36afee8af3de046683c55215a677a529b0837c77
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274257"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="19f29-102">CodeChunkInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="19f29-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="19f29-103">Představuje jeden blok kódu v paměti.</span><span class="sxs-lookup"><span data-stu-id="19f29-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19f29-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="19f29-105">Členové</span><span class="sxs-lookup"><span data-stu-id="19f29-105">Members</span></span>  
  
|<span data-ttu-id="19f29-106">Člen</span><span class="sxs-lookup"><span data-stu-id="19f29-106">Member</span></span>|<span data-ttu-id="19f29-107">Popis</span><span class="sxs-lookup"><span data-stu-id="19f29-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="19f29-108">`CORDB_ADDRESS` Hodnota, která určuje počáteční adresu bloku.</span><span class="sxs-lookup"><span data-stu-id="19f29-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="19f29-109">Velikost bloku (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="19f29-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19f29-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19f29-110">Remarks</span></span>  
 <span data-ttu-id="19f29-111">Jediný blok kódu je oblast nativního kódu, který je součástí objektu kódu, jako je například funkce.</span><span class="sxs-lookup"><span data-stu-id="19f29-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19f29-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19f29-112">Requirements</span></span>  
 <span data-ttu-id="19f29-113">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19f29-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19f29-114">**Hlaviček** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="19f29-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="19f29-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19f29-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19f29-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19f29-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f29-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19f29-117">See also</span></span>

- [<span data-ttu-id="19f29-118">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="19f29-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="19f29-119">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="19f29-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="19f29-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="19f29-120">Debugging</span></span>](index.md)
