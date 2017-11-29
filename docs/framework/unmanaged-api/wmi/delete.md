---
title: "Odstranit funkci (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce odstranění odstraní zadanou vlastnost a všechny jeho kvalifikátory z definice třídy CIM."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f32487d2bd59bd76acdc32218c6bb0842de20e87
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="delete-function"></a><span data-ttu-id="6fa44-103">Odstranit – funkce</span><span class="sxs-lookup"><span data-stu-id="6fa44-103">Delete function</span></span>
<span data-ttu-id="6fa44-104">Odstraní zadanou vlastnost a všechny jeho kvalifikátory z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="6fa44-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6fa44-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fa44-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="6fa44-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fa44-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6fa44-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="6fa44-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6fa44-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="6fa44-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="6fa44-109">[v] Název vlastnosti, která má odstranit.</span><span class="sxs-lookup"><span data-stu-id="6fa44-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="6fa44-110">`wszName`musí být ukazatel na platnou `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="6fa44-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="6fa44-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6fa44-111">Return value</span></span>

<span data-ttu-id="6fa44-112">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="6fa44-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6fa44-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6fa44-113">Constant</span></span>  |<span data-ttu-id="6fa44-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6fa44-114">Value</span></span>  |<span data-ttu-id="6fa44-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6fa44-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="6fa44-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6fa44-116">0x80041001</span></span> | <span data-ttu-id="6fa44-117">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="6fa44-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="6fa44-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="6fa44-118">0x80041016</span></span> | <span data-ttu-id="6fa44-119">Vlastnost nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="6fa44-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6fa44-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6fa44-120">0x80041008</span></span> | <span data-ttu-id="6fa44-121">Formát  `wszzName` je neplatný.</span><span class="sxs-lookup"><span data-stu-id="6fa44-121">`wszzName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="6fa44-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6fa44-122">0x80041002</span></span> | <span data-ttu-id="6fa44-123">Zadaná vlastnost neexistuje.</span><span class="sxs-lookup"><span data-stu-id="6fa44-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6fa44-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6fa44-124">0x80041006</span></span> | <span data-ttu-id="6fa44-125">Není k dispozici dostatek paměti pro dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="6fa44-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="6fa44-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="6fa44-126">0x8004101c</span></span> | <span data-ttu-id="6fa44-127">Vlastnost je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6fa44-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="6fa44-128">Vlastnost je vlastnost systému.</span><span class="sxs-lookup"><span data-stu-id="6fa44-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6fa44-129">0</span><span class="sxs-lookup"><span data-stu-id="6fa44-129">0</span></span> | <span data-ttu-id="6fa44-130">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6fa44-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="6fa44-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="6fa44-131">0x80041030</span></span> | <span data-ttu-id="6fa44-132">Funkce odstranit výchozí hodnotu přepsání pro aktuální třídu.</span><span class="sxs-lookup"><span data-stu-id="6fa44-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="6fa44-133">Výchozí hodnota pro tuto vlastnost v nadřazené třídě byl reactiviated.</span><span class="sxs-lookup"><span data-stu-id="6fa44-133">The default value for this property in the parent class has been reactiviated.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="6fa44-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fa44-134">Remarks</span></span>

<span data-ttu-id="6fa44-135">Tato funkce zabalí volání [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="6fa44-135">This function wraps a call to the [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6fa44-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fa44-136">Requirements</span></span>  
 <span data-ttu-id="6fa44-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fa44-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fa44-138">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6fa44-138">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6fa44-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6fa44-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa44-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fa44-140">See also</span></span>  
[<span data-ttu-id="6fa44-141">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="6fa44-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
