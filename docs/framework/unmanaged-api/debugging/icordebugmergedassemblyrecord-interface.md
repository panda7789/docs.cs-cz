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
ms.openlocfilehash: 301d7d3d20b78e833101de1df8fd5c271a757144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="9ae17-102">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ae17-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="9ae17-103">Poskytuje informace o sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ae17-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ae17-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9ae17-104">Methods</span></span>  
  
|<span data-ttu-id="9ae17-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ae17-105">Method</span></span>|<span data-ttu-id="9ae17-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9ae17-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ae17-107">GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="9ae17-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="9ae17-108">Získá řetězec název jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ae17-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="9ae17-109">Getindex – metoda</span><span class="sxs-lookup"><span data-stu-id="9ae17-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="9ae17-110">Získá index předpona je sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ae17-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="9ae17-111">GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="9ae17-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="9ae17-112">Získá sestavení veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="9ae17-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="9ae17-113">Getpublickeytoken – metoda</span><span class="sxs-lookup"><span data-stu-id="9ae17-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="9ae17-114">Získá token veřejného klíče je sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ae17-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="9ae17-115">GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="9ae17-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="9ae17-116">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ae17-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="9ae17-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="9ae17-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="9ae17-118">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ae17-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ae17-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ae17-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ae17-120">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="9ae17-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9ae17-121">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ae17-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ae17-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ae17-122">Requirements</span></span>  
 <span data-ttu-id="9ae17-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ae17-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ae17-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ae17-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ae17-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ae17-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ae17-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ae17-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae17-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ae17-127">See Also</span></span>  
 [<span data-ttu-id="9ae17-128">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ae17-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9ae17-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="9ae17-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
