---
title: "Rozhraní ICorDebugAssembly3"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e581b4256da2ecc19a8b97520e0e70fef972b549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="430a0-102">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="430a0-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="430a0-103">Logicky rozšiřuje rozhraní ICorDebugAssembly kvůli zajištění podpory pro kontejner sestavení a jejich omezením sestavení.</span><span class="sxs-lookup"><span data-stu-id="430a0-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="430a0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="430a0-104">Methods</span></span>  
  
|<span data-ttu-id="430a0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="430a0-105">Method</span></span>|<span data-ttu-id="430a0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="430a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="430a0-107">EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="430a0-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="430a0-108">Získá enumerátor pro sestavení obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="430a0-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="430a0-109">GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="430a0-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="430a0-110">Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="430a0-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="430a0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="430a0-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="430a0-112">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="430a0-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="430a0-113">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="430a0-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="430a0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="430a0-114">Requirements</span></span>  
 <span data-ttu-id="430a0-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="430a0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="430a0-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="430a0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="430a0-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="430a0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="430a0-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="430a0-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430a0-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="430a0-119">See Also</span></span>  
 [<span data-ttu-id="430a0-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="430a0-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="430a0-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="430a0-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
