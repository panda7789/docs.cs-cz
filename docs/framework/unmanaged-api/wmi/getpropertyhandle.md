---
title: "Funkce GetPropertyHandle (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetPropertyHandle vrací jedinečný popisovač identit, že bude vlastnost."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyHandle
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyHandle
helpviewer_keywords: GetPropertyHandle function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ab3df6d2233059de76036da7ff27f5cc1808aaf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="9675b-103">GetPropertyHandle – funkce</span><span class="sxs-lookup"><span data-stu-id="9675b-103">GetPropertyHandle function</span></span>
<span data-ttu-id="9675b-104">Vrací jedinečný popisovač, který identifikuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9675b-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="9675b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9675b-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a><span data-ttu-id="9675b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9675b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9675b-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="9675b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9675b-108">[v] Ukazatel na [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="9675b-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`wszPropertyName`  
<span data-ttu-id="9675b-109">[v] Řetězec kódovaný jazykem UTF16 characaters, který obsahuje název vlastnosti ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="9675b-109">[in] A null-terminated string of UTF16-encoded characaters that contains the property name.</span></span>   

`pType`  
<span data-ttu-id="9675b-110">[out] Ukazatel [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) člen výčtu, který představuje typ modelu CIM vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9675b-110">[out] A pointer to a [`CIMTYPE`](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`   
<span data-ttu-id="9675b-111">[out] Ukazatel na celé číslo, které obsahuje popisovače vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9675b-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="9675b-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9675b-112">Return value</span></span>

<span data-ttu-id="9675b-113">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="9675b-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9675b-114">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9675b-114">Constant</span></span>  |<span data-ttu-id="9675b-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9675b-115">Value</span></span>  |<span data-ttu-id="9675b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="9675b-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="9675b-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9675b-117">0x80041002</span></span> | <span data-ttu-id="9675b-118">Zadaný název vlastnosti nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="9675b-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9675b-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9675b-119">0x80041008</span></span> | <span data-ttu-id="9675b-120">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="9675b-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="9675b-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="9675b-121">0x8004100c</span></span> | <span data-ttu-id="9675b-122">Požadovaná vlastnost je typu jsou `CIM_OBJECT` nebo `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="9675b-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9675b-123">0</span><span class="sxs-lookup"><span data-stu-id="9675b-123">0</span></span> | <span data-ttu-id="9675b-124">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9675b-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9675b-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9675b-125">Remarks</span></span>

<span data-ttu-id="9675b-126">Tato funkce zabalí volání [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="9675b-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="9675b-127">Tento popisovač můžete použít k identifikaci vlastnosti při použití [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) metody pro čtení nebo zápis hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="9675b-127">You can use this handle to identify properties when using  [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) methods to read or write property values.</span></span>

<span data-ttu-id="9675b-128">Zpracovává se nedají načíst pro vlastnosti všech typů dat než `CIM_OBJECT` a `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="9675b-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="9675b-129">Vrátí popisovače pracovní napříč všemi instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="9675b-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="9675b-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9675b-130">Requirements</span></span>  
<span data-ttu-id="9675b-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9675b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9675b-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9675b-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9675b-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9675b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9675b-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="9675b-134">See also</span></span>  
[<span data-ttu-id="9675b-135">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9675b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
