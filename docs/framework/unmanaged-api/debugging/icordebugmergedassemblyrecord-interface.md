---
title: ICorDebugMergedAssemblyRecord – rozhraní
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 8dc07cb8c2f57ee6f9598c727cbd6de38bf4625f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139194"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="7d79c-102">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d79c-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="7d79c-103">Poskytuje informace o sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d79c-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d79c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7d79c-104">Methods</span></span>  
  
|<span data-ttu-id="7d79c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7d79c-105">Method</span></span>|<span data-ttu-id="7d79c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7d79c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d79c-107">GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="7d79c-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="7d79c-108">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d79c-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="7d79c-109">GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="7d79c-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="7d79c-110">Získá index předpony sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d79c-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="7d79c-111">GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="7d79c-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="7d79c-112">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d79c-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="7d79c-113">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7d79c-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="7d79c-114">Získá token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d79c-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="7d79c-115">GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="7d79c-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="7d79c-116">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d79c-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="7d79c-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="7d79c-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="7d79c-118">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d79c-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d79c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d79c-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d79c-120">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7d79c-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7d79c-121">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="7d79c-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d79c-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d79c-122">Requirements</span></span>  
 <span data-ttu-id="7d79c-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d79c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d79c-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d79c-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d79c-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d79c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d79c-126">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d79c-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d79c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d79c-127">See also</span></span>

- [<span data-ttu-id="7d79c-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7d79c-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7d79c-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="7d79c-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
