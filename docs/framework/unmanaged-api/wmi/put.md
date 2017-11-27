---
title: "PUT – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce Put přiřadí novou hodnotu s názvem vlastnosti."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c4ad979a3a662618ab62b52d63bda3dbb1e71b9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="put-function"></a><span data-ttu-id="7cbf8-103">PUT – funkce</span><span class="sxs-lookup"><span data-stu-id="7cbf8-103">Put function</span></span>
<span data-ttu-id="7cbf8-104">Nastaví vlastnost s názvem na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="7cbf8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cbf8-105">Syntax</span></span>  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a><span data-ttu-id="7cbf8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cbf8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7cbf8-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7cbf8-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="7cbf8-109">[v] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-109">[in] The name of the property.</span></span> <span data-ttu-id="7cbf8-110">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-110">This parameter cannot be `null`.</span></span>

`lFlags`  
<span data-ttu-id="7cbf8-111">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-111">[in] Reserved.</span></span> <span data-ttu-id="7cbf8-112">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-112">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="7cbf8-113">[v] Ukazatel na platnou `VARIANT` , stane se nová hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="7cbf8-114">Pokud `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`, je nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span> 

`vtType`  
<span data-ttu-id="7cbf8-115">[v] Typ `VARIANT` na kterou odkazuje `pVal`.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="7cbf8-116">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-116">See the [Remarks](#remarks) section for more information.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="7cbf8-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7cbf8-117">Return value</span></span>

<span data-ttu-id="7cbf8-118">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="7cbf8-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7cbf8-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7cbf8-119">Constant</span></span>  |<span data-ttu-id="7cbf8-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7cbf8-120">Value</span></span>  |<span data-ttu-id="7cbf8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="7cbf8-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="7cbf8-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="7cbf8-122">0x80041001</span></span> | <span data-ttu-id="7cbf8-123">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7cbf8-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7cbf8-124">0x80041008</span></span> | <span data-ttu-id="7cbf8-125">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="7cbf8-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="7cbf8-126">0x8004102a</span></span> | <span data-ttu-id="7cbf8-127">Typ vlastnosti nebyl rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-127">The property type is not recognized.</span></span> <span data-ttu-id="7cbf8-128">Tato hodnota se vrátí při vytváření instancí třídy, pokud třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7cbf8-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7cbf8-129">0x80041006</span></span> | <span data-ttu-id="7cbf8-130">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="7cbf8-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="7cbf8-131">0x80041005</span></span> | <span data-ttu-id="7cbf8-132">Pro instance: Určuje, že `pVal` odkazuje na `VARIANT` nesprávného typu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="7cbf8-133">Definice třídy: vlastnost již existuje v nadřazené třídě a nový typ COM se liší od původního COM typu.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7cbf8-134">0</span><span class="sxs-lookup"><span data-stu-id="7cbf8-134">0</span></span> | <span data-ttu-id="7cbf8-135">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-135">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7cbf8-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7cbf8-136">Remarks</span></span>

<span data-ttu-id="7cbf8-137">Tato funkce zabalí volání [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-137">This function wraps a call to the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="7cbf8-138">Tato funkce vždy přepíše aktuální hodnota vlastnosti novou.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="7cbf8-139">Pokud [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) odkazuje na definice třídy, `Put` vytvoří nebo aktualizuje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-139">If the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="7cbf8-140">Když [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) odkazuje na instanci CIM, `Put` aktualizuje jenom; hodnota vlastnosti `Put` nelze vytvořit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-140">When [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="7cbf8-141">`__CLASS` Systému vlastnost je pouze s možností zápisu během vytváření třídy, když se nemusí být ponecháno prázdné.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="7cbf8-142">Všechny ostatní vlastnosti systému jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-142">All other system properties are read-only.</span></span>

<span data-ttu-id="7cbf8-143">Uživatele nelze vytvořit vlastnosti s názvy, které začínat ani končit podtržítko ("_").</span><span class="sxs-lookup"><span data-stu-id="7cbf8-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="7cbf8-144">Toto je vyhrazená pro systém třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="7cbf8-145">Pokud je vlastnost nastavena `Put` funkce existuje v nadřazené třídě, výchozí hodnota vlastnosti je změnit, dokud se vlastnost typ neodpovídá typu nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="7cbf8-146">Pokud se nejedná o neshodě typů vlastnost neexistuje, je vlastnost ceated.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-146">If the property does not exist and it is not a type mismatch, the property is ceated.</span></span>

<span data-ttu-id="7cbf8-147">Použití `vtType` parametr pouze při vytváření nové vlastnosti v definici třídy CIM a `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="7cbf8-148">V takovém případě `vType` parametr určuje typ modelu CIM vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="7cbf8-149">V každém případě `vtType` musí být 0.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="7cbf8-150">`vtType`musí také být 0, pokud je základní objekt instancí (i když `Val` je `null`) vzhledem k tomu, že typem vlastnosti je pevná a nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>   

## <a name="example"></a><span data-ttu-id="7cbf8-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cbf8-151">Example</span></span>

<span data-ttu-id="7cbf8-152">Příklad, naleznete v části [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="7cbf8-152">For an example, see the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7cbf8-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cbf8-153">Requirements</span></span>  
 <span data-ttu-id="7cbf8-154">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cbf8-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cbf8-155">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7cbf8-155">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7cbf8-156">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7cbf8-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cbf8-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cbf8-157">See also</span></span>  
[<span data-ttu-id="7cbf8-158">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="7cbf8-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
