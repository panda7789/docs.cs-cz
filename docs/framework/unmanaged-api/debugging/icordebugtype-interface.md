---
title: ICorDebugType Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de2871b406bb9da84d20d7c526ad4a703baae409
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422854"
---
# <a name="icordebugtype-interface1"></a><span data-ttu-id="e93c4-102">ICorDebugType Interface1</span><span class="sxs-lookup"><span data-stu-id="e93c4-102">ICorDebugType Interface1</span></span>
<span data-ttu-id="e93c4-103">Představuje typ, základní nebo komplexní (která je, uživatelem definované).</span><span class="sxs-lookup"><span data-stu-id="e93c4-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="e93c4-104">Pokud je typ Obecné, `ICorDebugType` představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="e93c4-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e93c4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e93c4-105">Methods</span></span>  
  
|<span data-ttu-id="e93c4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-106">Method</span></span>|<span data-ttu-id="e93c4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e93c4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e93c4-108">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="e93c4-109">Získá ukazatele rozhraní k ICorDebugTypeEnum, který odkazuje na Obecné <xref:System.Type> parametry třídy odkazuje toto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e93c4-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="e93c4-110">GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="e93c4-111">Získá ukazatele rozhraní k `ICorDebugType` který odkazuje na základní třídy třídy odkazuje toto `ICorDebugType`, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="e93c4-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="e93c4-112">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="e93c4-113">Získá ukazatele rozhraní k ICorDebugClass odkazující typové konstruktoru tohoto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e93c4-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="e93c4-114">GetFirstTypeParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="e93c4-115">Získá ukazatele rozhraní k `ICorDebugType` který odkazuje na první obecná <xref:System.Type> parametr pro konstruktor třídy odkazuje toto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e93c4-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="e93c4-116">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="e93c4-117">Získá počet dimenzí v typu pole.</span><span class="sxs-lookup"><span data-stu-id="e93c4-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="e93c4-118">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="e93c4-119">Získá ukazatele rozhraní k ICorDebugValue, který obsahuje hodnotu statického pole odkazovaná v zadaném poli token v rámci zadaného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e93c4-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="e93c4-120">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="e93c4-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="e93c4-121">Získá hodnotu CorElementType, která popisuje typ nativní modul common language runtime <xref:System.Type> odkazuje toto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e93c4-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e93c4-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e93c4-122">Remarks</span></span>  
 <span data-ttu-id="e93c4-123">Pokud je typ Obecné, `ICorDebugClass` představuje typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="e93c4-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="e93c4-124">`ICorDebugType` Rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="e93c4-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="e93c4-125">Například zatřiďovací tabulky\<tisíc, V > by být reprezentovaná `ICorDebugClass`, zatímco zatřiďovací tabulky\<Int32, řetězec > by být reprezentovaná `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e93c4-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="e93c4-126">Jak jsou reprezentována non obecné typy `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e93c4-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="e93c4-127">Rozhraní pozdější byla zavedena v rozhraní .NET Framework verze 2.0, jak nakládat s vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="e93c4-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e93c4-128">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e93c4-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e93c4-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e93c4-129">Requirements</span></span>  
 <span data-ttu-id="e93c4-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e93c4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e93c4-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e93c4-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e93c4-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e93c4-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e93c4-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e93c4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93c4-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e93c4-134">See Also</span></span>  
 [<span data-ttu-id="e93c4-135">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e93c4-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
