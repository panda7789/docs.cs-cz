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
ms.openlocfilehash: 7e1ad830e728fbe764085a5808a48e4cacedc595
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133624"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="584db-102">ICorDebugClass – rozhraní</span><span class="sxs-lookup"><span data-stu-id="584db-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="584db-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="584db-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="584db-104">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="584db-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="584db-105">Metody</span><span class="sxs-lookup"><span data-stu-id="584db-105">Methods</span></span>  
  
|<span data-ttu-id="584db-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="584db-106">Method</span></span>|<span data-ttu-id="584db-107">Popis</span><span class="sxs-lookup"><span data-stu-id="584db-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="584db-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="584db-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="584db-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="584db-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="584db-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="584db-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="584db-111">Získá hodnotu zadané statické pole.</span><span class="sxs-lookup"><span data-stu-id="584db-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="584db-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="584db-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="584db-113">Získá `TypeDef` tokenu metadat pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="584db-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="584db-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="584db-114">Remarks</span></span>  
 <span data-ttu-id="584db-115">`ICorDebugClass` Rozhraní představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="584db-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="584db-116">Icordebugtype – rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="584db-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="584db-117">Například `Hashtable<K, V>` by být reprezentována `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentována `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="584db-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="584db-118">Neobecné typy jsou reprezentovány obě `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="584db-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="584db-119">Druhá možnost rozhraní byla zavedena v rozhraní .NET Framework verze 2.0 k vytvoření instance typu řešení.</span><span class="sxs-lookup"><span data-stu-id="584db-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="584db-120">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="584db-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="584db-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="584db-121">Requirements</span></span>  
 <span data-ttu-id="584db-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="584db-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="584db-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="584db-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="584db-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="584db-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="584db-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="584db-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="584db-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="584db-126">See also</span></span>

- [<span data-ttu-id="584db-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="584db-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
