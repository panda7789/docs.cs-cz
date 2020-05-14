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
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396693"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="375fc-102">ICorDebugType – rozhraní</span><span class="sxs-lookup"><span data-stu-id="375fc-102">ICorDebugType Interface</span></span>
<span data-ttu-id="375fc-103">Představuje typ buď Basic, nebo Complex (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="375fc-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="375fc-104">Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="375fc-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="375fc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="375fc-105">Methods</span></span>  
  
|<span data-ttu-id="375fc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-106">Method</span></span>|<span data-ttu-id="375fc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="375fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="375fc-108">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-108">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="375fc-109">Získá ukazatel rozhraní na objekt ICorDebugTypeEnum, který odkazuje na obecné <xref:System.Type> parametry třídy, na kterou odkazuje `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="375fc-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="375fc-110">GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-110">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="375fc-111">Získá ukazatel rozhraní `ICorDebugType` , který odkazuje na základní třídu třídy, na kterou odkazuje `ICorDebugType` , pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="375fc-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="375fc-112">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-112">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="375fc-113">Získá ukazatel rozhraní na ICorDebugClass, který odkazuje na konstruktor typu this `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="375fc-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="375fc-114">GetFirstTypeParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-114">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="375fc-115">Získá ukazatel rozhraní `ICorDebugType` , který odkazuje na první obecný <xref:System.Type> parametr pro konstruktor třídy, na kterou odkazuje tento objekt `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="375fc-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="375fc-116">GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-116">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="375fc-117">Získá počet rozměrů v typu pole.</span><span class="sxs-lookup"><span data-stu-id="375fc-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="375fc-118">GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-118">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="375fc-119">Získá ukazatel rozhraní na ICorDebugValue, který obsahuje hodnotu statického pole, na které odkazuje zadaný token pole v zadaném bloku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="375fc-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="375fc-120">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="375fc-120">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="375fc-121">Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime), na který <xref:System.Type> odkazuje `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="375fc-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="375fc-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="375fc-122">Remarks</span></span>  
 <span data-ttu-id="375fc-123">Pokud je typ obecný, `ICorDebugClass` představuje nevytvořený typ.</span><span class="sxs-lookup"><span data-stu-id="375fc-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="375fc-124">`ICorDebugType`Rozhraní představuje instanci generického typu.</span><span class="sxs-lookup"><span data-stu-id="375fc-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="375fc-125">Například zatřiďovací tabulka \< K, V> by měla být reprezentována `ICorDebugClass` , zatímco zatřiďovací tabulka \< Int32, řetězec> by představoval `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="375fc-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="375fc-126">Neobecné typy jsou reprezentovány v `ICorDebugClass` a `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="375fc-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="375fc-127">Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.</span><span class="sxs-lookup"><span data-stu-id="375fc-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="375fc-128">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="375fc-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="375fc-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="375fc-129">Requirements</span></span>  
 <span data-ttu-id="375fc-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="375fc-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="375fc-131">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="375fc-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="375fc-132">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="375fc-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="375fc-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="375fc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="375fc-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="375fc-134">See also</span></span>

- [<span data-ttu-id="375fc-135">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="375fc-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
