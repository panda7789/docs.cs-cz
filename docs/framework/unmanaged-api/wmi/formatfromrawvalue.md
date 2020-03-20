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
# <a name="formatfromrawvalue-function"></a>Funkce FormatFromRawValue
Převede jednu nezpracovaná hodnota dat výkonu na zadaný formát nebo dvě nezpracovaná hodnoty dat výkonu, pokud je převod formátu založen na čase.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

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

## <a name="parameters"></a>Parametry

`dwCounterType`\
[v] Typ čítače. Seznam typů čítačů naleznete v tématu [Typy čítačů výkonu služby WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType`může být libovolný typ `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`čítače s výjimkou a .

`dwFormat`\
[v] Formát, na který chcete převést nezpracovaná data o výkonu. Může to být jedna z následujících hodnot:

|Trvalé  |Hodnota  |Popis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Vrátí vypočtenou hodnotu jako hodnotu s dvojitou přesností s plovoucí desetinnou hodnotou. |
| `PDH_FMT_LARGE` | 0x00000400 | Vrátí vypočtenou hodnotu jako 64bitové celé číslo. |
| `PDH_FMT_LONG` | 0x00000100 | Vrátí vypočtenou hodnotu jako 32bitové celé číslo. |

Jednou z předchozích hodnot může být ORed s jedním z následujících příznaků měřítka:

|Trvalé  |Hodnota  |Popis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x000010000 | Nepoužívejte faktory měřítka čítače. |
| `PDH_FMT_1000` | 0x00002000 | Konečnou hodnotu vynásobte hodnotou 1 000. |

`pTimeBase`\
[v] Ukazatel na časovou základnu, pokud je to nutné pro převod formátu. Pokud informace o základu času není nutné pro převod formátu, hodnota tohoto parametru je ignorována.

`pRawValue1`\
[v] Ukazatel na [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) strukturu, která představuje hodnotu nezpracovaného výkonu.

`pRawValue2`\
[v] Ukazatel na [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) strukturu, která představuje druhou hodnotu nezpracovaného výkonu. Pokud druhá nezpracovaná hodnota výkonu není `null`nutná, měl by být tento parametr .

`pFmtValue`\
[out] Ukazatel na [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) strukturu, která obdrží formátovanou hodnotu výkonu.

## <a name="return-value"></a>Návratová hodnota

Tato funkce vrací následující hodnoty:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Volání funkce je úspěšné. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Požadovaný argument chybí nebo je nesprávný. |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Popisovač není platný objekt PDH. |

## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) funkce.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).

 **Knihovna:** Soubor PerfCounter.dll

 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
