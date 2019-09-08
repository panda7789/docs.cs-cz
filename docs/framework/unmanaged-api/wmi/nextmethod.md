---
title: NextMethod – funkce (Reference nespravovaného rozhraní API)
description: Funkce NextMethod načte další metodu ve výčtu.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee743a4499824bea723043d5a2c7d57d7cbd7106
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798431"
---
# <a name="nextmethod-function"></a>NextMethod – funkce
Načte další metodu ve výčtu, který začíná voláním [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`pName`  
mimo Ukazatel, na `null` který odkazuje před voláním. Když se funkce vrátí, adresa nového `BSTR` obsahující název metody. 

`ppSignatureIn`  
mimo Ukazatel, který obdrží ukazatel na [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `in` parametry pro metodu. 

`ppSignatureOut`  
mimo Ukazatel, který obdrží ukazatel na [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `out` parametry pro metodu. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | [`BeginEnumeration`](beginenumeration.md) Funkci se nevolalo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Ve výčtu nejsou žádné další vlastnosti. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .

Volající zahájí sekvenci výčtu voláním funkce [BeginMethodEnumeration](beginmethodenumeration.md) a poté zavolá funkci [NextMethod], dokud funkce nevrátí `WBEM_S_NO_MORE_DATA`. Volitelně volající sekvenci dokončí voláním [EndMethodEnumeration](endmethodenumeration.md). Volající může ukončit výčet na začátku voláním [EndMethodEnumeration](endmethodenumeration.md) v každém okamžiku.

## <a name="example"></a>Příklad

C++ Příklad naleznete v tématu metoda [IWbemclassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
