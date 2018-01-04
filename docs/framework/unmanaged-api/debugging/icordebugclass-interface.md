---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3998cf76430612759f69df07fb4f5afebd7a25ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="7a712-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="7a712-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="7a712-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="7a712-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="7a712-104">Pokud je typ Obecné, `ICorDebugClass` představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7a712-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a712-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7a712-105">Methods</span></span>  
  
|<span data-ttu-id="7a712-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7a712-106">Method</span></span>|<span data-ttu-id="7a712-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7a712-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a712-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="7a712-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="7a712-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="7a712-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="7a712-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="7a712-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="7a712-111">Získá hodnotu zadaného pole statické.</span><span class="sxs-lookup"><span data-stu-id="7a712-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="7a712-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7a712-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="7a712-113">Získá `TypeDef` token metadata pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="7a712-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a712-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a712-114">Remarks</span></span>  
 <span data-ttu-id="7a712-115">`ICorDebugClass` Rozhraní představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7a712-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="7a712-116">ICorDebugType rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7a712-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="7a712-117">Například `Hashtable<K, V>` by být reprezentovaná `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentovaná `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7a712-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="7a712-118">Jak jsou reprezentována non obecné typy `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7a712-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="7a712-119">Rozhraní pozdější byla zavedena v rozhraní .NET Framework verze 2.0, jak nakládat s vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="7a712-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a712-120">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7a712-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a712-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a712-121">Requirements</span></span>  
 <span data-ttu-id="7a712-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a712-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a712-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a712-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a712-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a712-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a712-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a712-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a712-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a712-126">See Also</span></span>  
 [<span data-ttu-id="7a712-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7a712-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
