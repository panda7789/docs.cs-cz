---
title: "Get – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce Get načte zadanou hodnotu vlastnosti."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69312030689ab1b87e3aadd040395f06e1c94ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="get-function"></a><span data-ttu-id="4c660-103">Get – funkce</span><span class="sxs-lookup"><span data-stu-id="4c660-103">Get function</span></span>
<span data-ttu-id="4c660-104">Pokud existuje, načte zadanou hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4c660-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4c660-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c660-105">Syntax</span></span>  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="4c660-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c660-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4c660-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="4c660-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4c660-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="4c660-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="4c660-109">[v] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4c660-109">[in] The name of the property.</span></span>

<span data-ttu-id="4c660-110">`lFlags`[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="4c660-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="4c660-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="4c660-111">This parameter must be 0.</span></span>

<span data-ttu-id="4c660-112">`pVal`[out] Pokud funkce vrátí úspěšně, obsahuje hodnotu `wszName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4c660-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="4c660-113">`pval` Argument je přiřazen správný typ a hodnotu pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="4c660-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="4c660-114">`pvtType`[out] Pokud funkce vrátí úspěšně, obsahuje [typ modelu CIM konstanta](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) určující typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4c660-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) that indicates the property type.</span></span> <span data-ttu-id="4c660-115">Jeho hodnota může být také `null`.</span><span class="sxs-lookup"><span data-stu-id="4c660-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="4c660-116">`plFlavor`[out] Pokud funkce vrátí úspěšně, obdrží informace o zdroji vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4c660-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="4c660-117">Jeho hodnota může být `null`, nebo jeden z následujících WBEM_FLAVOR_TYPE konstanty definované v *WbemCli.h* hlavičkový soubor:</span><span class="sxs-lookup"><span data-stu-id="4c660-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="4c660-118">Konstanta</span><span class="sxs-lookup"><span data-stu-id="4c660-118">Constant</span></span>  |<span data-ttu-id="4c660-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4c660-119">Value</span></span>  |<span data-ttu-id="4c660-120">Popis</span><span class="sxs-lookup"><span data-stu-id="4c660-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="4c660-121">0x40</span><span class="sxs-lookup"><span data-stu-id="4c660-121">0x40</span></span> | <span data-ttu-id="4c660-122">Vlastnost je standardní systém vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4c660-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="4c660-123">0x20</span><span class="sxs-lookup"><span data-stu-id="4c660-123">0x20</span></span> | <span data-ttu-id="4c660-124">Pro třídu: vlastnost je zděděna od nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="4c660-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="4c660-125">Pro instanci: vlastnost, zatímco zděděn od nadřazené třídy, se nezměnil instance.</span><span class="sxs-lookup"><span data-stu-id="4c660-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="4c660-126">0</span><span class="sxs-lookup"><span data-stu-id="4c660-126">0</span></span> | <span data-ttu-id="4c660-127">Pro třídu: vlastnost náleží do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4c660-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="4c660-128">Pro instanci: vlastnost je upravovat instance; To znamená, že byla zadána hodnota, nebo kvalifikátor byla přidána nebo upravena.</span><span class="sxs-lookup"><span data-stu-id="4c660-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="4c660-129">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4c660-129">Return value</span></span>

<span data-ttu-id="4c660-130">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="4c660-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4c660-131">Konstanta</span><span class="sxs-lookup"><span data-stu-id="4c660-131">Constant</span></span>  |<span data-ttu-id="4c660-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4c660-132">Value</span></span>  |<span data-ttu-id="4c660-133">Popis</span><span class="sxs-lookup"><span data-stu-id="4c660-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="4c660-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4c660-134">0x80041001</span></span> | <span data-ttu-id="4c660-135">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="4c660-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4c660-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4c660-136">0x80041008</span></span> | <span data-ttu-id="4c660-137">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="4c660-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4c660-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4c660-138">0x80041002</span></span> | <span data-ttu-id="4c660-139">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="4c660-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4c660-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4c660-140">0x80041006</span></span> | <span data-ttu-id="4c660-141">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="4c660-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4c660-142">0</span><span class="sxs-lookup"><span data-stu-id="4c660-142">0</span></span> | <span data-ttu-id="4c660-143">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4c660-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4c660-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c660-144">Remarks</span></span>

<span data-ttu-id="4c660-145">Tato funkce zabalí volání [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="4c660-145">This function wraps a call to the [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4c660-146">`Get` Funkce mohou vracet vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="4c660-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="4c660-147">`pVal` Argument je přiřazen správný typ a hodnotu pro kvalifikátor a knihovny COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) – funkce</span><span class="sxs-lookup"><span data-stu-id="4c660-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) function</span></span>

## <a name="requirements"></a><span data-ttu-id="4c660-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c660-148">Requirements</span></span>  
 <span data-ttu-id="4c660-149">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c660-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c660-150">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4c660-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4c660-151">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c660-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c660-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c660-152">See also</span></span>  
[<span data-ttu-id="4c660-153">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="4c660-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
