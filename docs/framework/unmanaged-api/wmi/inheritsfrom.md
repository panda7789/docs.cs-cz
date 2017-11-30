---
title: "Funkce InheritsFrom (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce InheritsFrom Určuje, zda třídy nebo instance je odvozena z konkrétní nadřazené třídy."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: InheritsFrom
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: InheritsFrom
helpviewer_keywords: InheritsFrom function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aedeec76f4fabb2f6bd32d7d06eb5a1a5734534e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="7a1f4-103">InheritsFrom – funkce</span><span class="sxs-lookup"><span data-stu-id="7a1f4-103">InheritsFrom function</span></span>
<span data-ttu-id="7a1f4-104">Určuje, zda aktuální třídy nebo instance je odvozena od třídy zadaný nadřazený.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="7a1f4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a1f4-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="7a1f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a1f4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7a1f4-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7a1f4-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="7a1f4-109">[v] Název třídy.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-109">[in] The name of the class.</span></span> <span data-ttu-id="7a1f4-110">`wszAncestor`musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a1f4-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7a1f4-111">Return value</span></span>

<span data-ttu-id="7a1f4-112">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="7a1f4-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7a1f4-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7a1f4-113">Constant</span></span>  |<span data-ttu-id="7a1f4-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7a1f4-114">Value</span></span>  |<span data-ttu-id="7a1f4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7a1f4-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7a1f4-116">0</span><span class="sxs-lookup"><span data-stu-id="7a1f4-116">0</span></span> | <span data-ttu-id="7a1f4-117">Aktuální objekt dědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="7a1f4-118">1</span><span class="sxs-lookup"><span data-stu-id="7a1f4-118">1</span></span> | <span data-ttu-id="7a1f4-119">Aktuální objekt nedědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7a1f4-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7a1f4-120">0x80041008</span></span> | <span data-ttu-id="7a1f4-121">`wszAncestor`je `null`.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7a1f4-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a1f4-122">Remarks</span></span>

<span data-ttu-id="7a1f4-123">Tato funkce zabalí volání [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="7a1f4-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a1f4-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a1f4-124">Requirements</span></span>  
 <span data-ttu-id="7a1f4-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a1f4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a1f4-126">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7a1f4-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7a1f4-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7a1f4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1f4-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a1f4-128">See also</span></span>  
[<span data-ttu-id="7a1f4-129">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="7a1f4-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
