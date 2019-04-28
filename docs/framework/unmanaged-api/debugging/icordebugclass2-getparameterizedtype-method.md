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
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750765"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="a2e47-102">ICorDebugClass2::GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="a2e47-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="a2e47-103">Získá deklarace typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2e47-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2e47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2e47-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="a2e47-106">[in] Hodnota corelementtype – výčet, který určuje typ elementu pro tuto třídu: Nastavte tuto hodnotu na typ ELEMENT_TYPE_VALUETYPE, který, pokud tento icordebugclass2 – představuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a2e47-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="a2e47-107">Pokud tuto hodnotu nastavit na za řetězcem ELEMENT_TYPE_CLASS `ICorDebugClass2` představuje komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="a2e47-108">[in] Počet parametrů typu, pokud typ není obecný.</span><span class="sxs-lookup"><span data-stu-id="a2e47-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="a2e47-109">Počet parametrů typu (pokud existuje) musí odpovídat počtu požadovaného třídy.</span><span class="sxs-lookup"><span data-stu-id="a2e47-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="a2e47-110">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který reprezentuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="a2e47-111">Pokud je třída neobecnou, je tato hodnota null.</span><span class="sxs-lookup"><span data-stu-id="a2e47-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a2e47-112">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="a2e47-113">Tento objekt je ekvivalentní <xref:System.Type> objektu ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2e47-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2e47-114">Remarks</span></span>  
 <span data-ttu-id="a2e47-115">Pokud je třída neobecnou, to znamená, pokud nemá žádné parametry typu `GetParameterizedType` jednoduše načte běhový objekt type odpovídající třídu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="a2e47-116">`elementType` Parametr musí být nastavena na správný elementární typ pro třídu: Typ ELEMENT_TYPE_VALUETYPE, který pokud je hodnota typu; třída v opačném případě za řetězcem ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="a2e47-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="a2e47-117">Pokud třída přijímá parametry typu (například `ArrayList<T>`), můžete použít `GetParameterizedType` k vytvoření objektu typu u typu tvořícího instanci jako `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="a2e47-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="a2e47-118">Základní informace</span><span class="sxs-lookup"><span data-stu-id="a2e47-118">Background Information</span></span>  
 <span data-ttu-id="a2e47-119">V rozhraní .NET Framework verze 1.0 a 1.1 všechny typy v metadatech přímo mapovat na typ v běžící proces.</span><span class="sxs-lookup"><span data-stu-id="a2e47-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="a2e47-120">Proto typ metadat a typ prostředí runtime došlo jednotné vyjádření v běžící proces.</span><span class="sxs-lookup"><span data-stu-id="a2e47-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="a2e47-121">Jednoho obecného typu v metadatech však lze mapovat na mnoha různým konkretizacím typu v běžící proces.</span><span class="sxs-lookup"><span data-stu-id="a2e47-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="a2e47-122">Například typ metadat `SortedList<K,V>` můžete namapovat na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a2e47-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="a2e47-123">Proto je třeba způsob, jak zpracovat vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="a2e47-124">Představuje rozhraní .NET Framework verze 2.0 `ICorDebugType` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a2e47-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="a2e47-125">Pro obecný typ `ICorDebugClass` nebo `ICorDebugClass2` objekt představuje typ bez instancí (`SortedList<K,V>`) a `ICorDebugType` objekt představuje různé instance.</span><span class="sxs-lookup"><span data-stu-id="a2e47-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="a2e47-126">Vzhledem `ICorDebugClass` nebo `ICorDebugClass2` objektu, můžete vytvořit `ICorDebugType` objekt pro všechny instance voláním `ICorDebugClass2::GetParameterizedType` metoda.</span><span class="sxs-lookup"><span data-stu-id="a2e47-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="a2e47-127">Můžete taky vytvořit `ICorDebugType` objekt pro jednoduchý typ., jako je například Int32, nebo u jiného než obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="a2e47-128">Po zavedení služby `ICorDebugType` objekt reprezentující pojem run-time typu má zvlněný efekt v celém rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="a2e47-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="a2e47-129">Funkce, které dřív trval `ICorDebugClass` nebo `ICorDebugClass2` objektu nebo dokonce `CorElementType` hodnotu zobecněné provést `ICorDebugType` objektu.</span><span class="sxs-lookup"><span data-stu-id="a2e47-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e47-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2e47-130">Requirements</span></span>  
 <span data-ttu-id="a2e47-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2e47-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e47-132">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2e47-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2e47-133">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2e47-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2e47-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e47-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
