---
title: Funkce NextMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce NextMethod načte další metody ve výčtu.
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
ms.openlocfilehash: 2ebe6924dfe1a4aa640ef8ccd7b4047c1d137948
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640040"
---
# <a name="nextmethod-function"></a>NextMethod – funkce
Načte další metody ve výčtu, která začíná volání [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Vyhrazená. Tento parametr musí být 0.

`pName`  
[out] Ukazatel, který odkazuje na `null` před voláním. Pokud funkce vrátí, adresa nového `BSTR` obsahující název metody. 

`ppSignatureIn`  
[out] Ukazatel, který přijímá ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `in` parametrů metody. 

`ppSignatureOut`  
[out] Ukazatel, který přijímá ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `out` parametrů metody. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Došlo bez volání [ `BeginEnumeration` ](beginenumeration.md) funkce. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nejsou žádné další vlastnosti ve výčtu. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.

Volající začne pořadí výčtu voláním [BeginMethodEnumeration](beginmethodenumeration.md) pracovat a pak volá funkci [NextMethod], dokud se funkce vrátí `WBEM_S_NO_MORE_DATA`. Volitelně můžete volající dokončení sekvence pomocí volání [EndMethodEnumeration](endmethodenumeration.md). Volající může již v rané fázi ukončit výčtu voláním [EndMethodEnumeration](endmethodenumeration.md) kdykoli.

## <a name="example"></a>Příklad

Příklad C++, naleznete v tématu [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:
- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
