---
title: ICorDebugAssembly Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88134fb7854091bb60e8084a6d776bdec922c7e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406367"
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="c4749-102">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="c4749-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="c4749-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4749-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4749-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c4749-104">Methods</span></span>  
  
|<span data-ttu-id="c4749-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4749-105">Method</span></span>|<span data-ttu-id="c4749-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c4749-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4749-107">EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="c4749-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="c4749-108">Získá enumerátor pro moduly obsažený v sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4749-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="c4749-109">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="c4749-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="c4749-110">Získá ukazatele rozhraní k doméně aplikace, která obsahuje toto `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="c4749-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="c4749-111">GetCodeBase – metoda</span><span class="sxs-lookup"><span data-stu-id="c4749-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="c4749-112">Není implementováno v aktuální verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4749-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="c4749-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="c4749-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="c4749-114">Získá název sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4749-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="c4749-115">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="c4749-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="c4749-116">Získá instanci ICorDebugProcess, ve kterém je spuštěna sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4749-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4749-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4749-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4749-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c4749-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4749-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4749-119">Requirements</span></span>  
 <span data-ttu-id="c4749-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4749-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4749-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4749-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4749-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4749-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4749-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4749-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4749-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4749-124">See Also</span></span>  
 [<span data-ttu-id="c4749-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4749-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
