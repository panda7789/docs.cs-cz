---
title: "Metoda DeleteMethod – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce metody DeleteMethod odstraní zadanou metodu z definice třídy CIM."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: DeleteMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: DeleteMethod
helpviewer_keywords: DeleteMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d931cb76eeaf19ddeb80bdde412fabeea4b70203
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="deletemethod-function"></a><span data-ttu-id="98693-103">Metoda DeleteMethod – funkce</span><span class="sxs-lookup"><span data-stu-id="98693-103">DeleteMethod function</span></span>
<span data-ttu-id="98693-104">Odstraní zadanou metodu z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="98693-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="98693-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98693-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="98693-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="98693-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="98693-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="98693-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="98693-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="98693-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="98693-109">[v] Název metody, která odebere z tabulky třídy.</span><span class="sxs-lookup"><span data-stu-id="98693-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="98693-110">`wszName`musí být ukazatel na platnou `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="98693-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="98693-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="98693-111">Return value</span></span>

<span data-ttu-id="98693-112">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="98693-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="98693-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="98693-113">Constant</span></span>  |<span data-ttu-id="98693-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="98693-114">Value</span></span>  |<span data-ttu-id="98693-115">Popis</span><span class="sxs-lookup"><span data-stu-id="98693-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="98693-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="98693-116">0x80041002</span></span> | <span data-ttu-id="98693-117">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="98693-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="98693-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="98693-118">0x80041006</span></span> | <span data-ttu-id="98693-119">Není k dispozici dostatek paměti pro dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="98693-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="98693-120">0</span><span class="sxs-lookup"><span data-stu-id="98693-120">0</span></span> | <span data-ttu-id="98693-121">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="98693-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="98693-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98693-122">Remarks</span></span>

<span data-ttu-id="98693-123">Tato funkce zabalí volání [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="98693-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="98693-124">Metoda odstranění není podporována pro [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ukazatele, které odkazují na modelu CIM instancí.</span><span class="sxs-lookup"><span data-stu-id="98693-124">Method deletion is not supported for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="98693-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98693-125">Requirements</span></span>  
 <span data-ttu-id="98693-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98693-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98693-127">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="98693-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="98693-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="98693-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98693-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="98693-129">See also</span></span>  
[<span data-ttu-id="98693-130">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="98693-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
