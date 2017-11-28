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
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue – funkce
Převede jednu hodnotu hrubý výkon při zpracování dat pro zadaný formát nebo dvě hodnoty hrubý výkon při zpracování dat, pokud převod formátu je založené na čase.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
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

## <a name="parameters"></a>Parametry

`dwCounterType`  
[v] Typ čítače. Seznam typů čítač najdete v tématu [typy čítače výkonu rozhraní WMI](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx). `dwCounterType`mohou být jakéhokoli typu čítač s výjimkou `PERF_LARGE_RAW_FRACTION` a `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[v] Formát, do kterého se mají převést data hrubý výkon. Může být jedna z následujících hodnot:

|Konstanta  |Hodnota  |Popis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Vrátí počítanou hodnotu jako hodnotu s plovoucí desetinnou dvojitou přesností. | 
| `PDH_FMT_LARGE` | 0x00000400 | Vrátí počítanou hodnotu jako 64bitové celé číslo. |
| `PDH_FMT_LONG` | 0x00000100 | Vrátí počítanou hodnotu jako 32bitové celé číslo. |

Sloučeny pomocí operátoru OR s jedním z následujících příznaků škálování může být jeden z předchozí hodnot:

|Konstanta  |Hodnota  |Popis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Neplatí škálování faktory čítače. |
| `PDH_FMT_1000` | 0x00002000 | Vynásobte konečná hodnota 1 000. | 

`pTimeBase`  
[v] Ukazatel na základní doba, v případě potřeby pro převod formátu. Pokud není čas základní informace potřebné pro převod formátu, hodnota tohoto parametru je ignorována.

`pRawValue1`[v] Ukazatel [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) struktura, která reprezentuje hodnotu hrubý výkon.

`pRawValue2`[v] Ukazatel [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) struktura, která reprezentuje hodnotu druhý hrubý výkon. Pokud je druhá hodnota hrubý výkon při zpracování je nezbytné, tento parametr by měl být `null`.

`pFmtValue`[out] Ukazatel [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) struktura, která přijímá hodnota formátovaný výkonu.

## <a name="return-value"></a>Návratová hodnota

Pomocí této funkce se vrátí následující hodnoty:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Volání funkce je úspěšné. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Požadovaný argument je chybí nebo není správný. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Popisovač nepředstavuje platný objekt PDH. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Knihovna:** PerfCounter.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
