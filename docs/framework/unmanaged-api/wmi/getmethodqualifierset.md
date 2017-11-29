---
title: "Funkce GetMethodQualifierSet (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetMethodQualifierSet načte metoda kvalifikátor sady."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79a19d3bb40dd4d435bd7cf97eb0b4071020648e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="f29e4-103">GetMethodQualifierSet – funkce</span><span class="sxs-lookup"><span data-stu-id="f29e4-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="f29e4-104">Načte kvalifikátor nastavit pro konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="f29e4-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f29e4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f29e4-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="f29e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f29e4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f29e4-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f29e4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f29e4-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="f29e4-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="f29e4-109">[v] Název metody.</span><span class="sxs-lookup"><span data-stu-id="f29e4-109">[in] The method  name.</span></span> <span data-ttu-id="f29e4-110">`wszMethod`musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="f29e4-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="f29e4-111">[out] Ukazatel rozhraní, které umožňuje přístup k kvalifikátory metody obdrží.</span><span class="sxs-lookup"><span data-stu-id="f29e4-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="f29e4-112">`ppQualSet`nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="f29e4-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="f29e4-113">Pokud dojde k chybě, nevrátí nový objekt a ukazatel je nastaven tak, aby odkazoval na `null`.</span><span class="sxs-lookup"><span data-stu-id="f29e4-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f29e4-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f29e4-114">Return value</span></span>

<span data-ttu-id="f29e4-115">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="f29e4-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f29e4-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f29e4-116">Constant</span></span>  |<span data-ttu-id="f29e4-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f29e4-117">Value</span></span>  |<span data-ttu-id="f29e4-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f29e4-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="f29e4-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f29e4-119">0x80041002</span></span> | <span data-ttu-id="f29e4-120">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f29e4-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f29e4-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f29e4-121">0x80041008</span></span> | <span data-ttu-id="f29e4-122">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="f29e4-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f29e4-123">0</span><span class="sxs-lookup"><span data-stu-id="f29e4-123">0</span></span> | <span data-ttu-id="f29e4-124">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f29e4-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f29e4-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f29e4-125">Remarks</span></span>

<span data-ttu-id="f29e4-126">Tato funkce zabalí volání [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="f29e4-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="f29e4-127">Volání této funkce je podporována pouze v případě, že je aktuální objekt definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="f29e4-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="f29e4-128">Není k dispozici pro manipulaci s metoda [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters, které odkazují na modelu CIM instancí.</span><span class="sxs-lookup"><span data-stu-id="f29e4-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="f29e4-129">Protože každá metoda může mít svůj vlastní kvalifikátory [IWbemQualifierSet ukazatel](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umožňuje přidat, upravit nebo odstranit tyto kvalifikátory volající.</span><span class="sxs-lookup"><span data-stu-id="f29e4-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="f29e4-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f29e4-130">Requirements</span></span>  
<span data-ttu-id="f29e4-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f29e4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f29e4-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f29e4-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f29e4-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f29e4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f29e4-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f29e4-134">See also</span></span>  
[<span data-ttu-id="f29e4-135">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f29e4-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
