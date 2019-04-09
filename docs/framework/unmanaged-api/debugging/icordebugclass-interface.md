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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133624"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="f9006-102">ICorDebugClass – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9006-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="f9006-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="f9006-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="f9006-104">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="f9006-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9006-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f9006-105">Methods</span></span>  
  
|<span data-ttu-id="f9006-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f9006-106">Method</span></span>|<span data-ttu-id="f9006-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f9006-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9006-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="f9006-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="f9006-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="f9006-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="f9006-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="f9006-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="f9006-111">Získá hodnotu zadané statické pole.</span><span class="sxs-lookup"><span data-stu-id="f9006-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="f9006-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="f9006-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="f9006-113">Získá `TypeDef` tokenu metadat pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="f9006-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9006-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9006-114">Remarks</span></span>  
 <span data-ttu-id="f9006-115">`ICorDebugClass` Rozhraní představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="f9006-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="f9006-116">Icordebugtype – rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f9006-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="f9006-117">Například `Hashtable<K, V>` by být reprezentována `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentována `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="f9006-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="f9006-118">Neobecné typy jsou reprezentovány obě `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="f9006-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="f9006-119">Druhá možnost rozhraní byla zavedena v rozhraní .NET Framework verze 2.0 k vytvoření instance typu řešení.</span><span class="sxs-lookup"><span data-stu-id="f9006-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9006-120">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="f9006-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9006-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9006-121">Requirements</span></span>  
 <span data-ttu-id="f9006-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9006-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9006-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9006-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9006-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9006-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f9006-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f9006-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9006-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9006-126">See also</span></span>

- [<span data-ttu-id="f9006-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9006-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
