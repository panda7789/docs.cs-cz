---
title: Funkce GetPropertyOrigin (Reference k rozhraní API Unmnaged)
description: Funkce GetPropertyOrigin určuje třídy, ve kterém je deklarována vlastnost.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86c512f25c40f201d818b6789c6410bfb095b878
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865267"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="294a0-103">Funkce GetPropertyOrigin</span><span class="sxs-lookup"><span data-stu-id="294a0-103">GetPropertyOrigin function</span></span>
<span data-ttu-id="294a0-104">Určuje třídy, ve kterém je deklarována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="294a0-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="294a0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="294a0-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="294a0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="294a0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="294a0-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="294a0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="294a0-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="294a0-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="294a0-109">[in] Název vlastnosti pro objekt, jehož vlastnící třídy jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="294a0-109">[in] The name of the property for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="294a0-110">[out] Získá název třídy, která vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="294a0-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="294a0-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="294a0-111">Return value</span></span>

<span data-ttu-id="294a0-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="294a0-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="294a0-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="294a0-113">Constant</span></span>  |<span data-ttu-id="294a0-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="294a0-114">Value</span></span>  |<span data-ttu-id="294a0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="294a0-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="294a0-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="294a0-116">0x80041001</span></span> | <span data-ttu-id="294a0-117">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="294a0-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="294a0-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="294a0-118">0x80041002</span></span> | <span data-ttu-id="294a0-119">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="294a0-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="294a0-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="294a0-120">0x80041008</span></span> | <span data-ttu-id="294a0-121">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="294a0-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="294a0-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="294a0-122">0x80041006</span></span> | <span data-ttu-id="294a0-123">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="294a0-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="294a0-124">0</span><span class="sxs-lookup"><span data-stu-id="294a0-124">0</span></span> | <span data-ttu-id="294a0-125">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="294a0-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="294a0-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="294a0-126">Remarks</span></span>

<span data-ttu-id="294a0-127">Tato funkce zalamuje volání na [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) metody.</span><span class="sxs-lookup"><span data-stu-id="294a0-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="294a0-128">Protože třída může dědit vlastnosti z jednoho nebo více základních tříd, vývojáři často chtějí zjistit vlastnosti, ve kterém je definována dané metody.</span><span class="sxs-lookup"><span data-stu-id="294a0-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="294a0-129">`pstrClassName` Parametr nesmí odkazovat na platnou `BSTR` před voláním funkce, protože se jedná `out` parametr; tato ukazatel není uvolněný po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="294a0-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="294a0-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="294a0-130">Requirements</span></span>  
<span data-ttu-id="294a0-131">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="294a0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="294a0-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="294a0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="294a0-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="294a0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="294a0-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="294a0-134">See also</span></span>  
[<span data-ttu-id="294a0-135">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="294a0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
