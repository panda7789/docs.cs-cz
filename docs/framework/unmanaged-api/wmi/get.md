---
title: Get – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce Get načte hodnotu zadané vlastnosti.
ms.date: 11/06/2017
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
ms.openlocfilehash: cb7475623961fe2ee5fc821c5f237f0a2acfae1a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507659"
---
# <a name="get-function"></a><span data-ttu-id="8b8c6-103">Get – funkce</span><span class="sxs-lookup"><span data-stu-id="8b8c6-103">Get function</span></span>
<span data-ttu-id="8b8c6-104">Načte hodnotu zadané vlastnosti, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8b8c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b8c6-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="8b8c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b8c6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8b8c6-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8b8c6-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="8b8c6-109">[in] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-109">[in] The name of the property.</span></span>

<span data-ttu-id="8b8c6-110">`lFlags` [in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="8b8c6-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-111">This parameter must be 0.</span></span>

<span data-ttu-id="8b8c6-112">`pVal` [out] Pokud funkce vrátí úspěšně, obsahuje hodnotu `wszName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="8b8c6-113">`pval` Argument je přiřazena správný typ a hodnota pro kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="8b8c6-114">`pvtType` [out] Pokud funkce vrátí úspěšně, obsahuje [konstantní typ modelu CIM](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) , který určuje typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="8b8c6-115">Jeho hodnota může být také `null`.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="8b8c6-116">`plFlavor` [out] Pokud funkce vrátí úspěšně, obdrží informace o původu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="8b8c6-117">Jeho hodnota může být `null`, nebo jednu z následujících konstant WBEM_FLAVOR_TYPE definované v *WbemCli.h* hlavičkový soubor:</span><span class="sxs-lookup"><span data-stu-id="8b8c6-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="8b8c6-118">Konstanta</span><span class="sxs-lookup"><span data-stu-id="8b8c6-118">Constant</span></span>  |<span data-ttu-id="8b8c6-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8b8c6-119">Value</span></span>  |<span data-ttu-id="8b8c6-120">Popis</span><span class="sxs-lookup"><span data-stu-id="8b8c6-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="8b8c6-121">0x40</span><span class="sxs-lookup"><span data-stu-id="8b8c6-121">0x40</span></span> | <span data-ttu-id="8b8c6-122">Vlastnost je standardní systém vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="8b8c6-123">0x20</span><span class="sxs-lookup"><span data-stu-id="8b8c6-123">0x20</span></span> | <span data-ttu-id="8b8c6-124">Pro třídu: vlastnost je zděděná z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="8b8c6-125">Pro instanci: vlastnost, zatímco zděděná z nadřazené třídy nebyl změněn instancí.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="8b8c6-126">0</span><span class="sxs-lookup"><span data-stu-id="8b8c6-126">0</span></span> | <span data-ttu-id="8b8c6-127">Pro třídu: vlastnost patří k odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="8b8c6-128">Instance: instance; je změněna vlastnost To znamená, že byla zadána hodnota nebo kvalifikátor byla přidána nebo upravena.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="8b8c6-129">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8b8c6-129">Return value</span></span>

<span data-ttu-id="8b8c6-130">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="8b8c6-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8b8c6-131">Konstanta</span><span class="sxs-lookup"><span data-stu-id="8b8c6-131">Constant</span></span>  |<span data-ttu-id="8b8c6-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8b8c6-132">Value</span></span>  |<span data-ttu-id="8b8c6-133">Popis</span><span class="sxs-lookup"><span data-stu-id="8b8c6-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8b8c6-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8b8c6-134">0x80041001</span></span> | <span data-ttu-id="8b8c6-135">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8b8c6-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8b8c6-136">0x80041008</span></span> | <span data-ttu-id="8b8c6-137">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="8b8c6-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="8b8c6-138">0x80041002</span></span> | <span data-ttu-id="8b8c6-139">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8b8c6-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8b8c6-140">0x80041006</span></span> | <span data-ttu-id="8b8c6-141">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8b8c6-142">0</span><span class="sxs-lookup"><span data-stu-id="8b8c6-142">0</span></span> | <span data-ttu-id="8b8c6-143">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8b8c6-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b8c6-144">Remarks</span></span>

<span data-ttu-id="8b8c6-145">Tato funkce zalamuje volání na [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) metody.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="8b8c6-146">`Get` Funkce může vrátit také vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="8b8c6-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="8b8c6-147">`pVal` Argument je přiřazena správný typ a hodnota pro kvalifikátor a modelu COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) – funkce</span><span class="sxs-lookup"><span data-stu-id="8b8c6-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="8b8c6-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b8c6-148">Requirements</span></span>  
 <span data-ttu-id="8b8c6-149">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b8c6-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b8c6-150">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8b8c6-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8b8c6-151">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8b8c6-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8c6-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b8c6-152">See also</span></span>  
[<span data-ttu-id="8b8c6-153">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="8b8c6-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
