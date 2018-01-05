---
title: "Funkce GetObjectText (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetObjectText vrací textové vykreslování objektu v syntaxi MOF."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b47dc73bb9da71b0c8593aa5758179327d7572d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getobjecttext-function"></a><span data-ttu-id="14d76-103">GetObjectText – funkce</span><span class="sxs-lookup"><span data-stu-id="14d76-103">GetObjectText function</span></span>
<span data-ttu-id="14d76-104">Vrátí textovou vykreslit objekt ve formátu MOF (Managed Object) syntaxe.</span><span class="sxs-lookup"><span data-stu-id="14d76-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="14d76-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14d76-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="14d76-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="14d76-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="14d76-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="14d76-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="14d76-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="14d76-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="14d76-109">[v] Za normálních okolností 0.</span><span class="sxs-lookup"><span data-stu-id="14d76-109">[in] Normally 0.</span></span> <span data-ttu-id="14d76-110">Pokud `WBEM_FLAG_NO_FLAVORS` (nebo 0x1) je zadán, jsou zahrnuty bez informací o šíření nebo příchuť kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="14d76-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="14d76-111">[out] Ukazatel na `null` na položku.</span><span class="sxs-lookup"><span data-stu-id="14d76-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="14d76-112">Na vrátit, nově přidělených `BSTR` vykreslování syntaxe MOF objektu, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="14d76-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="14d76-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="14d76-113">Return value</span></span>

<span data-ttu-id="14d76-114">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="14d76-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="14d76-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="14d76-115">Constant</span></span>  |<span data-ttu-id="14d76-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="14d76-116">Value</span></span>  |<span data-ttu-id="14d76-117">Popis</span><span class="sxs-lookup"><span data-stu-id="14d76-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="14d76-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="14d76-118">0x80041001</span></span> | <span data-ttu-id="14d76-119">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="14d76-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="14d76-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="14d76-120">0x80041008</span></span> | <span data-ttu-id="14d76-121">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="14d76-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="14d76-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="14d76-122">0x80041006</span></span> | <span data-ttu-id="14d76-123">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="14d76-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="14d76-124">0</span><span class="sxs-lookup"><span data-stu-id="14d76-124">0</span></span> | <span data-ttu-id="14d76-125">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="14d76-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="14d76-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14d76-126">Remarks</span></span>

<span data-ttu-id="14d76-127">Tato funkce zabalí volání [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="14d76-127">This function wraps a call to the [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="14d76-128">Vrátí text MOF neobsahuje všechny informace o objektu, ale pouze dostatek informací pro kompilátor MOF moct původní objekt znovu vytvořit.</span><span class="sxs-lookup"><span data-stu-id="14d76-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="14d76-129">Žádné šířený kvalifikátory nebo vlastnosti nadřazené třídy pro instanci, jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="14d76-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="14d76-130">Následující algoritmus se používá k rekonstrukci text parametry metody:</span><span class="sxs-lookup"><span data-stu-id="14d76-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="14d76-131">Parametry jsou resequenced v pořadí podle jejich hodnot identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="14d76-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="14d76-132">Parametry, které jsou určeny jako `[in]` a `[out]` jsou sloučeny do jednoho parametru.</span><span class="sxs-lookup"><span data-stu-id="14d76-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="14d76-133">`pstrObjectText`musí být ukazatel na `null` při volání funkce; nesmí bodu na řetězec, který je platný před voláním metody, protože ukazatel nesmí být navrácena.</span><span class="sxs-lookup"><span data-stu-id="14d76-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="14d76-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14d76-134">Requirements</span></span>  
<span data-ttu-id="14d76-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14d76-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14d76-136">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="14d76-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="14d76-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="14d76-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d76-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="14d76-138">See also</span></span>  
[<span data-ttu-id="14d76-139">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="14d76-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
