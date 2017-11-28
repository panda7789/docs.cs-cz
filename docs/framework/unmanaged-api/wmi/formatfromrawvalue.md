---
title: "Funkce FormatFromRawValue (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce FormatFromRawValue převede nezpracovaných dat výkonu do zadaného formátu."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c01db47b5362d7048e2e5ecd1b63acfe03eff860
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2017
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="7d327-103">FormatFromRawValue – funkce</span><span class="sxs-lookup"><span data-stu-id="7d327-103">FormatFromRawValue function</span></span>
<span data-ttu-id="7d327-104">Převede jednu hodnotu hrubý výkon při zpracování dat pro zadaný formát nebo dvě hodnoty hrubý výkon při zpracování dat, pokud převod formátu je založené na čase.</span><span class="sxs-lookup"><span data-stu-id="7d327-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7d327-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d327-105">Syntax</span></span>  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a><span data-ttu-id="7d327-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d327-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="7d327-107">[v] Typ čítače.</span><span class="sxs-lookup"><span data-stu-id="7d327-107">[in] The counter type.</span></span> <span data-ttu-id="7d327-108">Seznam typů čítač najdete v tématu [typy čítače výkonu rozhraní WMI](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="7d327-108">For a list of counter types, see [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span></span> <span data-ttu-id="7d327-109">`dwCounterType`mohou být jakéhokoli typu čítač s výjimkou `PERF_LARGE_RAW_FRACTION` a `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="7d327-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="7d327-110">[v] Formát, do kterého se mají převést data hrubý výkon.</span><span class="sxs-lookup"><span data-stu-id="7d327-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="7d327-111">Může být jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="7d327-111">It can be one of the following values:</span></span>

|<span data-ttu-id="7d327-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7d327-112">Constant</span></span>  |<span data-ttu-id="7d327-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7d327-113">Value</span></span>  |<span data-ttu-id="7d327-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7d327-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="7d327-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="7d327-115">0x00000200</span></span> | <span data-ttu-id="7d327-116">Vrátí počítanou hodnotu jako hodnotu s plovoucí desetinnou dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="7d327-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="7d327-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="7d327-117">0x00000400</span></span> | <span data-ttu-id="7d327-118">Vrátí počítanou hodnotu jako 64bitové celé číslo.</span><span class="sxs-lookup"><span data-stu-id="7d327-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="7d327-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="7d327-119">0x00000100</span></span> | <span data-ttu-id="7d327-120">Vrátí počítanou hodnotu jako 32bitové celé číslo.</span><span class="sxs-lookup"><span data-stu-id="7d327-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="7d327-121">Sloučeny pomocí operátoru OR s jedním z následujících příznaků škálování může být jeden z předchozí hodnot:</span><span class="sxs-lookup"><span data-stu-id="7d327-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="7d327-122">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7d327-122">Constant</span></span>  |<span data-ttu-id="7d327-123">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7d327-123">Value</span></span>  |<span data-ttu-id="7d327-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7d327-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="7d327-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="7d327-125">0x00001000</span></span> | <span data-ttu-id="7d327-126">Neplatí škálování faktory čítače.</span><span class="sxs-lookup"><span data-stu-id="7d327-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="7d327-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="7d327-127">0x00002000</span></span> | <span data-ttu-id="7d327-128">Vynásobte konečná hodnota 1 000.</span><span class="sxs-lookup"><span data-stu-id="7d327-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="7d327-129">[v] Ukazatel na základní doba, v případě potřeby pro převod formátu.</span><span class="sxs-lookup"><span data-stu-id="7d327-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="7d327-130">Pokud není čas základní informace potřebné pro převod formátu, hodnota tohoto parametru je ignorována.</span><span class="sxs-lookup"><span data-stu-id="7d327-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="7d327-131">`pRawValue1`[v] Ukazatel [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) struktura, která reprezentuje hodnotu hrubý výkon.</span><span class="sxs-lookup"><span data-stu-id="7d327-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="7d327-132">`pRawValue2`[v] Ukazatel [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) struktura, která reprezentuje hodnotu druhý hrubý výkon.</span><span class="sxs-lookup"><span data-stu-id="7d327-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="7d327-133">Pokud je druhá hodnota hrubý výkon při zpracování je nezbytné, tento parametr by měl být `null`.</span><span class="sxs-lookup"><span data-stu-id="7d327-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="7d327-134">`pFmtValue`[out] Ukazatel [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) struktura, která přijímá hodnota formátovaný výkonu.</span><span class="sxs-lookup"><span data-stu-id="7d327-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="7d327-135">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d327-135">Return value</span></span>

<span data-ttu-id="7d327-136">Pomocí této funkce se vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7d327-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="7d327-137">Konstanta</span><span class="sxs-lookup"><span data-stu-id="7d327-137">Constant</span></span>  |<span data-ttu-id="7d327-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7d327-138">Value</span></span>  |<span data-ttu-id="7d327-139">Popis</span><span class="sxs-lookup"><span data-stu-id="7d327-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="7d327-140">0</span><span class="sxs-lookup"><span data-stu-id="7d327-140">0</span></span> | <span data-ttu-id="7d327-141">Volání funkce je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="7d327-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="7d327-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="7d327-142">0xC0000BBD</span></span> | <span data-ttu-id="7d327-143">Požadovaný argument je chybí nebo není správný.</span><span class="sxs-lookup"><span data-stu-id="7d327-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="7d327-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="7d327-144">0xC0000BBC</span></span> | <span data-ttu-id="7d327-145">Popisovač nepředstavuje platný objekt PDH.</span><span class="sxs-lookup"><span data-stu-id="7d327-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7d327-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d327-146">Remarks</span></span>

<span data-ttu-id="7d327-147">Tato funkce zabalí volání [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) funkce.</span><span class="sxs-lookup"><span data-stu-id="7d327-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d327-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d327-148">Requirements</span></span>  
 <span data-ttu-id="7d327-149">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d327-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d327-150">**Knihovna:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="7d327-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="7d327-151">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7d327-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d327-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d327-152">See also</span></span>  
[<span data-ttu-id="7d327-153">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="7d327-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
