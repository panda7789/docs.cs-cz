---
title: Funkce QualifierSet_Next (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_Next načte další kvalifikátor ve výčtu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8b96957467b0acb100f7eea137b3294a60e208a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000191"
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next function
Načte další kvalifikátor ve výčtu, který spustil pomocí volání [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce.   

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
[in] Tento parametr se nepoužívá.

`ptr`   
[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`lFlags`   
[in] Vyhrazená. Tento parametr musí být 0.

`pstrName`   
[out] Název kvalifikátor. Pokud `null`, tento parametr se ignoruje; v opačném případě `pstrName` nesmí odkazovat na platnou `BSTR` nebo nevracení paměti. Pokud není null, funkce vždy přidělí novou `BSTR` při vrácení `WBEM_S_NO_ERROR`.

`pVal`   
[out] V případě úspěchu, hodnota pro kvalifikátor. Pokud funkce selže, `VARIANT` odkazované `pVal` se nezmění. Pokud je tento parametr `null`, tento parametr je ignorován.

`plFlavor`   
[out] Ukazatel, který přijímá charakter kvalifikátoru DLOUHO. Pokud není žádoucí informace charakter, tento parametr může být `null`. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Volající nezavolalo [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici zahájíte nový výčet. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Žádné další kvalifikátory jsou ponechány ve výčtu. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metody.

Volání `QualifierSet_Next` funkce opakovaně k vytvoření výčtu v kvalifikátorech dokud návratová hodnota funkce `WBEM_S_NO_MORE_DATA`. Chcete-li ukončit výčet již v rané fázi, zavolejte [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkce.

Pořadí kvalifikátory vrátil během výčtu není definováno.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
