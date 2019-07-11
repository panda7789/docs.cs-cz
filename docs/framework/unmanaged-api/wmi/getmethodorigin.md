---
title: Funkce GetMethodOrigin (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetMethodOrigin určuje třídy, ve kterém je deklarována metodu.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b21e08d3bf6845b9fc44d5a5edef0ea39b91da5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746536"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="97613-103">Funkce GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="97613-103">GetMethodOrigin function</span></span>
<span data-ttu-id="97613-104">Určuje třídy, ve kterém je deklarována metodu.</span><span class="sxs-lookup"><span data-stu-id="97613-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="97613-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97613-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="97613-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97613-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="97613-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="97613-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="97613-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="97613-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="97613-109">[in] Název metody pro objekt, jehož vlastnící třídy jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="97613-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="97613-110">[out] Získá název třídy, která vlastní metodu.</span><span class="sxs-lookup"><span data-stu-id="97613-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="97613-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97613-111">Return value</span></span>

<span data-ttu-id="97613-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="97613-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="97613-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="97613-113">Constant</span></span>  |<span data-ttu-id="97613-114">Value</span><span class="sxs-lookup"><span data-stu-id="97613-114">Value</span></span>  |<span data-ttu-id="97613-115">Popis</span><span class="sxs-lookup"><span data-stu-id="97613-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="97613-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="97613-116">0x80041002</span></span> | <span data-ttu-id="97613-117">Zadaná metoda nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="97613-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="97613-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="97613-118">0x80041008</span></span> | <span data-ttu-id="97613-119">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="97613-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="97613-120">0</span><span class="sxs-lookup"><span data-stu-id="97613-120">0</span></span> | <span data-ttu-id="97613-121">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="97613-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="97613-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97613-122">Remarks</span></span>

<span data-ttu-id="97613-123">Tato funkce zalamuje volání na [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="97613-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="97613-124">Protože třída může dědit z jednoho nebo více základních tříd metody, vývojáři často chtějí určit třídu, ve kterém je definována dané metody.</span><span class="sxs-lookup"><span data-stu-id="97613-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="97613-125">`pstrClassName` Parametr nesmí odkazovat na platnou `BSTR` před voláním funkce, protože se jedná `out` parametr; tato ukazatel není uvolněný po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="97613-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="97613-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97613-126">Requirements</span></span>  
<span data-ttu-id="97613-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97613-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97613-128">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="97613-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="97613-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="97613-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97613-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97613-130">See also</span></span>

- [<span data-ttu-id="97613-131">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="97613-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
