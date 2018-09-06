---
title: Funkce GetMethodQualifierSet (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetMethodQualifierSet načte sadu metod kvalifikátoru.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a363591f5db7a2dbcba1147df35d8c023c9b0707
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800125"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="8577c-103">Funkce GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="8577c-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="8577c-104">Načte kvalifikátor nastavit pro konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="8577c-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8577c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8577c-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="8577c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8577c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8577c-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="8577c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8577c-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="8577c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`  
<span data-ttu-id="8577c-109">[in] Název metody.</span><span class="sxs-lookup"><span data-stu-id="8577c-109">[in] The method  name.</span></span> <span data-ttu-id="8577c-110">`wszMethod` musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="8577c-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="8577c-111">[out] Přijímá ukazatel rozhraní, která umožňuje přístup k kvalifikátory metody.</span><span class="sxs-lookup"><span data-stu-id="8577c-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="8577c-112">`ppQualSet` nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="8577c-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="8577c-113">Pokud dojde k chybě, není vrátí nový objekt a ukazatel je nastaven tak, aby odkazoval na `null`.</span><span class="sxs-lookup"><span data-stu-id="8577c-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="8577c-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8577c-114">Return value</span></span>

<span data-ttu-id="8577c-115">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="8577c-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8577c-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="8577c-116">Constant</span></span>  |<span data-ttu-id="8577c-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8577c-117">Value</span></span>  |<span data-ttu-id="8577c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8577c-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="8577c-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="8577c-119">0x80041002</span></span> | <span data-ttu-id="8577c-120">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="8577c-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8577c-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8577c-121">0x80041008</span></span> | <span data-ttu-id="8577c-122">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="8577c-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8577c-123">0</span><span class="sxs-lookup"><span data-stu-id="8577c-123">0</span></span> | <span data-ttu-id="8577c-124">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8577c-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8577c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8577c-125">Remarks</span></span>

<span data-ttu-id="8577c-126">Tato funkce zalamuje volání na [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) metody.</span><span class="sxs-lookup"><span data-stu-id="8577c-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span> 

<span data-ttu-id="8577c-127">Voláním této funkce je podporována pouze v případě, že je aktuální objekt definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="8577c-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="8577c-128">Není k dispozici pro manipulaci s metoda [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters odkazující na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="8577c-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters that point to CIM instances.</span></span>

<span data-ttu-id="8577c-129">Protože každá metoda může mít svůj vlastní kvalifikátory [IWbemQualifierSet ukazatel](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="8577c-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="8577c-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8577c-130">Requirements</span></span>  
<span data-ttu-id="8577c-131">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8577c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8577c-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8577c-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8577c-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8577c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8577c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8577c-134">See also</span></span>  
[<span data-ttu-id="8577c-135">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="8577c-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
