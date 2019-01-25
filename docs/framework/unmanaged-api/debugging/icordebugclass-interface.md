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
ms.openlocfilehash: d12d952fe540b2ec36d058ae2100f0cf5c8e6bcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710212"
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="d0b52-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="d0b52-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="d0b52-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="d0b52-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="d0b52-104">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="d0b52-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0b52-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d0b52-105">Methods</span></span>  
  
|<span data-ttu-id="d0b52-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0b52-106">Method</span></span>|<span data-ttu-id="d0b52-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d0b52-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0b52-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b52-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="d0b52-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="d0b52-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="d0b52-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b52-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="d0b52-111">Získá hodnotu zadané statické pole.</span><span class="sxs-lookup"><span data-stu-id="d0b52-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="d0b52-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d0b52-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="d0b52-113">Získá `TypeDef` tokenu metadat pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="d0b52-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0b52-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0b52-114">Remarks</span></span>  
 <span data-ttu-id="d0b52-115">`ICorDebugClass` Rozhraní představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="d0b52-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="d0b52-116">Icordebugtype – rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d0b52-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="d0b52-117">Například `Hashtable<K, V>` by být reprezentována `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentována `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="d0b52-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="d0b52-118">Neobecné typy jsou reprezentovány obě `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="d0b52-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="d0b52-119">Druhá možnost rozhraní byla zavedena v rozhraní .NET Framework verze 2.0 k vytvoření instance typu řešení.</span><span class="sxs-lookup"><span data-stu-id="d0b52-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0b52-120">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="d0b52-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0b52-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0b52-121">Requirements</span></span>  
 <span data-ttu-id="d0b52-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0b52-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0b52-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0b52-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0b52-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0b52-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0b52-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0b52-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b52-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0b52-126">See also</span></span>
- [<span data-ttu-id="d0b52-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d0b52-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
