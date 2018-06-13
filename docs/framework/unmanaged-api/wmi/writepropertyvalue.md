---
title: Funkce WritePropertyValue (referenční dokumentace nespravovaného rozhraní API)
description: Funkce WritePropertyValue zapíše bajtů na vlastnost.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6aafb918616d27cf6289a8747f3336b2e813beb6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461081"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="b8eb4-103">WritePropertyValue – funkce</span><span class="sxs-lookup"><span data-stu-id="b8eb4-103">WritePropertyValue function</span></span>
<span data-ttu-id="b8eb4-104">Zapíše zadaný počet bajtů na vlastnost identifikovaný popisovače vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b8eb4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8eb4-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="b8eb4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8eb4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b8eb4-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b8eb4-108">[v] Ukazatel na [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`lHandle`  
<span data-ttu-id="b8eb4-109">[v] Celé číslo, které obsahuje popisovač, který identifikuje tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="b8eb4-110">Popisovač může načíst volání [GetPropertyHandle](getpropertyhandle.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="b8eb4-111">[v] Počet bajtů zapisovaný pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="b8eb4-112">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="b8eb4-113">[out] Ukazatel na pole bajtů, který obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8eb4-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8eb4-114">Return value</span></span>

<span data-ttu-id="b8eb4-115">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="b8eb4-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b8eb4-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b8eb4-116">Constant</span></span>  |<span data-ttu-id="b8eb4-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b8eb4-117">Value</span></span>  |<span data-ttu-id="b8eb4-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b8eb4-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b8eb4-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b8eb4-119">0x80041008</span></span> | <span data-ttu-id="b8eb4-120">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="b8eb4-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="b8eb4-121">0x80041005</span></span> | <span data-ttu-id="b8eb4-122">Došlo k neshodě typů.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b8eb4-123">0</span><span class="sxs-lookup"><span data-stu-id="b8eb4-123">0</span></span> | <span data-ttu-id="b8eb4-124">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b8eb4-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8eb4-125">Remarks</span></span>

<span data-ttu-id="b8eb4-126">Tato funkce zabalí volání [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="b8eb4-127">Pomocí této funkce můžete nastavit řetězec a všechny ostatní jinou hodnotu než`DWORD` nebo jiných-`QWORD` data.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="b8eb4-128">Hodnoty vlastnosti neřetězcový `lNumBytes` musí být zadaný typ velikost správná data.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="b8eb4-129">Řetězce hodnoty vlastnosti `lNumBytes` musí mít délku v bajtech zadaný řetězec a řetězec sám sebe musí být i délka v bajtech a následně s hodnotou null ukončení znakem.</span><span class="sxs-lookup"><span data-stu-id="b8eb4-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8eb4-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8eb4-130">Requirements</span></span>  
<span data-ttu-id="b8eb4-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8eb4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8eb4-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b8eb4-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b8eb4-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8eb4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8eb4-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8eb4-134">See also</span></span>  
[<span data-ttu-id="b8eb4-135">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="b8eb4-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
