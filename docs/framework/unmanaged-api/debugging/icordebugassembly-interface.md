---
title: ICorDebugAssembly – rozhraní
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
ms.openlocfilehash: dea3231e3bbb361b56254756c6d99b115f73e792
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133971"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="a5d72-102">ICorDebugAssembly – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5d72-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="a5d72-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5d72-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5d72-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a5d72-104">Methods</span></span>  
  
|<span data-ttu-id="a5d72-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a5d72-105">Method</span></span>|<span data-ttu-id="a5d72-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a5d72-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5d72-107">EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="a5d72-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="a5d72-108">Získá enumerátor pro moduly obsažené v sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5d72-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="a5d72-109">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="a5d72-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="a5d72-110">Získá ukazatel rozhraní na doménu aplikace, která obsahuje tuto instanci `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="a5d72-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="a5d72-111">GetCodeBase – metoda</span><span class="sxs-lookup"><span data-stu-id="a5d72-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="a5d72-112">Není implementováno v aktuální verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5d72-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="a5d72-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="a5d72-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="a5d72-114">Získá název sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5d72-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="a5d72-115">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="a5d72-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="a5d72-116">Získá instanci ICorDebugProcess, ve které je sestavení spuštěno.</span><span class="sxs-lookup"><span data-stu-id="a5d72-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5d72-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5d72-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5d72-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a5d72-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5d72-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5d72-119">Requirements</span></span>  
 <span data-ttu-id="a5d72-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5d72-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5d72-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5d72-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5d72-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a5d72-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5d72-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5d72-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d72-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5d72-124">See also</span></span>

- [<span data-ttu-id="a5d72-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a5d72-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
