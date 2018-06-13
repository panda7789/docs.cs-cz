---
title: Rozhraní ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5042f59b3716d077cc441585004e075b765c0cfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407852"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="71624-102">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="71624-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="71624-103">Logicky rozšiřuje rozhraní ICorDebugAssembly kvůli zajištění podpory pro kontejner sestavení a jejich omezením sestavení.</span><span class="sxs-lookup"><span data-stu-id="71624-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71624-104">Metody</span><span class="sxs-lookup"><span data-stu-id="71624-104">Methods</span></span>  
  
|<span data-ttu-id="71624-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="71624-105">Method</span></span>|<span data-ttu-id="71624-106">Popis</span><span class="sxs-lookup"><span data-stu-id="71624-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71624-107">EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="71624-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="71624-108">Získá enumerátor pro sestavení obsažené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="71624-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="71624-109">GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="71624-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="71624-110">Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="71624-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71624-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71624-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71624-112">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="71624-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="71624-113">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="71624-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71624-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71624-114">Requirements</span></span>  
 <span data-ttu-id="71624-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71624-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71624-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71624-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71624-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71624-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71624-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71624-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71624-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="71624-119">See Also</span></span>  
 [<span data-ttu-id="71624-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="71624-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="71624-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="71624-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
