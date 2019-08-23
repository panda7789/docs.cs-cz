---
title: Rozhraní ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca77360c36ff2cdce7ee47d5c3883dd824c6cef8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959324"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="4d817-102">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="4d817-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="4d817-103">Logicky rozšiřuje rozhraní ICorDebugAssembly, aby poskytovala podporu pro sestavení kontejneru a jejich obsažená sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d817-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d817-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d817-104">Methods</span></span>  
  
|<span data-ttu-id="4d817-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d817-105">Method</span></span>|<span data-ttu-id="4d817-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4d817-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d817-107">EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="4d817-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="4d817-108">Získá enumerátor pro sestavení obsažená v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d817-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="4d817-109">GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="4d817-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="4d817-110">Vrátí sestavení kontejneru tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="4d817-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d817-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d817-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d817-112">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d817-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="4d817-113">Pokus o volání metody `QueryInterface` načtení `E_NOINTERFACE` ukazatele rozhraní pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d817-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d817-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d817-114">Requirements</span></span>  
 <span data-ttu-id="4d817-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d817-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d817-116">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4d817-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d817-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d817-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d817-118">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d817-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d817-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d817-119">See also</span></span>

- [<span data-ttu-id="4d817-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4d817-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4d817-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="4d817-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
