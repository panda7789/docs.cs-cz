---
title: Funkce GetNames (Nespravovaný odkaz na rozhraní API)
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174950"
---
# <a name="getnames-function"></a><span data-ttu-id="5ad8f-103">Funkce GetNames</span><span class="sxs-lookup"><span data-stu-id="5ad8f-103">GetNames function</span></span>
<span data-ttu-id="5ad8f-104">Načte podmnožinu nebo všechny názvy vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5ad8f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ad8f-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="5ad8f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ad8f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5ad8f-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5ad8f-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="5ad8f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="5ad8f-109">[v] Ukazatel na platný, `LPCWSTR` který určuje název kvalifikátoru, který funguje jako součást filtru.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="5ad8f-110">Další informace naleznete v části [Poznámky.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="5ad8f-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="5ad8f-111">Tento parametr `null`může být .</span><span class="sxs-lookup"><span data-stu-id="5ad8f-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="5ad8f-112">[v] Kombinace bitových polí.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="5ad8f-113">Další informace naleznete v části [Poznámky.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="5ad8f-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="5ad8f-114">`pQualifierValue`[v] Ukazatel na platnou `VARIANT` strukturu inicializovanou na hodnotu filtru.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="5ad8f-115">Tento parametr `null`může být .</span><span class="sxs-lookup"><span data-stu-id="5ad8f-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="5ad8f-116">[out] Struktura, `SAFEARRAY` která obsahuje názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="5ad8f-117">Při zadávání musí být tento parametr `null`vždy ukazatelem .</span><span class="sxs-lookup"><span data-stu-id="5ad8f-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="5ad8f-118">Další informace naleznete v části [Poznámky.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="5ad8f-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ad8f-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5ad8f-119">Return value</span></span>

<span data-ttu-id="5ad8f-120">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="5ad8f-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5ad8f-121">Trvalé</span><span class="sxs-lookup"><span data-stu-id="5ad8f-121">Constant</span></span>  |<span data-ttu-id="5ad8f-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5ad8f-122">Value</span></span>  |<span data-ttu-id="5ad8f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5ad8f-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="5ad8f-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5ad8f-124">0x80041001</span></span> | <span data-ttu-id="5ad8f-125">Došlo k obecnému selhání.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5ad8f-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5ad8f-126">0x80041008</span></span> | <span data-ttu-id="5ad8f-127">Jeden nebo více parametrů není platné nebo byla zadána nesprávná kombinace příznaků a parametrů.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5ad8f-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5ad8f-128">0x80041006</span></span> | <span data-ttu-id="5ad8f-129">K dokončení operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5ad8f-130">0</span><span class="sxs-lookup"><span data-stu-id="5ad8f-130">0</span></span> | <span data-ttu-id="5ad8f-131">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5ad8f-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ad8f-132">Remarks</span></span>

<span data-ttu-id="5ad8f-133">Tato funkce zabalí volání metody [IWbemClassObject::GetNames.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)</span><span class="sxs-lookup"><span data-stu-id="5ad8f-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="5ad8f-134">Pojmenované vrácené jsou řízeny kombinací příznaků a parametrů.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="5ad8f-135">Funkce může například vrátit názvy všech vlastností nebo pouze názvy vlastností klíče.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="5ad8f-136">Primární filtr je určen `lFlags` v parametru a ostatní parametry se liší v závislosti na něm.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="5ad8f-137">Hodnoty příznaku `lFlags` v jsou bitová pole</span><span class="sxs-lookup"><span data-stu-id="5ad8f-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="5ad8f-138">Příznaky, které mohou být `lEnumFlags` předány jako argument jsou bitová pole, které jsou definovány v souboru hlavičky *WbemCli.h,* nebo je můžete definovat jako konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="5ad8f-139">Můžete kombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="5ad8f-140">Příznaky ze stejné skupiny se však vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="5ad8f-141">Příznaky skupiny 1</span><span class="sxs-lookup"><span data-stu-id="5ad8f-141">Group 1 flags</span></span> |<span data-ttu-id="5ad8f-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5ad8f-142">Value</span></span>  |<span data-ttu-id="5ad8f-143">Popis</span><span class="sxs-lookup"><span data-stu-id="5ad8f-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="5ad8f-144">0</span><span class="sxs-lookup"><span data-stu-id="5ad8f-144">0</span></span> | <span data-ttu-id="5ad8f-145">Vrátí všechny názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-145">Return all property names.</span></span> <span data-ttu-id="5ad8f-146">`strQualifierName`a `pQualifierVal` jsou nevyužity.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="5ad8f-147">1</span><span class="sxs-lookup"><span data-stu-id="5ad8f-147">1</span></span> | <span data-ttu-id="5ad8f-148">Vrátí pouze vlastnosti, které mají kvalifikátor názvu určeného parametrem. `strQualifierName`</span><span class="sxs-lookup"><span data-stu-id="5ad8f-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="5ad8f-149">Pokud je tento příznak použit, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="5ad8f-150">2</span><span class="sxs-lookup"><span data-stu-id="5ad8f-150">2</span></span> |  <span data-ttu-id="5ad8f-151">Vrátí pouze vlastnosti, které nemají kvalifikátor názvu určeného parametrem. `strQualifierName`</span><span class="sxs-lookup"><span data-stu-id="5ad8f-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="5ad8f-152">Pokud je tento příznak použit, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="5ad8f-153">3</span><span class="sxs-lookup"><span data-stu-id="5ad8f-153">3</span></span> | <span data-ttu-id="5ad8f-154">Vrátí pouze vlastnosti, které mají kvalifikátor názvu určeného `wszQualifierName` parametrem `pQualifierVal` a mají také hodnotu shodnou s hodnotou určenou strukturou.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="5ad8f-155">Pokud je tento příznak použit, `wszQualifierName` je `pQualifierValue`nutné zadat a a .</span><span class="sxs-lookup"><span data-stu-id="5ad8f-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="5ad8f-156">Příznaky skupiny 2</span><span class="sxs-lookup"><span data-stu-id="5ad8f-156">Group 2 flags</span></span> |<span data-ttu-id="5ad8f-157">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5ad8f-157">Value</span></span>  |<span data-ttu-id="5ad8f-158">Popis</span><span class="sxs-lookup"><span data-stu-id="5ad8f-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="5ad8f-159">0x4</span><span class="sxs-lookup"><span data-stu-id="5ad8f-159">0x4</span></span> | <span data-ttu-id="5ad8f-160">Vrátí pouze názvy vlastností, které definují klíče.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="5ad8f-161">0x8</span><span class="sxs-lookup"><span data-stu-id="5ad8f-161">0x8</span></span> | <span data-ttu-id="5ad8f-162">Vrátí pouze názvy vlastností, které jsou odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="5ad8f-163">Příznaky skupiny 3</span><span class="sxs-lookup"><span data-stu-id="5ad8f-163">Group 3 flags</span></span> |<span data-ttu-id="5ad8f-164">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5ad8f-164">Value</span></span>  |<span data-ttu-id="5ad8f-165">Popis</span><span class="sxs-lookup"><span data-stu-id="5ad8f-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="5ad8f-166">0x10</span><span class="sxs-lookup"><span data-stu-id="5ad8f-166">0x10</span></span> | <span data-ttu-id="5ad8f-167">Vrátí pouze názvy vlastností, které patří do nejvíce odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="5ad8f-168">Vyloučit vlastnosti z nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="5ad8f-169">0x20</span><span class="sxs-lookup"><span data-stu-id="5ad8f-169">0x20</span></span> | <span data-ttu-id="5ad8f-170">Vrátí pouze názvy vlastností, které patří do nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="5ad8f-171">0x30</span><span class="sxs-lookup"><span data-stu-id="5ad8f-171">0x30</span></span> | <span data-ttu-id="5ad8f-172">Vrátí pouze názvy vlastností systému.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="5ad8f-173">0x40</span><span class="sxs-lookup"><span data-stu-id="5ad8f-173">0x40</span></span> | <span data-ttu-id="5ad8f-174">Vrátí pouze názvy nesystémových vlastností.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="5ad8f-175">Funkce vždy přiděluje nový, `SAFEARRAY` pokud se vrátí `WBEM_S_NO_ERROR`a `pstrNames` je vždy nastavena na odkaz.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="5ad8f-176">Vrácené pole může mít 0 prvků, pokud žádné vlastnosti neodpovídají zadaným filtrům.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="5ad8f-177">Pokud funkce vrátí jinou `WBM_S_NO_ERROR`hodnotu `SAFEARRAY` než , není vrácena nová struktura.</span><span class="sxs-lookup"><span data-stu-id="5ad8f-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ad8f-178">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ad8f-178">Requirements</span></span>  
 <span data-ttu-id="5ad8f-179">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ad8f-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ad8f-180">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5ad8f-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5ad8f-181">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ad8f-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad8f-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ad8f-182">See also</span></span>

- [<span data-ttu-id="5ad8f-183">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5ad8f-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
