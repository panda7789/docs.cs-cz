---
title: "GetNames – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetNames načte názvy vlastností objektu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetNames
helpviewer_keywords: GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2ba2530dd43e6924187c80214d5efa13ebc548de
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="getnames-function"></a><span data-ttu-id="166f6-103">GetNames – funkce</span><span class="sxs-lookup"><span data-stu-id="166f6-103">GetNames function</span></span>
<span data-ttu-id="166f6-104">Načte podmnožinu nebo všechny názvy vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="166f6-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="166f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166f6-105">Syntax</span></span>  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="166f6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="166f6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="166f6-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="166f6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="166f6-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="166f6-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="166f6-109">[v] Ukazatel na platnou `LPCWSTR` určující kvalifikátor název, který funguje jako součást filtru.</span><span class="sxs-lookup"><span data-stu-id="166f6-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="166f6-110">Další informace najdete v tématu [poznámky](#remarks) části.</span><span class="sxs-lookup"><span data-stu-id="166f6-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="166f6-111">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="166f6-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="166f6-112">[v] Kombinace bitových polí.</span><span class="sxs-lookup"><span data-stu-id="166f6-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="166f6-113">Další informace najdete v tématu [poznámky](#remarks) části.</span><span class="sxs-lookup"><span data-stu-id="166f6-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="166f6-114">[v] Ukazatel na platnou `VARIANT` struktura inicializována tak, aby hodnota filtru.</span><span class="sxs-lookup"><span data-stu-id="166f6-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="166f6-115">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="166f6-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="166f6-116">[out] A `SAFEARRAY` struktura, která obsahuje názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="166f6-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="166f6-117">Na záznam, musí být tento parametr vždycky ukazatel na `null`.</span><span class="sxs-lookup"><span data-stu-id="166f6-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="166f6-118">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="166f6-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="166f6-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="166f6-119">Return value</span></span>

<span data-ttu-id="166f6-120">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="166f6-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="166f6-121">Konstanta</span><span class="sxs-lookup"><span data-stu-id="166f6-121">Constant</span></span>  |<span data-ttu-id="166f6-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="166f6-122">Value</span></span>  |<span data-ttu-id="166f6-123">Popis</span><span class="sxs-lookup"><span data-stu-id="166f6-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="166f6-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="166f6-124">0x80041001</span></span> | <span data-ttu-id="166f6-125">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="166f6-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="166f6-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="166f6-126">0x80041008</span></span> | <span data-ttu-id="166f6-127">Jeden nebo více parametrů nejsou platné nebo byl zadán nesprávný kombinace příznaky a parametry.</span><span class="sxs-lookup"><span data-stu-id="166f6-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="166f6-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="166f6-128">0x80041006</span></span> | <span data-ttu-id="166f6-129">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="166f6-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="166f6-130">0</span><span class="sxs-lookup"><span data-stu-id="166f6-130">0</span></span> | <span data-ttu-id="166f6-131">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="166f6-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="166f6-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="166f6-132">Remarks</span></span>

<span data-ttu-id="166f6-133">Tato funkce zabalí volání [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="166f6-133">This function wraps a call to the [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="166f6-134">Pojmenované vrátil jsou řízeny kombinaci příznaky a parametry.</span><span class="sxs-lookup"><span data-stu-id="166f6-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="166f6-135">Například funkce může vrátit názvy všech vlastností nebo pouze názvy klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="166f6-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="166f6-136">Primárním filtru je uveden v `lFlags` parametr a ostatní parametry lišit v závislosti na jeho.</span><span class="sxs-lookup"><span data-stu-id="166f6-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="166f6-137">Příznak hodnoty v `lFlags` jsou bitová pole</span><span class="sxs-lookup"><span data-stu-id="166f6-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="166f6-138">Příznaky, které lze předat jako `lEnumFlags` argument jsou bitová pole, které jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="166f6-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="166f6-139">Můžete kombinovat jeden příznak z každé skupiny libovolný příznakem z jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="166f6-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="166f6-140">Příznaky ze stejné skupiny jsou však vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="166f6-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="166f6-141">Příznaky skupina 1</span><span class="sxs-lookup"><span data-stu-id="166f6-141">Group 1 flags</span></span> |<span data-ttu-id="166f6-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="166f6-142">Value</span></span>  |<span data-ttu-id="166f6-143">Popis</span><span class="sxs-lookup"><span data-stu-id="166f6-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="166f6-144">0</span><span class="sxs-lookup"><span data-stu-id="166f6-144">0</span></span> | <span data-ttu-id="166f6-145">Vrátí všechny názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="166f6-145">Return all property names.</span></span> <span data-ttu-id="166f6-146">`strQualifierName`a `pQualifierVal` se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="166f6-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="166f6-147">1</span><span class="sxs-lookup"><span data-stu-id="166f6-147">1</span></span> | <span data-ttu-id="166f6-148">Vrátí pouze vlastnosti, které mají kvalifikátor název určený správcem `strQualifierName` parametr.</span><span class="sxs-lookup"><span data-stu-id="166f6-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="166f6-149">Pokud tento příznak se používá, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="166f6-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="166f6-150">2</span><span class="sxs-lookup"><span data-stu-id="166f6-150">2</span></span> |  <span data-ttu-id="166f6-151">Vrátí pouze vlastnosti, které nemají kvalifikátor název zadaný `strQualifierName` parametr.</span><span class="sxs-lookup"><span data-stu-id="166f6-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="166f6-152">Pokud tento příznak se používá, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="166f6-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="166f6-153">3</span><span class="sxs-lookup"><span data-stu-id="166f6-153">3</span></span> | <span data-ttu-id="166f6-154">Vrátí pouze vlastnosti, které mají kvalifikátor název zadaný `wszQualifierName` parametr a mají také stejná jako určeného hodnotu `pQualifierVal` struktura.</span><span class="sxs-lookup"><span data-stu-id="166f6-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="166f6-155">Pokud tento příznak se používá, musíte zadat oba `wszQualifierName` a `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="166f6-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="166f6-156">Skupina 2 příznaky</span><span class="sxs-lookup"><span data-stu-id="166f6-156">Group 2 flags</span></span> |<span data-ttu-id="166f6-157">Hodnota</span><span class="sxs-lookup"><span data-stu-id="166f6-157">Value</span></span>  |<span data-ttu-id="166f6-158">Popis</span><span class="sxs-lookup"><span data-stu-id="166f6-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="166f6-159">0x4</span><span class="sxs-lookup"><span data-stu-id="166f6-159">0x4</span></span> | <span data-ttu-id="166f6-160">Vrátí pouze názvy vlastností, které definují klíče.</span><span class="sxs-lookup"><span data-stu-id="166f6-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="166f6-161">0x8</span><span class="sxs-lookup"><span data-stu-id="166f6-161">0x8</span></span> | <span data-ttu-id="166f6-162">Návratový pouze názvy vlastností, které jsou odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="166f6-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="166f6-163">Příznaky skupiny 3</span><span class="sxs-lookup"><span data-stu-id="166f6-163">Group 3 flags</span></span> |<span data-ttu-id="166f6-164">Hodnota</span><span class="sxs-lookup"><span data-stu-id="166f6-164">Value</span></span>  |<span data-ttu-id="166f6-165">Popis</span><span class="sxs-lookup"><span data-stu-id="166f6-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="166f6-166">0x10</span><span class="sxs-lookup"><span data-stu-id="166f6-166">0x10</span></span> | <span data-ttu-id="166f6-167">Vrátí pouze názvy vlastností, které patří do nejvíce odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="166f6-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="166f6-168">Vlastnosti vylučte z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="166f6-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="166f6-169">0x20</span><span class="sxs-lookup"><span data-stu-id="166f6-169">0x20</span></span> | <span data-ttu-id="166f6-170">Vrátí pouze názvy vlastností, které patří do nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="166f6-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="166f6-171">0x30</span><span class="sxs-lookup"><span data-stu-id="166f6-171">0x30</span></span> | <span data-ttu-id="166f6-172">Vrátí pouze názvy vlastností systému.</span><span class="sxs-lookup"><span data-stu-id="166f6-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="166f6-173">0x40</span><span class="sxs-lookup"><span data-stu-id="166f6-173">0x40</span></span> | <span data-ttu-id="166f6-174">Vrátí pouze názvy nesystémové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="166f6-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="166f6-175">Funkce vždy přiděluje nový `SAFEARRAY` vrátí-li `WBEM_S_NO_ERROR`, a `pstrNames` je vždycky nastavený tak, aby odkazoval na ni.</span><span class="sxs-lookup"><span data-stu-id="166f6-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="166f6-176">Pole vrácené může mít elementy 0, pokud žádné vlastnosti, které odpovídají zadané filtry.</span><span class="sxs-lookup"><span data-stu-id="166f6-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="166f6-177">Pokud funkce vrátí hodnotu než `WBM_S_NO_ERROR`, nový `SAFEARRAY` struktura nevrátí.</span><span class="sxs-lookup"><span data-stu-id="166f6-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="166f6-178">Požadavky</span><span class="sxs-lookup"><span data-stu-id="166f6-178">Requirements</span></span>  
 <span data-ttu-id="166f6-179">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="166f6-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="166f6-180">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="166f6-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="166f6-181">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="166f6-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166f6-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="166f6-182">See also</span></span>  
[<span data-ttu-id="166f6-183">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="166f6-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
