---
title: ICorDebugClass2::GetParameterizedType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a5b3a28c7250a16e78e199bceff7c9e64517319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408210"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="e437f-102">ICorDebugClass2::GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="e437f-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="e437f-103">Získá deklarace typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="e437f-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e437f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e437f-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e437f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e437f-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="e437f-106">[v] Hodnota CorElementType – výčet, který určuje typ elementu pro tuto třídu: nastavte tuto hodnotu na typ ELEMENT_TYPE_VALUETYPE, který, pokud tato ICorDebugClass2 představuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e437f-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="e437f-107">Pokud nastavením této hodnoty na ELEMENT_TYPE_CLASS `ICorDebugClass2` představuje komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="e437f-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="e437f-108">[v] Počet parametrů typu, pokud je typ Obecné.</span><span class="sxs-lookup"><span data-stu-id="e437f-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="e437f-109">Počet parametrů typů (pokud existuje) musí odpovídat počtu požadovaného v třídě.</span><span class="sxs-lookup"><span data-stu-id="e437f-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="e437f-110">[v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který představuje typ parametru.</span><span class="sxs-lookup"><span data-stu-id="e437f-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="e437f-111">Pokud je třída neobecnou, tato hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="e437f-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="e437f-112">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="e437f-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="e437f-113">Tento objekt je ekvivalentní <xref:System.Type> objektu ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="e437f-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e437f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e437f-114">Remarks</span></span>  
 <span data-ttu-id="e437f-115">Pokud je třída neobecnou, to znamená, pokud ji nemá žádné parametry typu `GetParameterizedType` jednoduše získá odpovídající třídu objekt typu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e437f-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="e437f-116">`elementType` Parametr musí být nastavená na typ správné elementu pro třídu: Typ ELEMENT_TYPE_VALUETYPE, který pokud třída je typu hodnotu, jinak hodnota ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="e437f-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="e437f-117">Pokud třída přijímá parametry typu (například `ArrayList<T>`), můžete použít `GetParameterizedType` vytvořit jako objekt typu pro typ instancí `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="e437f-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="e437f-118">Základní informace</span><span class="sxs-lookup"><span data-stu-id="e437f-118">Background Information</span></span>  
 <span data-ttu-id="e437f-119">V rozhraní .NET Framework verze 1.0 a 1.1 každý typ v metadatech přímo mapovat k typu v běžící proces.</span><span class="sxs-lookup"><span data-stu-id="e437f-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="e437f-120">Proto typ metadat a typ modulu runtime měl jeden reprezentace v běžící proces.</span><span class="sxs-lookup"><span data-stu-id="e437f-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="e437f-121">Jeden obecný typ v metadatech však lze mapovat na mnoha různých instancí možnosti typu v běžící proces.</span><span class="sxs-lookup"><span data-stu-id="e437f-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="e437f-122">Například typ metadat `SortedList<K,V>` můžete namapovat `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e437f-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="e437f-123">Proto musíte způsob, jak zpracovat vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="e437f-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="e437f-124">Představuje rozhraní .NET Framework verze 2.0 `ICorDebugType` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e437f-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="e437f-125">Pro obecný typ `ICorDebugClass` nebo `ICorDebugClass2` objekt představuje typ bez instancí (`SortedList<K,V>`) a `ICorDebugType` objekt představuje různé typy instancí.</span><span class="sxs-lookup"><span data-stu-id="e437f-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="e437f-126">Zadané `ICorDebugClass` nebo `ICorDebugClass2` objekt, můžete vytvořit `ICorDebugType` objekt pro vytváření všech instancí voláním `ICorDebugClass2::GetParameterizedType` metoda.</span><span class="sxs-lookup"><span data-stu-id="e437f-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="e437f-127">Můžete taky vytvořit `ICorDebugType` jednoduchý typ, třeba Int32, nebo pro neobecný typ objektu.</span><span class="sxs-lookup"><span data-stu-id="e437f-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="e437f-128">Zavedení `ICorDebugType` objekt představující běhu představu o typu má vliv ripple v celém rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e437f-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="e437f-129">Funkce, které dříve trvalo `ICorDebugClass` nebo `ICorDebugClass2` objektu nebo dokonce `CorElementType` hodnotu zobecněné provést `ICorDebugType` objektu.</span><span class="sxs-lookup"><span data-stu-id="e437f-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e437f-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e437f-130">Requirements</span></span>  
 <span data-ttu-id="e437f-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e437f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e437f-132">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e437f-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e437f-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e437f-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e437f-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e437f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
