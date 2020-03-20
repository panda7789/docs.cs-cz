---
title: FormatFromRawValue (Nespravovaný odkaz na rozhraní API)
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
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176835"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="66577-103">Funkce FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="66577-103">FormatFromRawValue function</span></span>
<span data-ttu-id="66577-104">Převede jednu nezpracovaná hodnota dat výkonu na zadaný formát nebo dvě nezpracovaná hodnoty dat výkonu, pokud je převod formátu založen na čase.</span><span class="sxs-lookup"><span data-stu-id="66577-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="66577-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66577-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="66577-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="66577-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="66577-107">[v] Typ čítače.</span><span class="sxs-lookup"><span data-stu-id="66577-107">[in] The counter type.</span></span> <span data-ttu-id="66577-108">Seznam typů čítačů naleznete v tématu [Typy čítačů výkonu služby WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="66577-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="66577-109">`dwCounterType`může být libovolný typ `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`čítače s výjimkou a .</span><span class="sxs-lookup"><span data-stu-id="66577-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="66577-110">[v] Formát, na který chcete převést nezpracovaná data o výkonu.</span><span class="sxs-lookup"><span data-stu-id="66577-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="66577-111">Může to být jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="66577-111">It can be one of the following values:</span></span>

|<span data-ttu-id="66577-112">Trvalé</span><span class="sxs-lookup"><span data-stu-id="66577-112">Constant</span></span>  |<span data-ttu-id="66577-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66577-113">Value</span></span>  |<span data-ttu-id="66577-114">Popis</span><span class="sxs-lookup"><span data-stu-id="66577-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="66577-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="66577-115">0x00000200</span></span> | <span data-ttu-id="66577-116">Vrátí vypočtenou hodnotu jako hodnotu s dvojitou přesností s plovoucí desetinnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="66577-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="66577-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="66577-117">0x00000400</span></span> | <span data-ttu-id="66577-118">Vrátí vypočtenou hodnotu jako 64bitové celé číslo.</span><span class="sxs-lookup"><span data-stu-id="66577-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="66577-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="66577-119">0x00000100</span></span> | <span data-ttu-id="66577-120">Vrátí vypočtenou hodnotu jako 32bitové celé číslo.</span><span class="sxs-lookup"><span data-stu-id="66577-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="66577-121">Jednou z předchozích hodnot může být ORed s jedním z následujících příznaků měřítka:</span><span class="sxs-lookup"><span data-stu-id="66577-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="66577-122">Trvalé</span><span class="sxs-lookup"><span data-stu-id="66577-122">Constant</span></span>  |<span data-ttu-id="66577-123">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66577-123">Value</span></span>  |<span data-ttu-id="66577-124">Popis</span><span class="sxs-lookup"><span data-stu-id="66577-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="66577-125">0x000010000</span><span class="sxs-lookup"><span data-stu-id="66577-125">0x00001000</span></span> | <span data-ttu-id="66577-126">Nepoužívejte faktory měřítka čítače.</span><span class="sxs-lookup"><span data-stu-id="66577-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="66577-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="66577-127">0x00002000</span></span> | <span data-ttu-id="66577-128">Konečnou hodnotu vynásobte hodnotou 1 000.</span><span class="sxs-lookup"><span data-stu-id="66577-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="66577-129">[v] Ukazatel na časovou základnu, pokud je to nutné pro převod formátu.</span><span class="sxs-lookup"><span data-stu-id="66577-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="66577-130">Pokud informace o základu času není nutné pro převod formátu, hodnota tohoto parametru je ignorována.</span><span class="sxs-lookup"><span data-stu-id="66577-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="66577-131">[v] Ukazatel na [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) strukturu, která představuje hodnotu nezpracovaného výkonu.</span><span class="sxs-lookup"><span data-stu-id="66577-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="66577-132">[v] Ukazatel na [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) strukturu, která představuje druhou hodnotu nezpracovaného výkonu.</span><span class="sxs-lookup"><span data-stu-id="66577-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="66577-133">Pokud druhá nezpracovaná hodnota výkonu není `null`nutná, měl by být tento parametr .</span><span class="sxs-lookup"><span data-stu-id="66577-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="66577-134">[out] Ukazatel na [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) strukturu, která obdrží formátovanou hodnotu výkonu.</span><span class="sxs-lookup"><span data-stu-id="66577-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="66577-135">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66577-135">Return value</span></span>

<span data-ttu-id="66577-136">Tato funkce vrací následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="66577-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="66577-137">Trvalé</span><span class="sxs-lookup"><span data-stu-id="66577-137">Constant</span></span>  |<span data-ttu-id="66577-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66577-138">Value</span></span>  |<span data-ttu-id="66577-139">Popis</span><span class="sxs-lookup"><span data-stu-id="66577-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="66577-140">0</span><span class="sxs-lookup"><span data-stu-id="66577-140">0</span></span> | <span data-ttu-id="66577-141">Volání funkce je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="66577-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="66577-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="66577-142">0xC0000BBD</span></span> | <span data-ttu-id="66577-143">Požadovaný argument chybí nebo je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="66577-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="66577-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="66577-144">0xC0000BBC</span></span> | <span data-ttu-id="66577-145">Popisovač není platný objekt PDH.</span><span class="sxs-lookup"><span data-stu-id="66577-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="66577-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66577-146">Remarks</span></span>

<span data-ttu-id="66577-147">Tato funkce zabalí volání [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) funkce.</span><span class="sxs-lookup"><span data-stu-id="66577-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="66577-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66577-148">Requirements</span></span>

 <span data-ttu-id="66577-149">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66577-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="66577-150">**Knihovna:** Soubor PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="66577-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="66577-151">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66577-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="66577-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="66577-152">See also</span></span>

- [<span data-ttu-id="66577-153">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="66577-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
