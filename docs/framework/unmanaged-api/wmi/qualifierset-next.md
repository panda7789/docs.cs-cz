---
title: "Funkce QualifierSet_Next (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_Next načte další kvalifikátor ve výčtu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 01a9c9d162039547849597aaa9c8a6fa38a31455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="4c9cf-103">QualifierSet_Next – funkce</span><span class="sxs-lookup"><span data-stu-id="4c9cf-103">QualifierSet_Next function</span></span>
<span data-ttu-id="4c9cf-104">Načte další kvalifikátor v výčet, který je spuštěn s volání [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4c9cf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c9cf-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="4c9cf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c9cf-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="4c9cf-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="4c9cf-108">[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="4c9cf-109">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-109">[in] Reserved.</span></span> <span data-ttu-id="4c9cf-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="4c9cf-111">[out] Název kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="4c9cf-112">Pokud `null`, tento parametr je ignorováno, jinak hodnota `pstrName` by neměl přejděte na platnou `BSTR` nebo nevrací paměť.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="4c9cf-113">Pokud není null, funkce vždy přiděluje nový `BSTR` při vrácení `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="4c9cf-114">[out] Po úspěšné, hodnota kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="4c9cf-115">Pokud se funkce nezdaří, `VARIANT` na kterou odkazuje `pVal` se nemění.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="4c9cf-116">Pokud tento parametr je `null`, parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="4c9cf-117">[out] Ukazatel na typ LONG, která přijímá charakter kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="4c9cf-118">V případě potřeby příchuť informace není tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4c9cf-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4c9cf-119">Return value</span></span>

<span data-ttu-id="4c9cf-120">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="4c9cf-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4c9cf-121">Konstanta</span><span class="sxs-lookup"><span data-stu-id="4c9cf-121">Constant</span></span>  |<span data-ttu-id="4c9cf-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4c9cf-122">Value</span></span>  |<span data-ttu-id="4c9cf-123">Popis</span><span class="sxs-lookup"><span data-stu-id="4c9cf-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4c9cf-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4c9cf-124">0x80041008</span></span> | <span data-ttu-id="4c9cf-125">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="4c9cf-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="4c9cf-126">0x8004101d</span></span> | <span data-ttu-id="4c9cf-127">Volající nezavolalo [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4c9cf-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4c9cf-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4c9cf-128">0x80041006</span></span> | <span data-ttu-id="4c9cf-129">Je k dispozici zahájíte nové – výčet není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="4c9cf-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="4c9cf-130">0x40005</span></span> | <span data-ttu-id="4c9cf-131">Ve výčtu nezbývají žádné další kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4c9cf-132">0</span><span class="sxs-lookup"><span data-stu-id="4c9cf-132">0</span></span> | <span data-ttu-id="4c9cf-133">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4c9cf-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c9cf-134">Remarks</span></span>

<span data-ttu-id="4c9cf-135">Tato funkce zabalí volání [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-135">This function wraps a call to the [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4c9cf-136">Volání `QualifierSet_Next` funkce opakovaně se vytvořit výčet všech kvalifikátory dokud návratový funkce `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="4c9cf-137">Chcete-li ukončit výčtu již v rané fázi, volejte [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="4c9cf-138">Pořadí kvalifikátory vrátil během výčtu není definován.</span><span class="sxs-lookup"><span data-stu-id="4c9cf-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c9cf-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c9cf-139">Requirements</span></span>  
 <span data-ttu-id="4c9cf-140">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c9cf-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c9cf-141">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4c9cf-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4c9cf-142">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c9cf-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9cf-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c9cf-143">See also</span></span>  
[<span data-ttu-id="4c9cf-144">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="4c9cf-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
