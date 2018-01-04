---
title: "Funkce NextMethod (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce NextMethod načte další metoda ve výčtu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: NextMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: NextMethod
helpviewer_keywords: NextMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b886b3ecbd1d5b5b8d212846b2bd8291fa43909
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="nextmethod-function"></a>NextMethod – funkce
Načte metodu další v výčet, který začíná volání [BeginMethodEnumeration](beginmethodenumeration.md).  

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
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`pName`  
[out] Ukazatele, který odkazuje na `null` před voláním. Když funkce vrátí hodnotu, na novou adresu `BSTR` obsahující název metody. 

`ppSignatureIn`  
[out] Ukazatele, který obdrží ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) obsahující `in` parametry pro metodu. 

`ppSignatureOut`  
[out] Ukazatele, který obdrží ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) obsahující `out` parametry pro metodu. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Byl bez volání [ `BeginEnumeration` ](beginenumeration.md) funkce. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Ve výčtu nejsou žádné další vlastnosti. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) metoda.

Volající začne pořadí výčtu voláním [BeginMethodEnumeration](beginmethodenumeration.md) fungovat a pak zavolá funkci [NextMethod], dokud funkce vrátí hodnotu `WBEM_S_NO_MORE_DATA`. Volitelně volající dokončení sekvenci voláním [EndMethodEnumeration](endmethodenumeration.md). Volající ukončovat výčtu již v rané fázi voláním [EndMethodEnumeration](endmethodenumeration.md) kdykoli.

## <a name="example"></a>Příklad

Příklad, C++, najdete v článku [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) metoda.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
