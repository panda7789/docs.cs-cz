---
title: Funkce GetPropertyQualifierSet (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetPropertyQualifierSet načte kvalifikátor pro vlastnost nastavit.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec91a1f6fba70e3c9706541dc641ddd019d44841
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642201"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="eb127-103">GetPropertyQualifierSet – funkce</span><span class="sxs-lookup"><span data-stu-id="eb127-103">GetPropertyQualifierSet function</span></span>
<span data-ttu-id="eb127-104">Načte kvalifikátor nastavit určité vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eb127-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="eb127-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb127-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="eb127-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb127-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="eb127-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="eb127-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="eb127-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="eb127-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`  
<span data-ttu-id="eb127-109">[in] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eb127-109">[in] The property  name.</span></span> <span data-ttu-id="eb127-110">`wszProperty` musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="eb127-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="eb127-111">[out] Přijímá ukazatel rozhraní, která umožňuje přístup k kvalifikátory vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eb127-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="eb127-112">`ppQualSet` nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="eb127-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="eb127-113">Pokud dojde k chybě, není vrátí nový objekt a ukazatel je nastaven tak, aby odkazoval na `null`.</span><span class="sxs-lookup"><span data-stu-id="eb127-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="eb127-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eb127-114">Return value</span></span>

<span data-ttu-id="eb127-115">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="eb127-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="eb127-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="eb127-116">Constant</span></span>  |<span data-ttu-id="eb127-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="eb127-117">Value</span></span>  |<span data-ttu-id="eb127-118">Popis</span><span class="sxs-lookup"><span data-stu-id="eb127-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="eb127-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="eb127-119">0x80041001</span></span> | <span data-ttu-id="eb127-120">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="eb127-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="eb127-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="eb127-121">0x80041002</span></span> | <span data-ttu-id="eb127-122">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="eb127-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="eb127-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="eb127-123">0x80041006</span></span> | <span data-ttu-id="eb127-124">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="eb127-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="eb127-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="eb127-125">0x80041008</span></span> | <span data-ttu-id="eb127-126">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="eb127-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="eb127-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="eb127-127">0x80041030</span></span> | <span data-ttu-id="eb127-128">Funkce se pokusí získat kvalifikátory vlastnost systému.</span><span class="sxs-lookup"><span data-stu-id="eb127-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="eb127-129">0</span><span class="sxs-lookup"><span data-stu-id="eb127-129">0</span></span> | <span data-ttu-id="eb127-130">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="eb127-130">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="eb127-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb127-131">Remarks</span></span>

<span data-ttu-id="eb127-132">Tato funkce zalamuje volání na [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) metody.</span><span class="sxs-lookup"><span data-stu-id="eb127-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span> 

<span data-ttu-id="eb127-133">Voláním této funkce je podporována pouze v případě, že je aktuální objekt definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="eb127-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="eb127-134">Není k dispozici pro manipulaci s metoda [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters odkazující na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="eb127-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters that point to CIM instances.</span></span>

<span data-ttu-id="eb127-135">Protože každá metoda může mít svůj vlastní kvalifikátory [IWbemQualifierSet ukazatel](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="eb127-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="eb127-136">Vzhledem k tomu, že vlastnosti systému bez kvalifikátorů, funkce vrátí `WBEM_E_SYSTEM_PROPERTY` při pokusu o získání [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) ukazatel pro vlastnost systému.</span><span class="sxs-lookup"><span data-stu-id="eb127-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb127-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb127-137">Requirements</span></span>  
<span data-ttu-id="eb127-138">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb127-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb127-139">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="eb127-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="eb127-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eb127-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb127-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb127-141">See also</span></span>
- [<span data-ttu-id="eb127-142">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="eb127-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
