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
ms.openlocfilehash: 47f92122eddf3cc8e6aec19d75fd2a95f76e9973
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746706"
---
# <a name="formatfromrawvalue-function"></a>Funkce FormatFromRawValue
Převede jednu hodnotu hrubý výkon při zpracování dat pro zadaný formát nebo dvě hodnoty hrubý výkon při zpracování dat, pokud převod formátu podle času. 

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
[in] Typ čítače. Seznam typů čítačů najdete v tématu [typů čítačů výkonu služby WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` může být libovolný typ čítače s výjimkou `PERF_LARGE_RAW_FRACTION` a `PERF_LARGE_RAW_BASE`. 

`dwFormat`\
[in] Formát, do které chcete převést hrubá data. Může být jeden z následujících hodnot:

|Konstanta  |Value  |Popis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Vrátí počítanou hodnotu jako hodnotu s plovoucí desetinnou dvojitou přesností. | 
| `PDH_FMT_LARGE` | 0x00000400 | Počítané hodnoty lze vrátíte jako 64bitové celé číslo. |
| `PDH_FMT_LONG` | 0x00000100 | Vrátí počítané hodnoty jako 32bitové celé číslo. |

Použijte některou z předchozích hodnot mohou být sloučeny pomocí operátoru OR s jedním z následujících příznaků škálování:

|Konstanta  |Hodnota  |Popis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Nevztahují se čítač faktory měřítka. |
| `PDH_FMT_1000` | 0x00002000 | Vynásobte konečnou hodnotu 1000. | 

`pTimeBase`\
[in] Ukazatel na základní čas, pokud je to nutné pro převod formátu. Pokud základní informace o čase není nezbytné pro převod formátu, hodnota tohoto parametru je ignorována.

`pRawValue1`\ [in] ukazatel [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) struktura, která představuje hodnotu hrubého výkonu.

`pRawValue2`\
[in] Ukazatel [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) struktura, která představuje hodnotu druhého hrubého výkonu. Pokud druhá hodnota hrubého výkonu není nezbytné, tento parametr by měl být `null`.

`pFmtValue`\
[out] Ukazatel [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) struktura, která přijímá hodnotu formátovaný výkonu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty jsou vráceny pomocí této funkce:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Volání funkce je úspěšné. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Požadovaný argument je chybí nebo není správný. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Popisovač není platný objekt PDH. |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) funkce.

## <a name="requirements"></a>Požadavky

 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Knihovna:** PerfCounter.dll

 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
