---
title: Funkce EndMethodEnumeration (Nespravovaný odkaz rozhraní API)
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
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175002"
---
# <a name="endmethodenumeration-function"></a>Funkce EndMethodEnumeration
Ukončí posloupnost výčtu spuštěnou voláním [funkce BeginMethodEnumeration .](beginmethodenumeration.md)  

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
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101d | Došlo k vnitřní chybě. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::EndMethodEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)

Volající zahájí posloupnost výčtu pomocí [funkce BeginMethodEnumeration a](beginmethodenumeration.md)potom zavolá `WBEM_S_NO_MORE_DATA`funkci [NextMethod,](nextmethod.md )dokud metoda nevrátí . Volající volitelně dokončí pořadí voláním `EndMethodEnumeration`. Volající může ukončit výčtu `EndMethodEnumeration` brzy voláním kdykoli.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
