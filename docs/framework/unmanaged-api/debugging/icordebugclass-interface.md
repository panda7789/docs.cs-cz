---
title: ICorDebugClass – rozhraní
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
ms.openlocfilehash: 9beb8930143cbb0cc7dd8dd68a65b42d92563e31
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972050"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="a6a93-102">ICorDebugClass – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6a93-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="a6a93-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="a6a93-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="a6a93-104">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="a6a93-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6a93-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a6a93-105">Methods</span></span>  
  
|<span data-ttu-id="a6a93-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a6a93-106">Method</span></span>|<span data-ttu-id="a6a93-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a6a93-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6a93-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="a6a93-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="a6a93-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="a6a93-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="a6a93-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a6a93-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="a6a93-111">Získá hodnotu zadané statické pole.</span><span class="sxs-lookup"><span data-stu-id="a6a93-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="a6a93-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a6a93-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="a6a93-113">Získá `TypeDef` tokenu metadat pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="a6a93-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6a93-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6a93-114">Remarks</span></span>  
 <span data-ttu-id="a6a93-115">`ICorDebugClass` Rozhraní představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="a6a93-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="a6a93-116">Icordebugtype – rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a6a93-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="a6a93-117">Například `Hashtable<K, V>` by být reprezentována `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentována `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a6a93-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="a6a93-118">Neobecné typy jsou reprezentovány obě `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a6a93-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="a6a93-119">Druhá možnost rozhraní byla zavedena v rozhraní .NET Framework verze 2.0 k vytvoření instance typu řešení.</span><span class="sxs-lookup"><span data-stu-id="a6a93-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6a93-120">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="a6a93-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6a93-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6a93-121">Requirements</span></span>  
 <span data-ttu-id="a6a93-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6a93-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a93-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6a93-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6a93-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6a93-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6a93-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a93-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a93-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6a93-126">See also</span></span>
- [<span data-ttu-id="a6a93-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a6a93-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
