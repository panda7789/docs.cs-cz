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
ms.openlocfilehash: b9ed476746e627be987e6307bd367f0d16374de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="0cd26-102">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="0cd26-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="0cd26-103">Logicky rozšiřuje rozhraní ICorDebugAssembly kvůli zajištění podpory pro kontejner sestavení a jejich omezením sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cd26-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0cd26-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0cd26-104">Methods</span></span>  
  
|<span data-ttu-id="0cd26-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0cd26-105">Method</span></span>|<span data-ttu-id="0cd26-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0cd26-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0cd26-107">Metoda EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="0cd26-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="0cd26-108">Získá enumerátor pro sestavení obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cd26-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="0cd26-109">Metoda GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="0cd26-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="0cd26-110">Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="0cd26-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cd26-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cd26-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cd26-112">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="0cd26-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="0cd26-113">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0cd26-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cd26-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0cd26-114">Requirements</span></span>  
 <span data-ttu-id="0cd26-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cd26-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cd26-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cd26-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cd26-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cd26-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cd26-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cd26-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd26-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cd26-119">See Also</span></span>  
 [<span data-ttu-id="0cd26-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cd26-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0cd26-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="0cd26-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
