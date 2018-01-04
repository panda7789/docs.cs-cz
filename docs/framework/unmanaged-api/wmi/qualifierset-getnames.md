---
title: "Funkce QualifierSet_GetNames (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_GetNames načte názvy kvalifikátory z na objekt nebo vlastnost."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_GetNames
helpviewer_keywords: QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6077b448c2644f68d12679cf208ee921c2af119a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="5ea7a-103">QualifierSet_GetNames – funkce</span><span class="sxs-lookup"><span data-stu-id="5ea7a-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="5ea7a-104">Načte názvy všech kvalifikátory nebo určitých kvalifikátory, které jsou k dispozici na aktuální objekt nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5ea7a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ea7a-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="5ea7a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ea7a-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="5ea7a-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="5ea7a-108">[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="5ea7a-109">[v] Jeden z následujících příznaků nebo hodnoty, které určuje jména, které chcete zahrnout do výčtu.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="5ea7a-110">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5ea7a-110">Constant</span></span>  |<span data-ttu-id="5ea7a-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5ea7a-111">Value</span></span>  |<span data-ttu-id="5ea7a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea7a-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="5ea7a-113">0</span><span class="sxs-lookup"><span data-stu-id="5ea7a-113">0</span></span> | <span data-ttu-id="5ea7a-114">Vrátí názvy všech kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="5ea7a-115">0x10</span><span class="sxs-lookup"><span data-stu-id="5ea7a-115">0x10</span></span> | <span data-ttu-id="5ea7a-116">Vraťte pouze názvy kvalifikátory specifické pro aktuální vlastnost nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="5ea7a-117">Pro vlastnost: vracet jenom kvalifikátory specifické pro vlastnost (včetně potlačení), a ne těchto kvalifikátory rozšíří z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="5ea7a-118">Pro instanci: vrátit pouze názvy kvalifikátor specifické pro instanci.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="5ea7a-119">Pro třídu: vracet jenom kvalifikátory specifické pro beiong třídy odvozené.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="5ea7a-120">0x20</span><span class="sxs-lookup"><span data-stu-id="5ea7a-120">0x20</span></span> | <span data-ttu-id="5ea7a-121">Vraťte se rozšíří pouze názvy kvalifikátory z jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="5ea7a-122">Pro vlastnost: vrátit se rozšíří pouze kvalifikátory k této vlastnosti z definice třídy a ne z samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="5ea7a-123">Pro instanci: vrátí jenom ty kvalifikátory rozšíří z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="5ea7a-124">Pro třídu: vrátit pouze názvy kvalifikátor zděděn od nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="5ea7a-125">`pstrNames`[out] Nový `SAFEARRAY` obsahující požadované názvy.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="5ea7a-126">Pole může obsahovat 0 elementy.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-126">The array can have 0 elements.</span></span> <span data-ttu-id="5ea7a-127">Pokud dojde k chybě, nový `SAFEARRAY` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ea7a-128">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5ea7a-128">Return value</span></span>

<span data-ttu-id="5ea7a-129">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="5ea7a-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5ea7a-130">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5ea7a-130">Constant</span></span>  |<span data-ttu-id="5ea7a-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5ea7a-131">Value</span></span>  |<span data-ttu-id="5ea7a-132">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea7a-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5ea7a-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5ea7a-133">0x80041008</span></span> | <span data-ttu-id="5ea7a-134">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5ea7a-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5ea7a-135">0x80041006</span></span> | <span data-ttu-id="5ea7a-136">Je k dispozici zahájíte nové – výčet není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5ea7a-137">0</span><span class="sxs-lookup"><span data-stu-id="5ea7a-137">0</span></span> | <span data-ttu-id="5ea7a-138">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5ea7a-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ea7a-139">Remarks</span></span>

<span data-ttu-id="5ea7a-140">Tato funkce zabalí volání [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-140">This function wraps a call to the [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5ea7a-141">Jakmile jste načíst názvy kvalifikátor, můžete přístup každý kvalifikátor podle názvu voláním [QualifierSet_Get](qualifierset-get.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="5ea7a-142">Není pro daný objekt má nulové kvalifikátory, takže chybu počet řetězců v `pstrNames` návratu z může být 0, i když funkce vrátí hodnotu `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="5ea7a-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ea7a-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ea7a-143">Requirements</span></span>  
 <span data-ttu-id="5ea7a-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ea7a-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ea7a-145">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5ea7a-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5ea7a-146">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ea7a-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea7a-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ea7a-147">See also</span></span>  
[<span data-ttu-id="5ea7a-148">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5ea7a-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
