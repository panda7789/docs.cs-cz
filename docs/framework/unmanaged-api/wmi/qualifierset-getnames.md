---
title: Funkce QualifierSet_GetNames (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_GetNames načte názvy kvalifikátory z objektu nebo vlastnosti.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84059c5e5542e13b1d4fc4efcfc4c7f418db391e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516276"
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="a8864-103">QualifierSet_GetNames – funkce</span><span class="sxs-lookup"><span data-stu-id="a8864-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="a8864-104">Načte názvy všech kvalifikátory nebo určitých kvalifikátorů, které jsou k dispozici z aktuální objekt nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a8864-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a8864-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8864-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="a8864-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8864-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="a8864-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a8864-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="a8864-108">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="a8864-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="a8864-109">[in] Jeden z následujících příznaků nebo hodnoty, které určuje názvy, které chcete zahrnout do výčtu.</span><span class="sxs-lookup"><span data-stu-id="a8864-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="a8864-110">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a8864-110">Constant</span></span>  |<span data-ttu-id="a8864-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8864-111">Value</span></span>  |<span data-ttu-id="a8864-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a8864-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="a8864-113">0</span><span class="sxs-lookup"><span data-stu-id="a8864-113">0</span></span> | <span data-ttu-id="a8864-114">Vrátí názvy všech kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="a8864-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a8864-115">0x10</span><span class="sxs-lookup"><span data-stu-id="a8864-115">0x10</span></span> | <span data-ttu-id="a8864-116">Vrátíte pouze názvy kvalifikátory konkrétní aktuální vlastnost nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="a8864-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="a8864-117">Pro vlastnost: vracet jenom v kvalifikátorech specifické pro vlastnost (včetně potlačení), a ne těchto kvalifikátory rozšířena z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="a8864-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="a8864-118">Pro instanci: vrátit pouze názvy instancí kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="a8864-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="a8864-119">Pro třídu: vracet jenom kvalifikátory jsou specifické pro beiong třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="a8864-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="a8864-120">0x20</span><span class="sxs-lookup"><span data-stu-id="a8864-120">0x20</span></span> | <span data-ttu-id="a8864-121">Vrátit pouze názvy kvalifikátory rozšířena z jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="a8864-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="a8864-122">Pro vlastnost: vrátit jenom v kvalifikátorech rozšíří na tuto vlastnost z definice třídy a ne ty ze samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a8864-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="a8864-123">Pro instanci: vrátit pouze ty kvalifikátory rozšířena z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="a8864-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="a8864-124">Pro třídu: vrátit pouze názvy kvalifikátor zděděná z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="a8864-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="a8864-125">`pstrNames` [out] Nový `SAFEARRAY` , který obsahuje požadované názvy.</span><span class="sxs-lookup"><span data-stu-id="a8864-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="a8864-126">Pole může mít 0 prvků.</span><span class="sxs-lookup"><span data-stu-id="a8864-126">The array can have 0 elements.</span></span> <span data-ttu-id="a8864-127">Pokud dojde k chybě, nový `SAFEARRAY` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="a8864-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="a8864-128">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8864-128">Return value</span></span>

<span data-ttu-id="a8864-129">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="a8864-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a8864-130">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a8864-130">Constant</span></span>  |<span data-ttu-id="a8864-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8864-131">Value</span></span>  |<span data-ttu-id="a8864-132">Popis</span><span class="sxs-lookup"><span data-stu-id="a8864-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a8864-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a8864-133">0x80041008</span></span> | <span data-ttu-id="a8864-134">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="a8864-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a8864-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a8864-135">0x80041006</span></span> | <span data-ttu-id="a8864-136">Nedostatek paměti je k dispozici zahájíte nový výčet.</span><span class="sxs-lookup"><span data-stu-id="a8864-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a8864-137">0</span><span class="sxs-lookup"><span data-stu-id="a8864-137">0</span></span> | <span data-ttu-id="a8864-138">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a8864-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a8864-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8864-139">Remarks</span></span>

<span data-ttu-id="a8864-140">Tato funkce zalamuje volání na [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) metody.</span><span class="sxs-lookup"><span data-stu-id="a8864-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="a8864-141">Až jsme načíst názvy kvalifikátor, voláním dostanete každý kvalifikátor podle názvu [QualifierSet_Get](qualifierset-get.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="a8864-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="a8864-142">Není chybu pro daný objekt má nulovou kvalifikátory tak počet řetězců v `pstrNames` návratu může být 0, i když funkce vrátí `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="a8864-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8864-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8864-143">Requirements</span></span>  
 <span data-ttu-id="a8864-144">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8864-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8864-145">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a8864-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a8864-146">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a8864-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8864-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8864-147">See also</span></span>  
[<span data-ttu-id="a8864-148">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a8864-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
