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
ms.openlocfilehash: d9e2236b944137de82bb056820f81014febfcc5f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894899"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="246f4-102">ICorDebugAssembly – rozhraní</span><span class="sxs-lookup"><span data-stu-id="246f4-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="246f4-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="246f4-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="246f4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="246f4-104">Methods</span></span>  
  
|<span data-ttu-id="246f4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="246f4-105">Method</span></span>|<span data-ttu-id="246f4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="246f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="246f4-107">EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="246f4-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="246f4-108">Získá enumerátor pro moduly obsažené v sestavení.</span><span class="sxs-lookup"><span data-stu-id="246f4-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="246f4-109">GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="246f4-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="246f4-110">Získá ukazatel rozhraní na doménu aplikace, která obsahuje tuto `ICorDebugAssembly` instanci.</span><span class="sxs-lookup"><span data-stu-id="246f4-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="246f4-111">GetCodeBase – metoda</span><span class="sxs-lookup"><span data-stu-id="246f4-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="246f4-112">Není implementováno v aktuální verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="246f4-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="246f4-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="246f4-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="246f4-114">Získá název sestavení.</span><span class="sxs-lookup"><span data-stu-id="246f4-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="246f4-115">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="246f4-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="246f4-116">Získá instanci ICorDebugProcess, ve které je sestavení spuštěno.</span><span class="sxs-lookup"><span data-stu-id="246f4-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="246f4-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="246f4-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="246f4-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="246f4-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="246f4-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="246f4-119">Requirements</span></span>  
 <span data-ttu-id="246f4-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="246f4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="246f4-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="246f4-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="246f4-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="246f4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="246f4-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="246f4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="246f4-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="246f4-124">See also</span></span>

- [<span data-ttu-id="246f4-125">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="246f4-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
