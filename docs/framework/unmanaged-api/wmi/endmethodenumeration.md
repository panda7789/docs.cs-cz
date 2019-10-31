---
title: EndMethodEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce EndMethodEnumeration ukončí sekvenci výčtu metody.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 174cf76d4b0ddf07e67e02bff20a983dca08819a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132023"
---
# <a name="endmethodenumeration-function"></a>Funkce EndMethodEnumeration
Ukončí sekvenci výčtu spuštěnou voláním [funkce BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101d | Došlo k vnitřní chybě. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) .

Volající zahájí sekvenci výčtu pomocí [funkce BeginMethodEnumeration](beginmethodenumeration.md)a poté zavolá [funkci NextMethod](nextmethod.md ), dokud metoda nevrátí `WBEM_S_NO_MORE_DATA`. Volající volitelně dokončí sekvenci voláním `EndMethodEnumeration`. Volající může ukončit výčet hned po volání `EndMethodEnumeration` kdykoli.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
