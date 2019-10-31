---
title: GetCurrentApartmentType – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetCurrentApartmentType načte typ objektu apartment, ve kterém je volající spuštěn.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6ecd2b49d6850a8fae25ddca54f855fdda2ccabb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120354"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType – funkce
Načte typ objektu apartment, ve kterém je volající spuštěn.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .

`aptType`  
mimo Ukazatel na hodnotu výčtu [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) , která označuje objekt Apartment volajícího.

## <a name="return-value"></a>Návratová hodnota

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `S_OK` | 0,8 | Funkce byla úspěšně dokončena. |
| `E_FAIL` | 0x80000008 | Volající není spuštěn v objektu apartment. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
