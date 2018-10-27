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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83928696fc7fdfaf2eb944f4cdb9eebecdece0b3
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452911"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="c906d-102">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="c906d-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="c906d-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="c906d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c906d-104">Představuje výjimku zpracování – klauzule (EH) pro danou část kódu (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="c906d-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c906d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c906d-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c906d-106">Členové</span><span class="sxs-lookup"><span data-stu-id="c906d-106">Members</span></span>  
  
|<span data-ttu-id="c906d-107">Člen</span><span class="sxs-lookup"><span data-stu-id="c906d-107">Member</span></span>|<span data-ttu-id="c906d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c906d-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="c906d-109">Bitové pole, která popisuje informace o výjimce v klauzuli EH.</span><span class="sxs-lookup"><span data-stu-id="c906d-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="c906d-110">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="c906d-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="c906d-111">Posun v bajtech, nástroje `try` bloku od samého začátku tělo metody.</span><span class="sxs-lookup"><span data-stu-id="c906d-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="c906d-112">Délka v bajtech, nástroje `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="c906d-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="c906d-113">Umístění obslužné rutiny pro tuto `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="c906d-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="c906d-114">Velikost v bajtech kód obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="c906d-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="c906d-115">Token metadat pro obslužnou rutinu na základě typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="c906d-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="c906d-116">Posun v bajtech od začátku tělo metody obslužné rutiny na základě filtru výjimky.</span><span class="sxs-lookup"><span data-stu-id="c906d-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c906d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c906d-117">Remarks</span></span>  
 <span data-ttu-id="c906d-118">Pole `CoreDebugEHClause` hodnoty vrácené [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c906d-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="c906d-119">Klauzule informace EH je definován specifikací CLI.</span><span class="sxs-lookup"><span data-stu-id="c906d-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="c906d-120">Další informace najdete v tématu [Standard ECMA-355: společné jazykové infrastruktury (CLI), 6 Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="c906d-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="c906d-121">`flags` Pole může obsahovat následující příznaky.</span><span class="sxs-lookup"><span data-stu-id="c906d-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="c906d-122">Všimněte si, že nejsou definovány v CorDebug.idl nebo CorDebug.h.</span><span class="sxs-lookup"><span data-stu-id="c906d-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="c906d-123">Příznak</span><span class="sxs-lookup"><span data-stu-id="c906d-123">Flag</span></span>|<span data-ttu-id="c906d-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c906d-124">Value</span></span>|<span data-ttu-id="c906d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c906d-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="c906d-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="c906d-126">0x00000000</span></span>|<span data-ttu-id="c906d-127">Klauzule typovou výjimku.</span><span class="sxs-lookup"><span data-stu-id="c906d-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="c906d-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="c906d-128">0x00000001</span></span>|<span data-ttu-id="c906d-129">Výjimka filtr a obslužné rutiny klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c906d-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="c906d-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="c906d-130">0x00000002</span></span>|<span data-ttu-id="c906d-131">A `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c906d-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="c906d-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="c906d-132">0x00000004</span></span>|<span data-ttu-id="c906d-133">Klauzule fault ( `finally` klauzuli, která je volána, pouze když je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="c906d-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c906d-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c906d-134">Requirements</span></span>  
 <span data-ttu-id="c906d-135">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c906d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c906d-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c906d-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c906d-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c906d-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c906d-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c906d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c906d-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="c906d-139">See Also</span></span>  
 [<span data-ttu-id="c906d-140">GetEHClauses – metoda</span><span class="sxs-lookup"><span data-stu-id="c906d-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [<span data-ttu-id="c906d-141">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="c906d-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
