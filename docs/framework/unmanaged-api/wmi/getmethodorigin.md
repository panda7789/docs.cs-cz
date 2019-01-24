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
ms.openlocfilehash: 76f449e52168001a2aaac6cbc3707361cf7f809a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582460"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="9f4be-103">Funkce GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="9f4be-103">GetMethodOrigin function</span></span>
<span data-ttu-id="9f4be-104">Určuje třídy, ve kterém je deklarována metodu.</span><span class="sxs-lookup"><span data-stu-id="9f4be-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="9f4be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f4be-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="9f4be-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f4be-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9f4be-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="9f4be-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9f4be-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="9f4be-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="9f4be-109">[in] Název metody pro objekt, jehož vlastnící třídy jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="9f4be-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="9f4be-110">[out] Získá název třídy, která vlastní metodu.</span><span class="sxs-lookup"><span data-stu-id="9f4be-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="9f4be-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9f4be-111">Return value</span></span>

<span data-ttu-id="9f4be-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="9f4be-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9f4be-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9f4be-113">Constant</span></span>  |<span data-ttu-id="9f4be-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9f4be-114">Value</span></span>  |<span data-ttu-id="9f4be-115">Popis</span><span class="sxs-lookup"><span data-stu-id="9f4be-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="9f4be-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9f4be-116">0x80041002</span></span> | <span data-ttu-id="9f4be-117">Zadaná metoda nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="9f4be-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9f4be-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9f4be-118">0x80041008</span></span> | <span data-ttu-id="9f4be-119">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="9f4be-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9f4be-120">0</span><span class="sxs-lookup"><span data-stu-id="9f4be-120">0</span></span> | <span data-ttu-id="9f4be-121">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9f4be-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9f4be-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f4be-122">Remarks</span></span>

<span data-ttu-id="9f4be-123">Tato funkce zalamuje volání na [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="9f4be-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="9f4be-124">Protože třída může dědit z jednoho nebo více základních tříd metody, vývojáři často chtějí určit třídu, ve kterém je definována dané metody.</span><span class="sxs-lookup"><span data-stu-id="9f4be-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="9f4be-125">`pstrClassName` Parametr nesmí odkazovat na platnou `BSTR` před voláním funkce, protože se jedná `out` parametr; tato ukazatel není uvolněný po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="9f4be-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f4be-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f4be-126">Requirements</span></span>  
<span data-ttu-id="9f4be-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f4be-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f4be-128">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9f4be-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9f4be-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f4be-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f4be-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f4be-130">See also</span></span>
- [<span data-ttu-id="9f4be-131">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9f4be-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
