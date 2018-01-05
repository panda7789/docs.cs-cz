---
title: Struktura CorDebugEHClause
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugEHClause
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97428837d78c246915381b51fb5005a68518b7bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="7a626-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="7a626-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="7a626-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="7a626-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7a626-104">Představuje výjimku zpracování (EH) klauzuli pro určitou část kód intermediate language (IL).</span><span class="sxs-lookup"><span data-stu-id="7a626-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a626-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a626-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7a626-106">Členové</span><span class="sxs-lookup"><span data-stu-id="7a626-106">Members</span></span>  
  
|<span data-ttu-id="7a626-107">Člen</span><span class="sxs-lookup"><span data-stu-id="7a626-107">Member</span></span>|<span data-ttu-id="7a626-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7a626-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="7a626-109">Bitová pole, které popisuje informace o výjimce v klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="7a626-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="7a626-110">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="7a626-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="7a626-111">Posun v bajtech z `try` bloku od začátku těla metody.</span><span class="sxs-lookup"><span data-stu-id="7a626-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="7a626-112">Délka v bajtech z `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="7a626-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="7a626-113">Umístění obslužná rutina pro tento `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="7a626-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="7a626-114">Velikost v bajtech kód obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="7a626-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="7a626-115">Token metadata pro obslužnou rutinu výjimky založený na typu.</span><span class="sxs-lookup"><span data-stu-id="7a626-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="7a626-116">Posun v bajtech, od začátku těla metody pro obslužnou rutinu na základě filtru výjimek.</span><span class="sxs-lookup"><span data-stu-id="7a626-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a626-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a626-117">Remarks</span></span>  
 <span data-ttu-id="7a626-118">Pole `CoreDebugEHClause` hodnoty vrátí [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="7a626-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="7a626-119">Informace klauzule EH je definován specifikací rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7a626-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="7a626-120">Další informace najdete v tématu [standardní ECMA-355: společné jazykové infrastruktury (CLI), 6. Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="7a626-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="7a626-121">`flags` Pole může obsahovat následující příznaky.</span><span class="sxs-lookup"><span data-stu-id="7a626-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="7a626-122">Všimněte si, že nejsou definovány v CorDebug.idl nebo CorDebug.h.</span><span class="sxs-lookup"><span data-stu-id="7a626-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="7a626-123">Příznak</span><span class="sxs-lookup"><span data-stu-id="7a626-123">Flag</span></span>|<span data-ttu-id="7a626-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7a626-124">Value</span></span>|<span data-ttu-id="7a626-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7a626-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="7a626-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="7a626-126">0x00000000</span></span>|<span data-ttu-id="7a626-127">Klauzuli typu výjimka.</span><span class="sxs-lookup"><span data-stu-id="7a626-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="7a626-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="7a626-128">0x00000001</span></span>|<span data-ttu-id="7a626-129">Výjimka filtr a obslužné rutiny klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7a626-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="7a626-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="7a626-130">0x00000002</span></span>|<span data-ttu-id="7a626-131">A `finally` klauzule.</span><span class="sxs-lookup"><span data-stu-id="7a626-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="7a626-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="7a626-132">0x00000004</span></span>|<span data-ttu-id="7a626-133">Klauzuli selhání ( `finally` klauzuli, která je volána, pouze když je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="7a626-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a626-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a626-134">Requirements</span></span>  
 <span data-ttu-id="7a626-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a626-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a626-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a626-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a626-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a626-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a626-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a626-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a626-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a626-139">See Also</span></span>  
 [<span data-ttu-id="7a626-140">GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="7a626-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [<span data-ttu-id="7a626-141">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="7a626-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
