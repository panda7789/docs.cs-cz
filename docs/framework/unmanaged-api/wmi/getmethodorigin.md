---
title: Funkce GetMethodOrigin (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetMethodOrigin Určuje třídu, ve kterém je deklarovaná metodu.
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
ms.openlocfilehash: 35e56494d0082db970afce21da8e63a597f0a535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458146"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="2d0b5-103">GetMethodOrigin – funkce</span><span class="sxs-lookup"><span data-stu-id="2d0b5-103">GetMethodOrigin function</span></span>
<span data-ttu-id="2d0b5-104">Určuje třídu, ve kterém je deklarovaná metodu.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="2d0b5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d0b5-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="2d0b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d0b5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2d0b5-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2d0b5-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="2d0b5-109">[v] Název metody pro objekt, jehož vlastnícím třída je požadováno.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="2d0b5-110">[out] Získá název třídy, která vlastní metodu.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="2d0b5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d0b5-111">Return value</span></span>

<span data-ttu-id="2d0b5-112">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="2d0b5-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2d0b5-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="2d0b5-113">Constant</span></span>  |<span data-ttu-id="2d0b5-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2d0b5-114">Value</span></span>  |<span data-ttu-id="2d0b5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2d0b5-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="2d0b5-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2d0b5-116">0x80041002</span></span> | <span data-ttu-id="2d0b5-117">Zadaná metoda nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2d0b5-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2d0b5-118">0x80041008</span></span> | <span data-ttu-id="2d0b5-119">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2d0b5-120">0</span><span class="sxs-lookup"><span data-stu-id="2d0b5-120">0</span></span> | <span data-ttu-id="2d0b5-121">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2d0b5-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d0b5-122">Remarks</span></span>

<span data-ttu-id="2d0b5-123">Tato funkce zabalí volání [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="2d0b5-124">Protože třída může dědit vlastnosti metody z jednoho nebo více základní třídy, vývojáři často chtějí určit třídu, ve kterém je definovaný dané metody.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="2d0b5-125">`pstrClassName` Parametr nesmí přejděte na platnou `BSTR` předtím, než je volána funkce, protože se jedná `out` parametr; tato ukazatel není navrácena po funkce vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2d0b5-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d0b5-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d0b5-126">Requirements</span></span>  
<span data-ttu-id="2d0b5-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d0b5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d0b5-128">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2d0b5-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2d0b5-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2d0b5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d0b5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d0b5-130">See also</span></span>  
[<span data-ttu-id="2d0b5-131">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="2d0b5-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
