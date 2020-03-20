---
title: Funkce GetCurrentApartmentType (Nespravovaný odkaz na rozhraní API)
description: Funkce GetCurrentApartmentType načte typ apartment, ve kterém volající provádí.
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176822"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType
Načte typ apartment, ve kterém volající provádí.
  
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
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)

`aptType`  
[out] Ukazatel na hodnotu výčtu [APTTYPE,](/windows/win32/api/objidlbase/ne-objidlbase-apttype) která označuje apartment volajícího.

## <a name="return-value"></a>Návratová hodnota

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `S_OK` | 0 | Funkce byla úspěšně dokončena. |
| `E_FAIL` | 0x80000008 | Volající není provádění v bytě. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [metody IComThreadingInfo::GetCurrentApartmentType.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
