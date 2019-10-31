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
ms.openlocfilehash: f35e979a5107064d2987a385a989075ef71283ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098862"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="73be6-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="73be6-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="73be6-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="73be6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="73be6-104">Představuje klauzuli zpracování výjimek (EH) pro danou část kódu přestupného jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="73be6-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73be6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73be6-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="73be6-106">Členové</span><span class="sxs-lookup"><span data-stu-id="73be6-106">Members</span></span>  
  
|<span data-ttu-id="73be6-107">Člen</span><span class="sxs-lookup"><span data-stu-id="73be6-107">Member</span></span>|<span data-ttu-id="73be6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="73be6-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="73be6-109">Bitové pole, které popisuje informace o výjimce v klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="73be6-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="73be6-110">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="73be6-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="73be6-111">Posun v bajtech `try` bloku od začátku těla metody.</span><span class="sxs-lookup"><span data-stu-id="73be6-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="73be6-112">Délka bloku `try` v bajtech.</span><span class="sxs-lookup"><span data-stu-id="73be6-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="73be6-113">Umístění obslužné rutiny pro tento blok `try`.</span><span class="sxs-lookup"><span data-stu-id="73be6-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="73be6-114">Velikost kódu obslužné rutiny v bajtech</span><span class="sxs-lookup"><span data-stu-id="73be6-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="73be6-115">Token metadat pro obslužnou rutinu výjimky založené na typu.</span><span class="sxs-lookup"><span data-stu-id="73be6-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="73be6-116">Posun v bajtech od začátku těla metody pro obslužnou rutinu výjimky na základě filtru.</span><span class="sxs-lookup"><span data-stu-id="73be6-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73be6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73be6-117">Remarks</span></span>  
 <span data-ttu-id="73be6-118">Metoda [GetEHClauses –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) vrací pole hodnot `CoreDebugEHClause`.</span><span class="sxs-lookup"><span data-stu-id="73be6-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="73be6-119">Informace o klauzuli EH jsou definovány specifikací CLI.</span><span class="sxs-lookup"><span data-stu-id="73be6-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="73be6-120">Další informace naleznete v tématu [Standard ECMA-355: Common Language Infrastructure (CLI), 6. verze](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="73be6-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="73be6-121">Pole `flags` může obsahovat následující příznaky.</span><span class="sxs-lookup"><span data-stu-id="73be6-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="73be6-122">Všimněte si, že nejsou definovány v CorDebug. idl nebo CorDebug. h.</span><span class="sxs-lookup"><span data-stu-id="73be6-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="73be6-123">příznaků</span><span class="sxs-lookup"><span data-stu-id="73be6-123">Flag</span></span>|<span data-ttu-id="73be6-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="73be6-124">Value</span></span>|<span data-ttu-id="73be6-125">Popis</span><span class="sxs-lookup"><span data-stu-id="73be6-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="73be6-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="73be6-126">0x00000000</span></span>|<span data-ttu-id="73be6-127">Typová klauzule Exception</span><span class="sxs-lookup"><span data-stu-id="73be6-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="73be6-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="73be6-128">0x00000001</span></span>|<span data-ttu-id="73be6-129">Filtr výjimky a klauzule obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="73be6-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="73be6-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="73be6-130">0x00000002</span></span>|<span data-ttu-id="73be6-131">Klauzule `finally`.</span><span class="sxs-lookup"><span data-stu-id="73be6-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="73be6-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="73be6-132">0x00000004</span></span>|<span data-ttu-id="73be6-133">Klauzule Fault (`finally` klauzule, která je volána pouze v případě, že je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="73be6-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73be6-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73be6-134">Requirements</span></span>  
 <span data-ttu-id="73be6-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73be6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73be6-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73be6-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73be6-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73be6-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73be6-138">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73be6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73be6-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73be6-139">See also</span></span>

- [<span data-ttu-id="73be6-140">GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="73be6-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="73be6-141">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="73be6-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
