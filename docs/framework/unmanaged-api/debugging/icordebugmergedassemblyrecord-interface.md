---
title: ICorDebugMergedAssemblyRecord – rozhraní
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793059"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="658fb-102">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="658fb-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="658fb-103">Poskytuje informace o sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="658fb-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="658fb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="658fb-104">Methods</span></span>  
  
|<span data-ttu-id="658fb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="658fb-105">Method</span></span>|<span data-ttu-id="658fb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="658fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="658fb-107">GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="658fb-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="658fb-108">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="658fb-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="658fb-109">GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="658fb-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="658fb-110">Získá index předpony sestavení.</span><span class="sxs-lookup"><span data-stu-id="658fb-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="658fb-111">GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="658fb-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="658fb-112">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="658fb-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="658fb-113">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="658fb-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="658fb-114">Získá token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="658fb-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="658fb-115">GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="658fb-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="658fb-116">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="658fb-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="658fb-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="658fb-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="658fb-118">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="658fb-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="658fb-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="658fb-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="658fb-120">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="658fb-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="658fb-121">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="658fb-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="658fb-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="658fb-122">Requirements</span></span>  
 <span data-ttu-id="658fb-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="658fb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="658fb-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="658fb-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="658fb-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="658fb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="658fb-126">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="658fb-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658fb-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="658fb-127">See also</span></span>

- [<span data-ttu-id="658fb-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="658fb-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="658fb-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="658fb-129">Debugging</span></span>](index.md)
