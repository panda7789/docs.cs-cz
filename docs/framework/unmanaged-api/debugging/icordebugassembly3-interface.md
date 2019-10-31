---
title: Rozhraní ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 930101f6cd4ebb9215d6420f774b8e066c54a4f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095370"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="fe23b-102">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="fe23b-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="fe23b-103">Logicky rozšiřuje rozhraní ICorDebugAssembly, aby poskytovala podporu pro sestavení kontejneru a jejich obsažená sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe23b-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe23b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fe23b-104">Methods</span></span>  
  
|<span data-ttu-id="fe23b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fe23b-105">Method</span></span>|<span data-ttu-id="fe23b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fe23b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe23b-107">EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="fe23b-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="fe23b-108">Získá enumerátor pro sestavení obsažená v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe23b-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="fe23b-109">GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="fe23b-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="fe23b-110">Vrátí sestavení kontejneru tohoto objektu `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="fe23b-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe23b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe23b-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe23b-112">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fe23b-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="fe23b-113">Pokus o volání `QueryInterface` pro načtení ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fe23b-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe23b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe23b-114">Requirements</span></span>  
 <span data-ttu-id="fe23b-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe23b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe23b-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fe23b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe23b-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fe23b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe23b-118">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe23b-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe23b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe23b-119">See also</span></span>

- [<span data-ttu-id="fe23b-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fe23b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fe23b-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="fe23b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
