---
title: Rozhraní ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 67707092c80b0e07aa284336c426aba09ff991af
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894817"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="f3a00-102">Rozhraní ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="f3a00-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="f3a00-103">Logicky rozšiřuje rozhraní ICorDebugAssembly, aby poskytovala podporu pro sestavení kontejneru a jejich obsažená sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3a00-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3a00-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f3a00-104">Methods</span></span>  
  
|<span data-ttu-id="f3a00-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f3a00-105">Method</span></span>|<span data-ttu-id="f3a00-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f3a00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3a00-107">EnumerateContainedAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="f3a00-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="f3a00-108">Získá enumerátor pro sestavení obsažená v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3a00-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="f3a00-109">GetContainerAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="f3a00-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="f3a00-110">Vrátí sestavení kontejneru tohoto `ICorDebugAssembly3` objektu.</span><span class="sxs-lookup"><span data-stu-id="f3a00-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3a00-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3a00-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3a00-112">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f3a00-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="f3a00-113">Pokus o volání metody `QueryInterface` načtení ukazatele rozhraní `E_NOINTERFACE` pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f3a00-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a00-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3a00-114">Requirements</span></span>  
 <span data-ttu-id="f3a00-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3a00-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a00-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3a00-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3a00-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3a00-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3a00-118">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a00-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a00-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3a00-119">See also</span></span>

- [<span data-ttu-id="f3a00-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3a00-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f3a00-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="f3a00-121">Debugging</span></span>](index.md)
