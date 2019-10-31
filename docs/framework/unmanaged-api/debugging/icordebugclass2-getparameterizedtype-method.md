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
ms.openlocfilehash: 64537ab97c1256cc6f963999b027bafc25cbbccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125733"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="883f3-102">ICorDebugClass2::GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="883f3-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="883f3-103">Získá deklaraci typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="883f3-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="883f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="883f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="883f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="883f3-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="883f3-106">pro Hodnota výčtu CorElementType –, která určuje typ elementu pro tuto třídu: tuto hodnotu nastavte na ELEMENT_TYPE_VALUETYPE, pokud tento ICorDebugClass2 představuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="883f3-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="883f3-107">Nastavte tuto hodnotu na ELEMENT_TYPE_CLASS, pokud tento `ICorDebugClass2` představuje komplexní typ.</span><span class="sxs-lookup"><span data-stu-id="883f3-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="883f3-108">pro Počet parametrů typu, pokud je typ obecný.</span><span class="sxs-lookup"><span data-stu-id="883f3-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="883f3-109">Počet parametrů typu (pokud existuje) musí odpovídat číslu požadovanému třídou.</span><span class="sxs-lookup"><span data-stu-id="883f3-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="883f3-110">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="883f3-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="883f3-111">Pokud třída není obecná, tato hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="883f3-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="883f3-112">mimo Ukazatel na adresu `ICorDebugType`ho objektu, který představuje deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="883f3-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="883f3-113">Tento objekt je ekvivalentní objektu <xref:System.Type> ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="883f3-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="883f3-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="883f3-114">Remarks</span></span>  
 <span data-ttu-id="883f3-115">Pokud třída není obecná, to znamená, pokud nemá žádné parametry typu, `GetParameterizedType` jednoduše načte objekt typu modulu runtime odpovídající třídě.</span><span class="sxs-lookup"><span data-stu-id="883f3-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="883f3-116">Parametr `elementType` by měl být nastaven na správný typ elementu pro třídu: ELEMENT_TYPE_VALUETYPE, pokud je třída typem hodnoty; v opačném případě ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="883f3-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="883f3-117">Pokud třída přijímá parametry typu (například `ArrayList<T>`), můžete použít `GetParameterizedType` k vytvoření objektu typu pro instanci typu, jako je například `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="883f3-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="883f3-118">Základní informace</span><span class="sxs-lookup"><span data-stu-id="883f3-118">Background Information</span></span>  
 <span data-ttu-id="883f3-119">V .NET Framework verzích 1,0 a 1,1 může být každý typ v metadatech přímo mapován na typ v běžícím procesu.</span><span class="sxs-lookup"><span data-stu-id="883f3-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="883f3-120">Proto typ metadat a typ modulu runtime mají v běžícím procesu jednu reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="883f3-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="883f3-121">Jeden obecný typ v metadatech však lze namapovat na mnoho různých instancí typu v běžícím procesu.</span><span class="sxs-lookup"><span data-stu-id="883f3-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="883f3-122">Například typ metadat `SortedList<K,V>` lze namapovat na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="883f3-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="883f3-123">Proto potřebujete způsob, jak zpracovat instanci typu.</span><span class="sxs-lookup"><span data-stu-id="883f3-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="883f3-124">.NET Framework verze 2,0 zavádí rozhraní `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="883f3-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="883f3-125">Pro obecný typ objekt `ICorDebugClass` nebo `ICorDebugClass2` představuje neinstanciní typ (`SortedList<K,V>`) a objekt `ICorDebugType` představuje různé typy s vytvořenými instancemi.</span><span class="sxs-lookup"><span data-stu-id="883f3-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="883f3-126">Pro objekt `ICorDebugClass` nebo `ICorDebugClass2` můžete vytvořit objekt `ICorDebugType` pro jakoukoliv instanci voláním metody `ICorDebugClass2::GetParameterizedType`.</span><span class="sxs-lookup"><span data-stu-id="883f3-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="883f3-127">Můžete také vytvořit objekt `ICorDebugType` pro jednoduchý typ, jako je Int32 nebo pro neobecný typ.</span><span class="sxs-lookup"><span data-stu-id="883f3-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="883f3-128">Zavedení objektu `ICorDebugType`, který představuje pojem běhu typu, má v rámci rozhraní API efekt Ripple.</span><span class="sxs-lookup"><span data-stu-id="883f3-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="883f3-129">Funkce, které dříve trvaly objekt `ICorDebugClass` nebo `ICorDebugClass2` nebo i hodnota `CorElementType`, jsou zobecněny k převzetí objektu `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="883f3-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="883f3-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="883f3-130">Requirements</span></span>  
 <span data-ttu-id="883f3-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="883f3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883f3-132">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="883f3-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="883f3-133">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="883f3-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="883f3-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="883f3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
