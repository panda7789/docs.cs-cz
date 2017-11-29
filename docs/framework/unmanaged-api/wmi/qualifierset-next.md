---
title: "Funkce QualifierSet_Next (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_Next načte další kvalifikátor ve výčtu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Next
helpviewer_keywords: QualifierSet_Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b66eeab2cba18268b602350c8bc8f489d943309
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next – funkce
Načte další kvalifikátor v výčet, který je spuštěn s volání [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce.   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[v] Tento parametr se nepoužívá.

`ptr`   
[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`lFlags`   
[v] Vyhrazena. Tento parametr musí být 0.

`pstrName`   
[out] Název kvalifikátor. Pokud `null`, tento parametr je ignorováno, jinak hodnota `pstrName` by neměl přejděte na platnou `BSTR` nebo nevrací paměť. Pokud není null, funkce vždy přiděluje nový `BSTR` při vrácení `WBEM_S_NO_ERROR`.

`pVal`   
[out] Po úspěšné, hodnota kvalifikátor. Pokud se funkce nezdaří, `VARIANT` na kterou odkazuje `pVal` se nemění. Pokud tento parametr je `null`, parametr je ignorován.

`plFlavor`   
[out] Ukazatel na typ LONG, která přijímá charakter kvalifikátoru. V případě potřeby příchuť informace není tento parametr může být `null`. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Volající nezavolalo [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici zahájíte nové – výčet není dostatek paměti. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Ve výčtu nezbývají žádné další kvalifikátory. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) metoda.

Volání `QualifierSet_Next` funkce opakovaně se vytvořit výčet všech kvalifikátory dokud návratový funkce `WBEM_S_NO_MORE_DATA`. Chcete-li ukončit výčtu již v rané fázi, volejte [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkce.

Pořadí kvalifikátory vrátil během výčtu není definován.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
