---
title: ICorDebugMergedAssemblyRecord – rozhraní
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 721f6c1cf468b3b518d2ea213588ae2410249690
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208717"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="4fb5d-102">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fb5d-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="4fb5d-103">Poskytuje informace o sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fb5d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4fb5d-104">Methods</span></span>  
  
|<span data-ttu-id="4fb5d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4fb5d-105">Method</span></span>|<span data-ttu-id="4fb5d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4fb5d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fb5d-107">GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="4fb5d-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="4fb5d-108">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="4fb5d-109">GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="4fb5d-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="4fb5d-110">Získá index předpony sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="4fb5d-111">GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="4fb5d-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="4fb5d-112">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="4fb5d-113">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="4fb5d-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="4fb5d-114">Získá token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="4fb5d-115">GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="4fb5d-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="4fb5d-116">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="4fb5d-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="4fb5d-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="4fb5d-118">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fb5d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fb5d-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fb5d-120">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4fb5d-121">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fb5d-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fb5d-122">Requirements</span></span>  
 <span data-ttu-id="4fb5d-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fb5d-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fb5d-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4fb5d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fb5d-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4fb5d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fb5d-126">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb5d-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb5d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fb5d-127">See also</span></span>

- [<span data-ttu-id="4fb5d-128">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fb5d-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4fb5d-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="4fb5d-129">Debugging</span></span>](index.md)
