---
title: ICorDebugMergedAssemblyRecord rozhraní
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e135166b79bb130e271549228418881b0c7587c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419673"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="4aece-102">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="4aece-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="4aece-103">Poskytuje informace o sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="4aece-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4aece-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4aece-104">Methods</span></span>  
  
|<span data-ttu-id="4aece-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4aece-105">Method</span></span>|<span data-ttu-id="4aece-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4aece-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4aece-107">GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="4aece-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="4aece-108">Získá řetězec název jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="4aece-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="4aece-109">GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="4aece-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="4aece-110">Získá index předpona je sestavení.</span><span class="sxs-lookup"><span data-stu-id="4aece-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="4aece-111">GetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="4aece-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="4aece-112">Získá sestavení veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="4aece-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="4aece-113">GetPublicKeyToken – metoda</span><span class="sxs-lookup"><span data-stu-id="4aece-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="4aece-114">Získá token veřejného klíče je sestavení.</span><span class="sxs-lookup"><span data-stu-id="4aece-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="4aece-115">GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="4aece-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="4aece-116">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="4aece-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="4aece-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="4aece-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="4aece-118">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="4aece-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aece-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4aece-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4aece-120">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="4aece-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4aece-121">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4aece-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aece-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4aece-122">Requirements</span></span>  
 <span data-ttu-id="4aece-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aece-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aece-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4aece-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4aece-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4aece-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4aece-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aece-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aece-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="4aece-127">See Also</span></span>  
 [<span data-ttu-id="4aece-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4aece-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4aece-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="4aece-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
