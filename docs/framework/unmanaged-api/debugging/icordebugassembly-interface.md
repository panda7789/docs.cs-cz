---
title: ICorDebugAssembly Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly
helpviewer_keywords: ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d08bb1d2bb7adcbdeb49cd634755d243d34d7f84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="f49cb-102">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="f49cb-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="f49cb-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="f49cb-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f49cb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f49cb-104">Methods</span></span>  
  
|<span data-ttu-id="f49cb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f49cb-105">Method</span></span>|<span data-ttu-id="f49cb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f49cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f49cb-107">Enumeratemodules – metoda</span><span class="sxs-lookup"><span data-stu-id="f49cb-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="f49cb-108">Získá enumerátor pro moduly obsažený v sestavení.</span><span class="sxs-lookup"><span data-stu-id="f49cb-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="f49cb-109">Getappdomain – metoda</span><span class="sxs-lookup"><span data-stu-id="f49cb-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="f49cb-110">Získá ukazatele rozhraní k doméně aplikace, která obsahuje toto `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="f49cb-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="f49cb-111">Getcodebase – metoda</span><span class="sxs-lookup"><span data-stu-id="f49cb-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="f49cb-112">Není implementováno v aktuální verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f49cb-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="f49cb-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="f49cb-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="f49cb-114">Získá název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f49cb-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="f49cb-115">Getprocess – metoda</span><span class="sxs-lookup"><span data-stu-id="f49cb-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="f49cb-116">Získá instanci ICorDebugProcess, ve kterém je spuštěna sestavení.</span><span class="sxs-lookup"><span data-stu-id="f49cb-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f49cb-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f49cb-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f49cb-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f49cb-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f49cb-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f49cb-119">Requirements</span></span>  
 <span data-ttu-id="f49cb-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f49cb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f49cb-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f49cb-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f49cb-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f49cb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f49cb-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f49cb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49cb-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f49cb-124">See Also</span></span>  
 [<span data-ttu-id="f49cb-125">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="f49cb-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
