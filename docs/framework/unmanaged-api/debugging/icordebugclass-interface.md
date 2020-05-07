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
ms.openlocfilehash: d7417e8dc193172c77d23fe3fa72c8298d802b5c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894045"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="7705f-102">ICorDebugClass – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7705f-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="7705f-103">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="7705f-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="7705f-104">Pokud je typ obecný, představuje `ICorDebugClass` obecný typ bez instance.</span><span class="sxs-lookup"><span data-stu-id="7705f-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7705f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7705f-105">Methods</span></span>  
  
|<span data-ttu-id="7705f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7705f-106">Method</span></span>|<span data-ttu-id="7705f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7705f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7705f-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="7705f-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="7705f-109">Získá modul, který definuje tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="7705f-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="7705f-110">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="7705f-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="7705f-111">Získá hodnotu zadaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="7705f-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="7705f-112">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7705f-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="7705f-113">Získá token `TypeDef` metadat pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="7705f-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7705f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7705f-114">Remarks</span></span>  
 <span data-ttu-id="7705f-115">`ICorDebugClass` Rozhraní představuje obecný typ uninstanceed.</span><span class="sxs-lookup"><span data-stu-id="7705f-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="7705f-116">Rozhraní ICorDebugType představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="7705f-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="7705f-117">Například `Hashtable<K, V>` by `ICorDebugClass`představovala, že `Hashtable<Int32, String>` by představoval. `ICorDebugType`</span><span class="sxs-lookup"><span data-stu-id="7705f-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="7705f-118">Neobecné typy jsou reprezentovány v `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7705f-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="7705f-119">Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.</span><span class="sxs-lookup"><span data-stu-id="7705f-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7705f-120">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7705f-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7705f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7705f-121">Requirements</span></span>  
 <span data-ttu-id="7705f-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7705f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7705f-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7705f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7705f-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7705f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7705f-125">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7705f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7705f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7705f-126">See also</span></span>

- [<span data-ttu-id="7705f-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7705f-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
