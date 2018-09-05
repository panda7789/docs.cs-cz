---
title: Funkce GetMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetMethod načte informace o metodě.
ms.date: 11/06/2017
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
ms.openlocfilehash: a913de0ff20fba51295fd8282b58e3953be9bba2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773956"
---
# <a name="getmethod-function"></a><span data-ttu-id="93db1-103">Funkce GetMethod</span><span class="sxs-lookup"><span data-stu-id="93db1-103">GetMethod function</span></span>
<span data-ttu-id="93db1-104">Načte informace o zadané metodě.</span><span class="sxs-lookup"><span data-stu-id="93db1-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="93db1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93db1-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="93db1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="93db1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="93db1-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="93db1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="93db1-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="93db1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="93db1-109">[in] Název metody.</span><span class="sxs-lookup"><span data-stu-id="93db1-109">[in] The method name.</span></span> <span data-ttu-id="93db1-110">Tento parametr nemůže mít `null` a musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="93db1-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="93db1-111">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="93db1-111">[in] Reserved.</span></span> <span data-ttu-id="93db1-112">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="93db1-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="93db1-113">[out] Ukazatel na adresu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instanci, která popisuje v paramteers metody.</span><span class="sxs-lookup"><span data-stu-id="93db1-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="93db1-114">Tento parametr se ignoruje, pokud je nastaveno na `null`.</span><span class="sxs-lookup"><span data-stu-id="93db1-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="93db1-115">[out] Ukazatel na adresu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instanci, která popisuje výstupní parametry metody.</span><span class="sxs-lookup"><span data-stu-id="93db1-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="93db1-116">Tento parametr se ignoruje, pokud je nastaveno na `null`.</span><span class="sxs-lookup"><span data-stu-id="93db1-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="93db1-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93db1-117">Return value</span></span>

<span data-ttu-id="93db1-118">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="93db1-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="93db1-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="93db1-119">Constant</span></span>  |<span data-ttu-id="93db1-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="93db1-120">Value</span></span>  |<span data-ttu-id="93db1-121">Popis</span><span class="sxs-lookup"><span data-stu-id="93db1-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="93db1-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="93db1-122">0x80041002</span></span> | <span data-ttu-id="93db1-123">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="93db1-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="93db1-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="93db1-124">0x80041006</span></span> | <span data-ttu-id="93db1-125">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="93db1-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="93db1-126">0</span><span class="sxs-lookup"><span data-stu-id="93db1-126">0</span></span> | <span data-ttu-id="93db1-127">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="93db1-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="93db1-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93db1-128">Remarks</span></span>

<span data-ttu-id="93db1-129">Tato funkce zalamuje volání na [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="93db1-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="93db1-130">Můžete nastavit správu Windows [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ukazatel na `null` Pokud metoda nemá žádné parametry. v.</span><span class="sxs-lookup"><span data-stu-id="93db1-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="93db1-131">V `ppInSignature` a `ppOutSignature` popisují ani výstupní parametry, v uvedeném pořadí, v jako vlastnosti `IWbemClassObject` instance třídy systému [_Parameters](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="93db1-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="93db1-132">Vlastnosti v `ppInsignature` jsou pojmenovány **Param *** n*, kde *n* je pozice parametru v podpisu metody (například `Param1`, `Param2`atd.).</span><span class="sxs-lookup"><span data-stu-id="93db1-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="93db1-133">Vlastnosti v `ppOutSignature` jsou také s názvem **Param *** n*, a návratová hodnota se nazývá **ReturnValue**.</span><span class="sxs-lookup"><span data-stu-id="93db1-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="93db1-134">Další informace a příklad najdete v tématu [IWbemClassObject::GetMethod metoda](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="93db1-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="93db1-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93db1-135">Requirements</span></span>  
<span data-ttu-id="93db1-136">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93db1-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93db1-137">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="93db1-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="93db1-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="93db1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93db1-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93db1-139">See also</span></span>  
[<span data-ttu-id="93db1-140">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="93db1-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
