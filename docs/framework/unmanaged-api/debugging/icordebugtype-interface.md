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
ms.openlocfilehash: 4f3f553ed5dc93433610365e0dae5bee54863de5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129631"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="ec0c1-102">ICorDebugType – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec0c1-102">ICorDebugType Interface</span></span>
<span data-ttu-id="ec0c1-103">Představuje typ buď Basic, nebo Complex (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="ec0c1-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="ec0c1-104">Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec0c1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ec0c1-105">Methods</span></span>  
  
|<span data-ttu-id="ec0c1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-106">Method</span></span>|<span data-ttu-id="ec0c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ec0c1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec0c1-108">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="ec0c1-109">Získá ukazatel rozhraní na ICorDebugTypeEnum, který odkazuje na Obecné parametry <xref:System.Type> třídy, na kterou odkazuje tento `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ec0c1-110">GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="ec0c1-111">Získá ukazatel rozhraní na `ICorDebugType`, který odkazuje na základní třídu třídy, na kterou odkazuje tento `ICorDebugType`, pokud jedna existuje.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="ec0c1-112">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="ec0c1-113">Získá ukazatel rozhraní na ICorDebugClass, který odkazuje na typový konstruktor tohoto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ec0c1-114">GetFirstTypeParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="ec0c1-115">Získá ukazatel rozhraní na `ICorDebugType`, který odkazuje na první obecný <xref:System.Type> parametr pro konstruktor třídy, na kterou odkazuje tento `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ec0c1-116">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="ec0c1-117">Získá počet rozměrů v typu pole.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="ec0c1-118">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="ec0c1-119">Získá ukazatel rozhraní na ICorDebugValue, který obsahuje hodnotu statického pole, na které odkazuje zadaný token pole v zadaném bloku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="ec0c1-120">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="ec0c1-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="ec0c1-121">Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime <xref:System.Type>), na který odkazuje tento `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec0c1-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec0c1-122">Remarks</span></span>  
 <span data-ttu-id="ec0c1-123">Pokud je typ obecný, `ICorDebugClass` představuje nevytvořený typ.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="ec0c1-124">Rozhraní `ICorDebugType` představuje instanci generického typu.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="ec0c1-125">Například hodnota hash\<K, V > by měla být reprezentována `ICorDebugClass`, zatímco zatřiďovací tabulka\<Int32, řetězec > by představovala `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="ec0c1-126">Neobecné typy jsou reprezentovány `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="ec0c1-127">Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec0c1-128">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ec0c1-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec0c1-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec0c1-129">Requirements</span></span>  
 <span data-ttu-id="ec0c1-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec0c1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec0c1-131">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec0c1-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec0c1-132">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ec0c1-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec0c1-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec0c1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec0c1-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec0c1-134">See also</span></span>

- [<span data-ttu-id="ec0c1-135">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ec0c1-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
