---
title: "ICorDebugMergedAssemblyRecord rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6086d1a82b5f086d857ac612a9d454a6ed77ba1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="f3d94-102">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3d94-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="f3d94-103">Poskytuje informace o sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3d94-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3d94-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f3d94-104">Methods</span></span>  
  
|<span data-ttu-id="f3d94-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f3d94-105">Method</span></span>|<span data-ttu-id="f3d94-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f3d94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3d94-107">GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="f3d94-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="f3d94-108">Získá řetězec název jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3d94-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="f3d94-109">GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="f3d94-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="f3d94-110">Získá index předpona je sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3d94-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="f3d94-111">GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="f3d94-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="f3d94-112">Získá sestavení veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="f3d94-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="f3d94-113">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="f3d94-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="f3d94-114">Získá token veřejného klíče je sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3d94-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="f3d94-115">GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="f3d94-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="f3d94-116">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3d94-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="f3d94-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="f3d94-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="f3d94-118">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3d94-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3d94-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3d94-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3d94-120">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="f3d94-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f3d94-121">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f3d94-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3d94-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3d94-122">Requirements</span></span>  
 <span data-ttu-id="f3d94-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3d94-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3d94-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3d94-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3d94-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3d94-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3d94-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3d94-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d94-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3d94-127">See Also</span></span>  
 [<span data-ttu-id="f3d94-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f3d94-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f3d94-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="f3d94-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
