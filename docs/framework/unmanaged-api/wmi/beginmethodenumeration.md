---
title: "Funkce BeginMethodEnumeration (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce BeginMethodEnumeration začne výčet metod objektu"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginMethodEnumeration
helpviewer_keywords: BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e44c432f9503f96ad4dab9e25b78e6dd148f94c
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="66aa6-103">Funkce BeginEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="66aa6-103">BeginEnumeration function</span></span>
<span data-ttu-id="66aa6-104">Zahájí výčet dostupné metody pro objekt.</span><span class="sxs-lookup"><span data-stu-id="66aa6-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="66aa6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66aa6-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="66aa6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="66aa6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="66aa6-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="66aa6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="66aa6-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="66aa6-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="66aa6-109">[v] Nula (0) pro všechny metody nebo příznak, který určuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="66aa6-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="66aa6-110">Následující příznaky jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="66aa6-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="66aa6-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="66aa6-111">Constant</span></span>  |<span data-ttu-id="66aa6-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66aa6-112">Value</span></span>  |<span data-ttu-id="66aa6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="66aa6-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="66aa6-114">0x10</span><span class="sxs-lookup"><span data-stu-id="66aa6-114">0x10</span></span> | <span data-ttu-id="66aa6-115">Omezte výčtu pro metody, které jsou definovány v vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="66aa6-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="66aa6-116">0x20</span><span class="sxs-lookup"><span data-stu-id="66aa6-116">0x20</span></span> | <span data-ttu-id="66aa6-117">Omezte výčet vlastností, které se dědí z třídy base.</span><span class="sxs-lookup"><span data-stu-id="66aa6-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="66aa6-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66aa6-118">Return value</span></span>

<span data-ttu-id="66aa6-119">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="66aa6-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="66aa6-120">Konstanta</span><span class="sxs-lookup"><span data-stu-id="66aa6-120">Constant</span></span>  |<span data-ttu-id="66aa6-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66aa6-121">Value</span></span>  |<span data-ttu-id="66aa6-122">Popis</span><span class="sxs-lookup"><span data-stu-id="66aa6-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="66aa6-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="66aa6-123">0x80041008</span></span> | <span data-ttu-id="66aa6-124">`lEnnumFlags`není zadaný příznaky je nulová.</span><span class="sxs-lookup"><span data-stu-id="66aa6-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="66aa6-125">0</span><span class="sxs-lookup"><span data-stu-id="66aa6-125">0</span></span> | <span data-ttu-id="66aa6-126">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="66aa6-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="66aa6-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66aa6-127">Remarks</span></span>

<span data-ttu-id="66aa6-128">Tato funkce zabalí volání [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="66aa6-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="66aa6-129">Toto volání metody je podporována pouze, pokud se aktuální objekt definici třídy.</span><span class="sxs-lookup"><span data-stu-id="66aa6-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="66aa6-130">Manipulace s metoda není k dispozici z [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ukazatele, které odkazují na instancí.</span><span class="sxs-lookup"><span data-stu-id="66aa6-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="66aa6-131">Pořadí, ve kterém jsou uvedené metody záruku, že se jako výchozí pro danou instanci [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="66aa6-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="66aa6-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66aa6-132">Requirements</span></span>  
 <span data-ttu-id="66aa6-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66aa6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66aa6-134">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="66aa6-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="66aa6-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66aa6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66aa6-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="66aa6-136">See also</span></span>  
[<span data-ttu-id="66aa6-137">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="66aa6-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
