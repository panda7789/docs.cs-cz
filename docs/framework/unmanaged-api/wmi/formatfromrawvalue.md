---
title: FormatFromRawValue – funkce (Reference nespravovaného rozhraní API)
description: Funkce FormatFromRawValue převede nezpracovaná data výkonu do určeného formátu.
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
ms.openlocfilehash: 5097cfe43ae785461a1e2af1217bcbd5e8c4b79c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120290"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="9cefb-103">Funkce FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="9cefb-103">FormatFromRawValue function</span></span>
<span data-ttu-id="9cefb-104">Převede jednu nezpracovaná hodnota dat výkonu na určený formát nebo dvě nezpracované hodnoty dat výkonu, pokud je převod formátu založený na čase.</span><span class="sxs-lookup"><span data-stu-id="9cefb-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9cefb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cefb-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a><span data-ttu-id="9cefb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cefb-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="9cefb-107">pro Typ čítače.</span><span class="sxs-lookup"><span data-stu-id="9cefb-107">[in] The counter type.</span></span> <span data-ttu-id="9cefb-108">Seznam typů čítačů najdete v tématu [typy čítačů výkonu služby WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="9cefb-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="9cefb-109">`dwCounterType` může být jakýkoli typ čítače s výjimkou `PERF_LARGE_RAW_FRACTION` a `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="9cefb-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="9cefb-110">pro Formát, ve kterém mají být převedena nezpracovaná data výkonu.</span><span class="sxs-lookup"><span data-stu-id="9cefb-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="9cefb-111">Může to být jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="9cefb-111">It can be one of the following values:</span></span>

|<span data-ttu-id="9cefb-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9cefb-112">Constant</span></span>  |<span data-ttu-id="9cefb-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9cefb-113">Value</span></span>  |<span data-ttu-id="9cefb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9cefb-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="9cefb-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="9cefb-115">0x00000200</span></span> | <span data-ttu-id="9cefb-116">Vrátí počítanou hodnotu jako hodnotu s dvojitou přesností s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="9cefb-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="9cefb-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="9cefb-117">0x00000400</span></span> | <span data-ttu-id="9cefb-118">Vrátí počítanou hodnotu jako celé číslo 64.</span><span class="sxs-lookup"><span data-stu-id="9cefb-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="9cefb-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="9cefb-119">0x00000100</span></span> | <span data-ttu-id="9cefb-120">Vrátí počítanou hodnotu jako celé číslo 32.</span><span class="sxs-lookup"><span data-stu-id="9cefb-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="9cefb-121">Jedna z předchozích hodnot může být ORed s jedním z následujících příznaků škálování:</span><span class="sxs-lookup"><span data-stu-id="9cefb-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="9cefb-122">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9cefb-122">Constant</span></span>  |<span data-ttu-id="9cefb-123">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9cefb-123">Value</span></span>  |<span data-ttu-id="9cefb-124">Popis</span><span class="sxs-lookup"><span data-stu-id="9cefb-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="9cefb-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="9cefb-125">0x00001000</span></span> | <span data-ttu-id="9cefb-126">Nepoužívejte faktory škálování čítače.</span><span class="sxs-lookup"><span data-stu-id="9cefb-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="9cefb-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="9cefb-127">0x00002000</span></span> | <span data-ttu-id="9cefb-128">Vynásobte konečnou hodnotu hodnotou 1 000.</span><span class="sxs-lookup"><span data-stu-id="9cefb-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="9cefb-129">pro Ukazatel na časový základ, je-li to nutné pro převod formátu.</span><span class="sxs-lookup"><span data-stu-id="9cefb-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="9cefb-130">Pokud informace o časovém základu není pro převod formátu nutná, hodnota tohoto parametru je ignorována.</span><span class="sxs-lookup"><span data-stu-id="9cefb-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="9cefb-131">`pRawValue1`\ [in] ukazatel na strukturu [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) , která představuje nezpracovaný hodnotu výkonu.</span><span class="sxs-lookup"><span data-stu-id="9cefb-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="9cefb-132">pro Ukazatel na strukturu [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) , která představuje druhou hodnotu nezpracovaného výkonu.</span><span class="sxs-lookup"><span data-stu-id="9cefb-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="9cefb-133">Není-li druhá hodnota nezpracovaného výkonu nutná, tento parametr by měl být `null`.</span><span class="sxs-lookup"><span data-stu-id="9cefb-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="9cefb-134">mimo Ukazatel na strukturu [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) , která přijímá naformátovanou hodnotu výkonu.</span><span class="sxs-lookup"><span data-stu-id="9cefb-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="9cefb-135">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9cefb-135">Return value</span></span>

<span data-ttu-id="9cefb-136">Následující hodnoty jsou vráceny touto funkcí:</span><span class="sxs-lookup"><span data-stu-id="9cefb-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="9cefb-137">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9cefb-137">Constant</span></span>  |<span data-ttu-id="9cefb-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9cefb-138">Value</span></span>  |<span data-ttu-id="9cefb-139">Popis</span><span class="sxs-lookup"><span data-stu-id="9cefb-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="9cefb-140">0,8</span><span class="sxs-lookup"><span data-stu-id="9cefb-140">0</span></span> | <span data-ttu-id="9cefb-141">Volání funkce je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9cefb-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="9cefb-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="9cefb-142">0xC0000BBD</span></span> | <span data-ttu-id="9cefb-143">Požadovaný argument chybí nebo není správný.</span><span class="sxs-lookup"><span data-stu-id="9cefb-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="9cefb-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="9cefb-144">0xC0000BBC</span></span> | <span data-ttu-id="9cefb-145">Popisovač není platným objektem PDH.</span><span class="sxs-lookup"><span data-stu-id="9cefb-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9cefb-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cefb-146">Remarks</span></span>

<span data-ttu-id="9cefb-147">Tato funkce zalomí volání funkce [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) .</span><span class="sxs-lookup"><span data-stu-id="9cefb-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9cefb-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cefb-148">Requirements</span></span>

 <span data-ttu-id="9cefb-149">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cefb-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="9cefb-150">**Knihovna:** Dokončení PerfCounter. dll</span><span class="sxs-lookup"><span data-stu-id="9cefb-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="9cefb-151">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9cefb-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9cefb-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cefb-152">See also</span></span>

- [<span data-ttu-id="9cefb-153">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9cefb-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
