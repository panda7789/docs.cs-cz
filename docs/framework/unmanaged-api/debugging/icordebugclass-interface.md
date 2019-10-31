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
ms.openlocfilehash: 5714597b5e5ca2936aad53217ae934684e75585c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125740"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="2e3c9-102">ICorDebugClass – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e3c9-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="2e3c9-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="2e3c9-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="2e3c9-104">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e3c9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2e3c9-105">Methods</span></span>  
  
|<span data-ttu-id="2e3c9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2e3c9-106">Method</span></span>|<span data-ttu-id="2e3c9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2e3c9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e3c9-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="2e3c9-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="2e3c9-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="2e3c9-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="2e3c9-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="2e3c9-111">Získá hodnotu zadaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="2e3c9-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="2e3c9-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="2e3c9-113">Získá token metadat `TypeDef` pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e3c9-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e3c9-114">Remarks</span></span>  
 <span data-ttu-id="2e3c9-115">Rozhraní `ICorDebugClass` představuje obecný typ uninstanceed.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="2e3c9-116">Rozhraní ICorDebugType představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="2e3c9-117">Například `Hashtable<K, V>` by představoval `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by představoval `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="2e3c9-118">Neobecné typy jsou reprezentovány `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="2e3c9-119">Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e3c9-120">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e3c9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e3c9-121">Requirements</span></span>  
 <span data-ttu-id="2e3c9-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e3c9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e3c9-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e3c9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e3c9-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e3c9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e3c9-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e3c9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3c9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e3c9-126">See also</span></span>

- [<span data-ttu-id="2e3c9-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2e3c9-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
