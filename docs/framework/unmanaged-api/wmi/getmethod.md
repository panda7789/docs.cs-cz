---
title: "Getmethod – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Getmethod – funkce načte informace o metodě."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f22a2dfa7aae411cac960cbad2017718df8057e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getmethod-function"></a><span data-ttu-id="20c7e-103">Getmethod – funkce</span><span class="sxs-lookup"><span data-stu-id="20c7e-103">GetMethod function</span></span>
<span data-ttu-id="20c7e-104">Načte informace o zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="20c7e-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="20c7e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20c7e-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="20c7e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="20c7e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="20c7e-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="20c7e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="20c7e-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="20c7e-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="20c7e-109">[v] Název metody.</span><span class="sxs-lookup"><span data-stu-id="20c7e-109">[in] The method name.</span></span> <span data-ttu-id="20c7e-110">Tento parametr nemůže být `null` a musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="20c7e-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="20c7e-111">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="20c7e-111">[in] Reserved.</span></span> <span data-ttu-id="20c7e-112">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="20c7e-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="20c7e-113">[out] Ukazatel na adresu [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instanci, která popisuje v paramteers metodě.</span><span class="sxs-lookup"><span data-stu-id="20c7e-113">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="20c7e-114">Tento parametr je ignorována, pokud je nastaven na hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="20c7e-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="20c7e-115">[out] Ukazatel na adresu [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instanci, která popisuje výstupní parametry metody.</span><span class="sxs-lookup"><span data-stu-id="20c7e-115">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="20c7e-116">Tento parametr je ignorována, pokud je nastaven na hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="20c7e-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="20c7e-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="20c7e-117">Return value</span></span>

<span data-ttu-id="20c7e-118">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="20c7e-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="20c7e-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="20c7e-119">Constant</span></span>  |<span data-ttu-id="20c7e-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="20c7e-120">Value</span></span>  |<span data-ttu-id="20c7e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="20c7e-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="20c7e-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="20c7e-122">0x80041002</span></span> | <span data-ttu-id="20c7e-123">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="20c7e-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="20c7e-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="20c7e-124">0x80041006</span></span> | <span data-ttu-id="20c7e-125">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="20c7e-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="20c7e-126">0</span><span class="sxs-lookup"><span data-stu-id="20c7e-126">0</span></span> | <span data-ttu-id="20c7e-127">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="20c7e-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="20c7e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20c7e-128">Remarks</span></span>

<span data-ttu-id="20c7e-129">Tato funkce zabalí volání [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="20c7e-129">This function wraps a call to the [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="20c7e-130">Správa systému Windows můžete nastavit [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ukazatel na `null` Pokud metoda nemá žádné parametry v.</span><span class="sxs-lookup"><span data-stu-id="20c7e-130">Windows Management can set the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="20c7e-131">V `ppInSignature` a `ppOutSignature` popisují v a výstupní parametry, v uvedeném pořadí, v jako vlastnosti `IWbemClassObject` instance třídy systému [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="20c7e-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span></span> <span data-ttu-id="20c7e-132">Vlastnosti v `ppInsignature` jsou pojmenované **Param***n*, kde  *n*  je pozice parametru v (například podpis – metoda jako `Param1`, `Param2`atd.).</span><span class="sxs-lookup"><span data-stu-id="20c7e-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="20c7e-133">Vlastnosti v `ppOutSignature` se také nazývají **Param***n*, a názvem návratovou hodnotu **ReturnValue**.</span><span class="sxs-lookup"><span data-stu-id="20c7e-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="20c7e-134">Další informace a příklady naleznete v tématu [IWbemClassObject::GetMethod metoda](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="20c7e-134">For more information and an example, see [IWbemClassObject::GetMethod method](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="20c7e-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20c7e-135">Requirements</span></span>  
<span data-ttu-id="20c7e-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20c7e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20c7e-137">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="20c7e-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="20c7e-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="20c7e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c7e-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="20c7e-139">See also</span></span>  
[<span data-ttu-id="20c7e-140">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="20c7e-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
