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
ms.openlocfilehash: ecd4ad31b8dad55e9538642a4dc652341bc84b97
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784676"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="cf0a6-102">ICorDebugAssembly – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf0a6-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="cf0a6-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="cf0a6-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf0a6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cf0a6-104">Methods</span></span>  
  
|<span data-ttu-id="cf0a6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cf0a6-105">Method</span></span>|<span data-ttu-id="cf0a6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cf0a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf0a6-107">EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="cf0a6-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="cf0a6-108">Získá enumerátor pro moduly obsažené v sestavení.</span><span class="sxs-lookup"><span data-stu-id="cf0a6-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="cf0a6-109">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="cf0a6-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="cf0a6-110">Získá ukazatel rozhraní na doménu aplikace, která obsahuje tuto instanci `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="cf0a6-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="cf0a6-111">GetCodeBase – metoda</span><span class="sxs-lookup"><span data-stu-id="cf0a6-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="cf0a6-112">Není implementováno v aktuální verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf0a6-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="cf0a6-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="cf0a6-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="cf0a6-114">Získá název sestavení.</span><span class="sxs-lookup"><span data-stu-id="cf0a6-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="cf0a6-115">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="cf0a6-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="cf0a6-116">Získá instanci ICorDebugProcess, ve které je sestavení spuštěno.</span><span class="sxs-lookup"><span data-stu-id="cf0a6-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf0a6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf0a6-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf0a6-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="cf0a6-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf0a6-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf0a6-119">Requirements</span></span>  
 <span data-ttu-id="cf0a6-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf0a6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf0a6-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf0a6-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf0a6-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cf0a6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf0a6-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf0a6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0a6-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf0a6-124">See also</span></span>

- [<span data-ttu-id="cf0a6-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cf0a6-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
