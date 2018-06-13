---
title: ICorDebugClass Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bec35babec96da5ca5d527b19f853b4ce1c384e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406933"
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="fe37f-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="fe37f-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="fe37f-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="fe37f-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="fe37f-104">Pokud je typ Obecné, `ICorDebugClass` představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fe37f-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe37f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fe37f-105">Methods</span></span>  
  
|<span data-ttu-id="fe37f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fe37f-106">Method</span></span>|<span data-ttu-id="fe37f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fe37f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe37f-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="fe37f-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="fe37f-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="fe37f-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="fe37f-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="fe37f-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="fe37f-111">Získá hodnotu zadaného pole statické.</span><span class="sxs-lookup"><span data-stu-id="fe37f-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="fe37f-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="fe37f-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="fe37f-113">Získá `TypeDef` token metadata pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="fe37f-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe37f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe37f-114">Remarks</span></span>  
 <span data-ttu-id="fe37f-115">`ICorDebugClass` Rozhraní představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fe37f-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="fe37f-116">ICorDebugType rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fe37f-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="fe37f-117">Například `Hashtable<K, V>` by být reprezentovaná `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentovaná `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="fe37f-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="fe37f-118">Jak jsou reprezentována non obecné typy `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="fe37f-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="fe37f-119">Rozhraní pozdější byla zavedena v rozhraní .NET Framework verze 2.0, jak nakládat s vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="fe37f-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe37f-120">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="fe37f-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe37f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe37f-121">Requirements</span></span>  
 <span data-ttu-id="fe37f-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe37f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe37f-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe37f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe37f-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe37f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe37f-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe37f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe37f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe37f-126">See Also</span></span>  
 [<span data-ttu-id="fe37f-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fe37f-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
