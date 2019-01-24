---
title: Rozhraní ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66d3024c0bb2c0014cbec2b24deb7b0d5845fe88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627522"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="6c5bd-102">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="6c5bd-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="6c5bd-103">Logicky rozšiřuje icordebugassembly – rozhraní a poskytuje podporu pro sestavení kontejneru a jejich obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c5bd-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c5bd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6c5bd-104">Methods</span></span>  
  
|<span data-ttu-id="6c5bd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6c5bd-105">Method</span></span>|<span data-ttu-id="6c5bd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6c5bd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c5bd-107">EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="6c5bd-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="6c5bd-108">Získá enumerátor pro sestaveních obsažených v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c5bd-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="6c5bd-109">GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="6c5bd-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="6c5bd-110">Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="6c5bd-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c5bd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c5bd-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c5bd-112">Rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6c5bd-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="6c5bd-113">Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6c5bd-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c5bd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c5bd-114">Requirements</span></span>  
 <span data-ttu-id="6c5bd-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c5bd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c5bd-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c5bd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c5bd-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c5bd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c5bd-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c5bd-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5bd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c5bd-119">See also</span></span>
- [<span data-ttu-id="6c5bd-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6c5bd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6c5bd-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="6c5bd-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
