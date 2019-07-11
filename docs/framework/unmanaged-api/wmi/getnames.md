---
title: Funkce GetNames (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetNames načte názvy vlastností objektu.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e75bf9aab820216373f2f33fe8aa567f10befcb1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746515"
---
# <a name="getnames-function"></a><span data-ttu-id="e9ffc-103">Funkce GetNames</span><span class="sxs-lookup"><span data-stu-id="e9ffc-103">GetNames function</span></span>
<span data-ttu-id="e9ffc-104">Načte podmnožinu nebo všechny názvy vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e9ffc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9ffc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="e9ffc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9ffc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e9ffc-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e9ffc-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="e9ffc-109">[in] Ukazatel na platný `LPCWSTR` , který určuje název kvalifikátor, který funguje jako součást filtr.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="e9ffc-110">Další informace najdete v tématu [poznámky](#remarks) oddílu.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="e9ffc-111">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="e9ffc-112">[in] Kombinací bitových polí.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="e9ffc-113">Další informace najdete v tématu [poznámky](#remarks) oddílu.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="e9ffc-114">[in] Ukazatel na platný `VARIANT` struktura inicializovány na hodnotu filtru.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="e9ffc-115">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="e9ffc-116">[out] A `SAFEARRAY` strukturu, která obsahuje názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="e9ffc-117">V položce, musí mít tento parametr vždy ukazatel na `null`.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="e9ffc-118">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e9ffc-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9ffc-119">Return value</span></span>

<span data-ttu-id="e9ffc-120">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e9ffc-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e9ffc-121">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e9ffc-121">Constant</span></span>  |<span data-ttu-id="e9ffc-122">Value</span><span class="sxs-lookup"><span data-stu-id="e9ffc-122">Value</span></span>  |<span data-ttu-id="e9ffc-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e9ffc-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e9ffc-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e9ffc-124">0x80041001</span></span> | <span data-ttu-id="e9ffc-125">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e9ffc-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e9ffc-126">0x80041008</span></span> | <span data-ttu-id="e9ffc-127">Jeden nebo více parametrů nejsou platné, nebo byl zadán nesprávný kombinace příznaků a parametry.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e9ffc-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e9ffc-128">0x80041006</span></span> | <span data-ttu-id="e9ffc-129">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e9ffc-130">0</span><span class="sxs-lookup"><span data-stu-id="e9ffc-130">0</span></span> | <span data-ttu-id="e9ffc-131">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e9ffc-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9ffc-132">Remarks</span></span>

<span data-ttu-id="e9ffc-133">Tato funkce zalamuje volání na [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) metody.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="e9ffc-134">Pojmenované vrátil řízeno pomocí kombinace příznaků a parametry.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="e9ffc-135">Funkce může vrátit třeba názvy všech vlastností nebo pouze názvy vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="e9ffc-136">Primární filtru je zadán v `lFlags` parametru a dalších parametrů se liší v závislosti na jeho.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="e9ffc-137">Příznak hodnoty v `lFlags` jsou bitová pole</span><span class="sxs-lookup"><span data-stu-id="e9ffc-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="e9ffc-138">Příznaky, které mohou být předány jako `lEnumFlags` argument jsou bitová pole, které jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="e9ffc-139">Můžete kombinovat jeden příznak z každé skupiny s všechny příznaky z jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="e9ffc-140">Ale příznaky ze stejné skupiny se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="e9ffc-141">Příznaky skupiny 1</span><span class="sxs-lookup"><span data-stu-id="e9ffc-141">Group 1 flags</span></span> |<span data-ttu-id="e9ffc-142">Value</span><span class="sxs-lookup"><span data-stu-id="e9ffc-142">Value</span></span>  |<span data-ttu-id="e9ffc-143">Popis</span><span class="sxs-lookup"><span data-stu-id="e9ffc-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="e9ffc-144">0</span><span class="sxs-lookup"><span data-stu-id="e9ffc-144">0</span></span> | <span data-ttu-id="e9ffc-145">Vrátí všechny názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-145">Return all property names.</span></span> <span data-ttu-id="e9ffc-146">`strQualifierName` a `pQualifierVal` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="e9ffc-147">1</span><span class="sxs-lookup"><span data-stu-id="e9ffc-147">1</span></span> | <span data-ttu-id="e9ffc-148">Vrátit pouze vlastnosti, které mají kvalifikátoru název určený `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e9ffc-149">Pokud tento příznak se používá, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="e9ffc-150">2</span><span class="sxs-lookup"><span data-stu-id="e9ffc-150">2</span></span> |  <span data-ttu-id="e9ffc-151">Vrátit pouze vlastnosti, které nemají kvalifikátoru název určený `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e9ffc-152">Pokud tento příznak se používá, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="e9ffc-153">3</span><span class="sxs-lookup"><span data-stu-id="e9ffc-153">3</span></span> | <span data-ttu-id="e9ffc-154">Vrátit pouze vlastnosti, které mají kvalifikátoru název určený `wszQualifierName` parametr a také mít identické s klíči určenému hodnotu `pQualifierVal` struktury.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="e9ffc-155">Pokud tento příznak se používá, je nutné zadat obě `wszQualifierName` a `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="e9ffc-156">Příznaky skupiny 2</span><span class="sxs-lookup"><span data-stu-id="e9ffc-156">Group 2 flags</span></span> |<span data-ttu-id="e9ffc-157">Value</span><span class="sxs-lookup"><span data-stu-id="e9ffc-157">Value</span></span>  |<span data-ttu-id="e9ffc-158">Popis</span><span class="sxs-lookup"><span data-stu-id="e9ffc-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="e9ffc-159">0x4</span><span class="sxs-lookup"><span data-stu-id="e9ffc-159">0x4</span></span> | <span data-ttu-id="e9ffc-160">Vrátíte pouze názvy vlastností, které definují klíče.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="e9ffc-161">0x8</span><span class="sxs-lookup"><span data-stu-id="e9ffc-161">0x8</span></span> | <span data-ttu-id="e9ffc-162">Vrácení pouze názvy vlastností, které jsou odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="e9ffc-163">Příznaky skupiny 3</span><span class="sxs-lookup"><span data-stu-id="e9ffc-163">Group 3 flags</span></span> |<span data-ttu-id="e9ffc-164">Value</span><span class="sxs-lookup"><span data-stu-id="e9ffc-164">Value</span></span>  |<span data-ttu-id="e9ffc-165">Popis</span><span class="sxs-lookup"><span data-stu-id="e9ffc-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="e9ffc-166">0x10</span><span class="sxs-lookup"><span data-stu-id="e9ffc-166">0x10</span></span> | <span data-ttu-id="e9ffc-167">Vrátíte pouze názvy vlastností, které patří k nejvíce odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="e9ffc-168">Vyloučíte vlastnosti od nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="e9ffc-169">0x20</span><span class="sxs-lookup"><span data-stu-id="e9ffc-169">0x20</span></span> | <span data-ttu-id="e9ffc-170">Vrátíte pouze názvy vlastností, které patří do nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="e9ffc-171">0x30</span><span class="sxs-lookup"><span data-stu-id="e9ffc-171">0x30</span></span> | <span data-ttu-id="e9ffc-172">Vrátíte pouze názvy vlastností systému.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="e9ffc-173">0x40</span><span class="sxs-lookup"><span data-stu-id="e9ffc-173">0x40</span></span> | <span data-ttu-id="e9ffc-174">Vrátíte pouze názvy vlastností nesystémové.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="e9ffc-175">Funkce vždy přidělí novou `SAFEARRAY` vrátí-li `WBEM_S_NO_ERROR`, a `pstrNames` je vždycky nastavený tak, aby odkazoval na ni.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="e9ffc-176">Vrácené pole může obsahovat 0 elementy, pokud určenému filtru neodpovídají žádné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="e9ffc-177">Pokud funkce vrátí hodnotu jiné než `WBM_S_NO_ERROR`, nový `SAFEARRAY` struktura nevrátí.</span><span class="sxs-lookup"><span data-stu-id="e9ffc-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="e9ffc-178">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9ffc-178">Requirements</span></span>  
 <span data-ttu-id="e9ffc-179">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9ffc-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9ffc-180">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e9ffc-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e9ffc-181">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e9ffc-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ffc-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9ffc-182">See also</span></span>

- [<span data-ttu-id="e9ffc-183">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e9ffc-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
