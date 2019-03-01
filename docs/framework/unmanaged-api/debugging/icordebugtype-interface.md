---
title: ICorDebugType – rozhraní
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
ms.openlocfilehash: 3e3d1173ac6fb14a380cdbc99882fd9baee6552a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966029"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="c94ae-102">ICorDebugType – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c94ae-102">ICorDebugType Interface</span></span>
<span data-ttu-id="c94ae-103">Představuje typ, základní nebo komplexní (který je definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="c94ae-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="c94ae-104">Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="c94ae-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c94ae-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c94ae-105">Methods</span></span>  
  
|<span data-ttu-id="c94ae-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-106">Method</span></span>|<span data-ttu-id="c94ae-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c94ae-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c94ae-108">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="c94ae-109">Získá ukazatel rozhraní icordebugtypeenum –, který odkazuje na Obecné <xref:System.Type> parametry třída odkazovaná tímto objektem `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c94ae-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="c94ae-110">GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="c94ae-111">Získá ukazatel rozhraní k `ICorDebugType` , který odkazuje na základní třídu třídy odkazuje toto `ICorDebugType`, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="c94ae-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="c94ae-112">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="c94ae-113">Získá ukazatel rozhraní k ICorDebugClass, odkazující na konstruktoru typu tohoto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c94ae-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="c94ae-114">GetFirstTypeParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="c94ae-115">Získá ukazatel rozhraní k `ICorDebugType` , která odkazuje na první obecný <xref:System.Type> parametr pro konstruktor třídy odkazuje toto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c94ae-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="c94ae-116">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="c94ae-117">Získá počet dimenzí v typu pole.</span><span class="sxs-lookup"><span data-stu-id="c94ae-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="c94ae-118">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="c94ae-119">Získá ukazatel rozhraní k ICorDebugValue, obsahující hodnotu statické pole určené pole odkazuje tokenu v určeném zásobníku rámce.</span><span class="sxs-lookup"><span data-stu-id="c94ae-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="c94ae-120">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="c94ae-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="c94ae-121">Získá hodnotu corelementtype –, který popisuje nativní typ modulu common language runtime <xref:System.Type> odkazovaná tímto objektem `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c94ae-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c94ae-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c94ae-122">Remarks</span></span>  
 <span data-ttu-id="c94ae-123">Pokud je typ obecný, `ICorDebugClass` představuje typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="c94ae-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="c94ae-124">`ICorDebugType` Rozhraní představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c94ae-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="c94ae-125">Například zatřiďovací tabulky\<K, V > by být reprezentována `ICorDebugClass`, zatímco zatřiďovací tabulky\<Int32, String > by být reprezentována `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c94ae-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="c94ae-126">Neobecné typy jsou reprezentovány obě `ICorDebugClass` a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c94ae-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="c94ae-127">Druhá možnost rozhraní byla zavedena v rozhraní .NET Framework verze 2.0 k vytvoření instance typu řešení.</span><span class="sxs-lookup"><span data-stu-id="c94ae-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c94ae-128">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="c94ae-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94ae-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c94ae-129">Requirements</span></span>  
 <span data-ttu-id="c94ae-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c94ae-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94ae-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c94ae-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c94ae-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c94ae-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c94ae-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c94ae-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94ae-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c94ae-134">See also</span></span>
- [<span data-ttu-id="c94ae-135">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c94ae-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
