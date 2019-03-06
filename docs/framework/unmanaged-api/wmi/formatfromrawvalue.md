---
title: Funkce FormatFromRawValue (referenční dokumentace nespravovaného rozhraní API)
description: Funkce FormatFromRawValue převede nezpracovaných dat výkonu do zadaného formátu.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bef18468ef02e37b857316cd9fa2bf4cf5f9e9b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369330"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="bb7eb-103">Funkce FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="bb7eb-103">FormatFromRawValue function</span></span>
<span data-ttu-id="bb7eb-104">Převede jednu hodnotu hrubý výkon při zpracování dat pro zadaný formát nebo dvě hodnoty hrubý výkon při zpracování dat, pokud převod formátu podle času.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bb7eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb7eb-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="bb7eb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb7eb-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="bb7eb-107">[in] Typ čítače.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-107">[in] The counter type.</span></span> <span data-ttu-id="bb7eb-108">Seznam typů čítačů najdete v tématu [typů čítačů výkonu služby WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="bb7eb-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="bb7eb-109">`dwCounterType` může být libovolný typ čítače s výjimkou `PERF_LARGE_RAW_FRACTION` a `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="bb7eb-110">[in] Formát, do které chcete převést hrubá data.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="bb7eb-111">Může být jeden z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="bb7eb-111">It can be one of the following values:</span></span>

|<span data-ttu-id="bb7eb-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bb7eb-112">Constant</span></span>  |<span data-ttu-id="bb7eb-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bb7eb-113">Value</span></span>  |<span data-ttu-id="bb7eb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bb7eb-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="bb7eb-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="bb7eb-115">0x00000200</span></span> | <span data-ttu-id="bb7eb-116">Vrátí počítanou hodnotu jako hodnotu s plovoucí desetinnou dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="bb7eb-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="bb7eb-117">0x00000400</span></span> | <span data-ttu-id="bb7eb-118">Počítané hodnoty lze vrátíte jako 64bitové celé číslo.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="bb7eb-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="bb7eb-119">0x00000100</span></span> | <span data-ttu-id="bb7eb-120">Vrátí počítané hodnoty jako 32bitové celé číslo.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="bb7eb-121">Použijte některou z předchozích hodnot mohou být sloučeny pomocí operátoru OR s jedním z následujících příznaků škálování:</span><span class="sxs-lookup"><span data-stu-id="bb7eb-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="bb7eb-122">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bb7eb-122">Constant</span></span>  |<span data-ttu-id="bb7eb-123">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bb7eb-123">Value</span></span>  |<span data-ttu-id="bb7eb-124">Popis</span><span class="sxs-lookup"><span data-stu-id="bb7eb-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="bb7eb-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="bb7eb-125">0x00001000</span></span> | <span data-ttu-id="bb7eb-126">Nevztahují se čítač faktory měřítka.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="bb7eb-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="bb7eb-127">0x00002000</span></span> | <span data-ttu-id="bb7eb-128">Vynásobte konečnou hodnotu 1000.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="bb7eb-129">[in] Ukazatel na základní čas, pokud je to nutné pro převod formátu.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="bb7eb-130">Pokud základní informace o čase není nezbytné pro převod formátu, hodnota tohoto parametru je ignorována.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="bb7eb-131">`pRawValue1`\ [in] ukazatel [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) struktura, která představuje hodnotu hrubého výkonu.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="bb7eb-132">[in] Ukazatel [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) struktura, která představuje hodnotu druhého hrubého výkonu.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="bb7eb-133">Pokud druhá hodnota hrubého výkonu není nezbytné, tento parametr by měl být `null`.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="bb7eb-134">[out] Ukazatel [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) struktura, která přijímá hodnotu formátovaný výkonu.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb7eb-135">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bb7eb-135">Return value</span></span>

<span data-ttu-id="bb7eb-136">Následující hodnoty jsou vráceny pomocí této funkce:</span><span class="sxs-lookup"><span data-stu-id="bb7eb-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="bb7eb-137">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bb7eb-137">Constant</span></span>  |<span data-ttu-id="bb7eb-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bb7eb-138">Value</span></span>  |<span data-ttu-id="bb7eb-139">Popis</span><span class="sxs-lookup"><span data-stu-id="bb7eb-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="bb7eb-140">0</span><span class="sxs-lookup"><span data-stu-id="bb7eb-140">0</span></span> | <span data-ttu-id="bb7eb-141">Volání funkce je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="bb7eb-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="bb7eb-142">0xC0000BBD</span></span> | <span data-ttu-id="bb7eb-143">Požadovaný argument je chybí nebo není správný.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="bb7eb-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="bb7eb-144">0xC0000BBC</span></span> | <span data-ttu-id="bb7eb-145">Popisovač není platný objekt PDH.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bb7eb-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb7eb-146">Remarks</span></span>

<span data-ttu-id="bb7eb-147">Tato funkce zalamuje volání na [FormatFromRawValue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms231047%28v=vs.85%29) funkce.</span><span class="sxs-lookup"><span data-stu-id="bb7eb-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms231047%28v=vs.85%29) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb7eb-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb7eb-148">Requirements</span></span>

 <span data-ttu-id="bb7eb-149">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb7eb-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bb7eb-150">**Knihovna:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="bb7eb-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="bb7eb-151">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bb7eb-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bb7eb-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb7eb-152">See also</span></span>

- [<span data-ttu-id="bb7eb-153">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bb7eb-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)