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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd60defc1c003fa4b235ddcb0a78b9a819b1b0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198020"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="937ec-102">ICorDebugAssembly – rozhraní</span><span class="sxs-lookup"><span data-stu-id="937ec-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="937ec-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="937ec-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="937ec-104">Metody</span><span class="sxs-lookup"><span data-stu-id="937ec-104">Methods</span></span>  
  
|<span data-ttu-id="937ec-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="937ec-105">Method</span></span>|<span data-ttu-id="937ec-106">Popis</span><span class="sxs-lookup"><span data-stu-id="937ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="937ec-107">EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="937ec-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="937ec-108">Získá enumerátor pro moduly, které jsou obsaženy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="937ec-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="937ec-109">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="937ec-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="937ec-110">Získá ukazatel rozhraní k doméně aplikace, která obsahuje tato `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="937ec-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="937ec-111">GetCodeBase – metoda</span><span class="sxs-lookup"><span data-stu-id="937ec-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="937ec-112">Není implementováno v aktuální verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="937ec-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="937ec-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="937ec-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="937ec-114">Získá název sestavení.</span><span class="sxs-lookup"><span data-stu-id="937ec-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="937ec-115">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="937ec-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="937ec-116">Získá instanci ICorDebugProcess, ve kterém je spuštěna sestavení.</span><span class="sxs-lookup"><span data-stu-id="937ec-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="937ec-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="937ec-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="937ec-118">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="937ec-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="937ec-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="937ec-119">Requirements</span></span>  
 <span data-ttu-id="937ec-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="937ec-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="937ec-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="937ec-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="937ec-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="937ec-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="937ec-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="937ec-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="937ec-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="937ec-124">See also</span></span>

- [<span data-ttu-id="937ec-125">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="937ec-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
