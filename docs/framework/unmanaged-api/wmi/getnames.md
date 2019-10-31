---
title: GetNames – funkce (odkaz na nespravované rozhraní API)
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
ms.openlocfilehash: 5b03ed6a68fbe288e93dedb4f425f1511563dfeb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102527"
---
# <a name="getnames-function"></a><span data-ttu-id="ff46b-103">Funkce GetNames</span><span class="sxs-lookup"><span data-stu-id="ff46b-103">GetNames function</span></span>
<span data-ttu-id="ff46b-104">Načte buď podmnožinu, nebo všechny názvy vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="ff46b-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="ff46b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff46b-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="ff46b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff46b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ff46b-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ff46b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ff46b-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="ff46b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="ff46b-109">pro Ukazatel na platný `LPCWSTR`, který určuje název kvalifikátoru, který funguje jako součást filtru.</span><span class="sxs-lookup"><span data-stu-id="ff46b-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="ff46b-110">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff46b-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="ff46b-111">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="ff46b-112">pro Kombinace bitových polí.</span><span class="sxs-lookup"><span data-stu-id="ff46b-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="ff46b-113">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff46b-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="ff46b-114">pro Ukazatel na platnou strukturu `VARIANT` inicializovaný jako hodnota filtru.</span><span class="sxs-lookup"><span data-stu-id="ff46b-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="ff46b-115">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="ff46b-116">mimo Struktura `SAFEARRAY`, která obsahuje názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="ff46b-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="ff46b-117">U vstupu musí být tento parametr vždy ukazatelem na `null`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="ff46b-118">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff46b-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="ff46b-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff46b-119">Return value</span></span>

<span data-ttu-id="ff46b-120">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ff46b-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ff46b-121">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ff46b-121">Constant</span></span>  |<span data-ttu-id="ff46b-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ff46b-122">Value</span></span>  |<span data-ttu-id="ff46b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ff46b-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="ff46b-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ff46b-124">0x80041001</span></span> | <span data-ttu-id="ff46b-125">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="ff46b-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ff46b-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ff46b-126">0x80041008</span></span> | <span data-ttu-id="ff46b-127">Jeden nebo více parametrů je neplatných nebo byla zadána nesprávná kombinace příznaků a parametrů.</span><span class="sxs-lookup"><span data-stu-id="ff46b-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ff46b-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ff46b-128">0x80041006</span></span> | <span data-ttu-id="ff46b-129">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="ff46b-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ff46b-130">0,8</span><span class="sxs-lookup"><span data-stu-id="ff46b-130">0</span></span> | <span data-ttu-id="ff46b-131">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ff46b-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ff46b-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff46b-132">Remarks</span></span>

<span data-ttu-id="ff46b-133">Tato funkce zalomí volání metody [IWbemclassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .</span><span class="sxs-lookup"><span data-stu-id="ff46b-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="ff46b-134">Pojmenované vrácené jsou ovládány kombinací příznaků a parametrů.</span><span class="sxs-lookup"><span data-stu-id="ff46b-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="ff46b-135">Funkce například může vracet názvy všech vlastností nebo pouze názvy vlastností klíče.</span><span class="sxs-lookup"><span data-stu-id="ff46b-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="ff46b-136">Primární filtr je uveden v parametru `lFlags` a ostatní parametry se liší v závislosti na tom.</span><span class="sxs-lookup"><span data-stu-id="ff46b-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="ff46b-137">Hodnoty příznaku v `lFlags` jsou bitová pole.</span><span class="sxs-lookup"><span data-stu-id="ff46b-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="ff46b-138">Příznaky, které mohou být předány jako argument `lEnumFlags`, jsou bitová pole, která jsou definována v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.</span><span class="sxs-lookup"><span data-stu-id="ff46b-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="ff46b-139">Můžete zkombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="ff46b-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="ff46b-140">Příznaky ze stejné skupiny se však vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="ff46b-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="ff46b-141">Příznaky skupiny 1</span><span class="sxs-lookup"><span data-stu-id="ff46b-141">Group 1 flags</span></span> |<span data-ttu-id="ff46b-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ff46b-142">Value</span></span>  |<span data-ttu-id="ff46b-143">Popis</span><span class="sxs-lookup"><span data-stu-id="ff46b-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="ff46b-144">0,8</span><span class="sxs-lookup"><span data-stu-id="ff46b-144">0</span></span> | <span data-ttu-id="ff46b-145">Vrátí všechny názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="ff46b-145">Return all property names.</span></span> <span data-ttu-id="ff46b-146">`strQualifierName` a `pQualifierVal` se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ff46b-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="ff46b-147">první</span><span class="sxs-lookup"><span data-stu-id="ff46b-147">1</span></span> | <span data-ttu-id="ff46b-148">Vrátí pouze vlastnosti, které mají kvalifikátor názvu určený parametrem `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="ff46b-149">Pokud je tento příznak použit, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="ff46b-150">odst</span><span class="sxs-lookup"><span data-stu-id="ff46b-150">2</span></span> |  <span data-ttu-id="ff46b-151">Vrátí pouze vlastnosti, které nemají kvalifikátor názvu určeného parametrem `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="ff46b-152">Pokud je tento příznak použit, je nutné zadat `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="ff46b-153">3</span><span class="sxs-lookup"><span data-stu-id="ff46b-153">3</span></span> | <span data-ttu-id="ff46b-154">Vrátí pouze vlastnosti, které mají kvalifikátor názvu zadaný parametrem `wszQualifierName` a mají také hodnotu shodnou s hodnotou určenou strukturou `pQualifierVal`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="ff46b-155">Pokud je tento příznak použit, je nutné zadat `wszQualifierName` i `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="ff46b-156">Příznaky skupiny 2</span><span class="sxs-lookup"><span data-stu-id="ff46b-156">Group 2 flags</span></span> |<span data-ttu-id="ff46b-157">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ff46b-157">Value</span></span>  |<span data-ttu-id="ff46b-158">Popis</span><span class="sxs-lookup"><span data-stu-id="ff46b-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="ff46b-159">0x4</span><span class="sxs-lookup"><span data-stu-id="ff46b-159">0x4</span></span> | <span data-ttu-id="ff46b-160">Vrátí pouze názvy vlastností, které definují klíče.</span><span class="sxs-lookup"><span data-stu-id="ff46b-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="ff46b-161">0x8</span><span class="sxs-lookup"><span data-stu-id="ff46b-161">0x8</span></span> | <span data-ttu-id="ff46b-162">Vrátí pouze názvy vlastností, které jsou odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="ff46b-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="ff46b-163">Příznaky skupiny 3</span><span class="sxs-lookup"><span data-stu-id="ff46b-163">Group 3 flags</span></span> |<span data-ttu-id="ff46b-164">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ff46b-164">Value</span></span>  |<span data-ttu-id="ff46b-165">Popis</span><span class="sxs-lookup"><span data-stu-id="ff46b-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="ff46b-166">0x10</span><span class="sxs-lookup"><span data-stu-id="ff46b-166">0x10</span></span> | <span data-ttu-id="ff46b-167">Vrátí pouze názvy vlastností, které patří do nejvyšší odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ff46b-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="ff46b-168">Vylučte vlastnosti z nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="ff46b-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="ff46b-169">0x20</span><span class="sxs-lookup"><span data-stu-id="ff46b-169">0x20</span></span> | <span data-ttu-id="ff46b-170">Vrátí pouze názvy vlastností, které patří do nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="ff46b-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="ff46b-171">0x30</span><span class="sxs-lookup"><span data-stu-id="ff46b-171">0x30</span></span> | <span data-ttu-id="ff46b-172">Vrátí pouze názvy systémových vlastností.</span><span class="sxs-lookup"><span data-stu-id="ff46b-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="ff46b-173">0x40</span><span class="sxs-lookup"><span data-stu-id="ff46b-173">0x40</span></span> | <span data-ttu-id="ff46b-174">Vrátí pouze názvy nesystémových vlastností.</span><span class="sxs-lookup"><span data-stu-id="ff46b-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="ff46b-175">Funkce vždy přidělí nový `SAFEARRAY`, pokud vrátí `WBEM_S_NO_ERROR`a `pstrNames` je vždy nastaven na odkaz.</span><span class="sxs-lookup"><span data-stu-id="ff46b-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="ff46b-176">Vrácené pole může mít 0 prvků, pokud žádné vlastnosti neodpovídají zadaným filtrům.</span><span class="sxs-lookup"><span data-stu-id="ff46b-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="ff46b-177">Vrátí-li funkce jinou hodnotu než `WBM_S_NO_ERROR`, nevrátí se nová struktura `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="ff46b-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="ff46b-178">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff46b-178">Requirements</span></span>  
 <span data-ttu-id="ff46b-179">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff46b-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff46b-180">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ff46b-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ff46b-181">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ff46b-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff46b-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff46b-182">See also</span></span>

- [<span data-ttu-id="ff46b-183">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ff46b-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
