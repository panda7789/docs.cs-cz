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
ms.openlocfilehash: 79e93a44f2cc532286a7e9b01fa32292a4e1c69a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="34af8-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="34af8-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="34af8-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="34af8-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="34af8-104">Pokud je typ Obecné, `ICorDebugClass` představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="34af8-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34af8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="34af8-105">Methods</span></span>  
  
|<span data-ttu-id="34af8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="34af8-106">Method</span></span>|<span data-ttu-id="34af8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="34af8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34af8-108">Getmodule – metoda</span><span class="sxs-lookup"><span data-stu-id="34af8-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="34af8-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="34af8-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="34af8-110">Getstaticfieldvalue – metoda</span><span class="sxs-lookup"><span data-stu-id="34af8-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="34af8-111">Získá hodnotu zadaného pole statické.</span><span class="sxs-lookup"><span data-stu-id="34af8-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="34af8-112">Gettoken – metoda</span><span class="sxs-lookup"><span data-stu-id="34af8-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="34af8-113">Získá `TypeDef` token metadata pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="34af8-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34af8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34af8-114">Remarks</span></span>  
 <span data-ttu-id="34af8-115">`ICorDebugClass` Rozhraní představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="34af8-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="34af8-116">ICorDebugType rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="34af8-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="34af8-117">Například `Hashtable<K, V>` by být reprezentovaná `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentovaná `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="34af8-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="34af8-118">Jak jsou reprezentována non obecné typy `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="34af8-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="34af8-119">Rozhraní pozdější byla zavedena v rozhraní .NET Framework verze 2.0, jak nakládat s vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="34af8-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34af8-120">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="34af8-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34af8-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34af8-121">Requirements</span></span>  
 <span data-ttu-id="34af8-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34af8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34af8-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34af8-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34af8-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34af8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34af8-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34af8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34af8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="34af8-126">See Also</span></span>  
 [<span data-ttu-id="34af8-127">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="34af8-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
