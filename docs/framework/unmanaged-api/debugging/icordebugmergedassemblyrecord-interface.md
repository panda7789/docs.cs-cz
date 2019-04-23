---
title: ICorDebugMergedAssemblyRecord – rozhraní
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180463"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="7bdcb-102">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7bdcb-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="7bdcb-103">Poskytuje informace o sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7bdcb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7bdcb-104">Methods</span></span>  
  
|<span data-ttu-id="7bdcb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7bdcb-105">Method</span></span>|<span data-ttu-id="7bdcb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7bdcb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7bdcb-107">GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="7bdcb-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="7bdcb-108">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="7bdcb-109">GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="7bdcb-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="7bdcb-110">Získá sestavení prefix index.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="7bdcb-111">GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="7bdcb-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="7bdcb-112">Získá veřejný klíč sestavení.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="7bdcb-113">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7bdcb-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="7bdcb-114">Získá token veřejného klíče sestavení.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="7bdcb-115">GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="7bdcb-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="7bdcb-116">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="7bdcb-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="7bdcb-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="7bdcb-118">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bdcb-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bdcb-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bdcb-120">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7bdcb-121">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7bdcb-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bdcb-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7bdcb-122">Requirements</span></span>  
 <span data-ttu-id="7bdcb-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bdcb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bdcb-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bdcb-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bdcb-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bdcb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bdcb-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bdcb-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bdcb-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bdcb-127">See also</span></span>

- [<span data-ttu-id="7bdcb-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7bdcb-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7bdcb-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="7bdcb-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
