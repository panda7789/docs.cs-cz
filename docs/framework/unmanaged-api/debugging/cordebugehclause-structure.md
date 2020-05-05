---
title: Struktura CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: a889d6ba00c4a0eb96a9923a7dbe52f3b93aaba5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795958"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="1a864-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="1a864-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="1a864-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="1a864-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1a864-104">Představuje klauzuli zpracování výjimek (EH) pro danou část kódu přestupného jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="1a864-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a864-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a864-105">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="1a864-106">Členové</span><span class="sxs-lookup"><span data-stu-id="1a864-106">Members</span></span>  
  
|<span data-ttu-id="1a864-107">Člen</span><span class="sxs-lookup"><span data-stu-id="1a864-107">Member</span></span>|<span data-ttu-id="1a864-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1a864-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="1a864-109">Bitové pole, které popisuje informace o výjimce v klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="1a864-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="1a864-110">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="1a864-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="1a864-111">Posun `try` bloku v bajtech od začátku těla metody.</span><span class="sxs-lookup"><span data-stu-id="1a864-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="1a864-112">Délka `try` bloku v bajtech.</span><span class="sxs-lookup"><span data-stu-id="1a864-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="1a864-113">Umístění obslužné rutiny pro tento `try` blok.</span><span class="sxs-lookup"><span data-stu-id="1a864-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="1a864-114">Velikost kódu obslužné rutiny v bajtech</span><span class="sxs-lookup"><span data-stu-id="1a864-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="1a864-115">Token metadat pro obslužnou rutinu výjimky založené na typu.</span><span class="sxs-lookup"><span data-stu-id="1a864-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="1a864-116">Posun v bajtech od začátku těla metody pro obslužnou rutinu výjimky na základě filtru.</span><span class="sxs-lookup"><span data-stu-id="1a864-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a864-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a864-117">Remarks</span></span>  
 <span data-ttu-id="1a864-118">Pole `CoreDebugEHClause` hodnot je vráceno metodou [GetEHClauses –](icordebugilcode-getehclauses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1a864-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="1a864-119">Informace o klauzuli EH jsou definovány specifikací CLI.</span><span class="sxs-lookup"><span data-stu-id="1a864-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="1a864-120">Další informace naleznete v tématu [Standard ECMA-355: Common Language Infrastructure (CLI), 6. verze](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="1a864-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="1a864-121">`flags` Pole může obsahovat následující příznaky.</span><span class="sxs-lookup"><span data-stu-id="1a864-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="1a864-122">Všimněte si, že nejsou definovány v CorDebug. idl nebo CorDebug. h.</span><span class="sxs-lookup"><span data-stu-id="1a864-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="1a864-123">Příznak</span><span class="sxs-lookup"><span data-stu-id="1a864-123">Flag</span></span>|<span data-ttu-id="1a864-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1a864-124">Value</span></span>|<span data-ttu-id="1a864-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1a864-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="1a864-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="1a864-126">0x00000000</span></span>|<span data-ttu-id="1a864-127">Typová klauzule Exception</span><span class="sxs-lookup"><span data-stu-id="1a864-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="1a864-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="1a864-128">0x00000001</span></span>|<span data-ttu-id="1a864-129">Filtr výjimky a klauzule obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1a864-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="1a864-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="1a864-130">0x00000002</span></span>|<span data-ttu-id="1a864-131">`finally` Klauzule.</span><span class="sxs-lookup"><span data-stu-id="1a864-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="1a864-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="1a864-132">0x00000004</span></span>|<span data-ttu-id="1a864-133">Klauzule Fault ( `finally` klauzule, která je volána pouze v případě, že je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="1a864-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a864-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a864-134">Requirements</span></span>  
 <span data-ttu-id="1a864-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a864-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a864-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a864-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a864-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1a864-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a864-138">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a864-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a864-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a864-139">See also</span></span>

- [<span data-ttu-id="1a864-140">GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="1a864-140">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="1a864-141">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="1a864-141">Debugging Structures</span></span>](debugging-structures.md)
