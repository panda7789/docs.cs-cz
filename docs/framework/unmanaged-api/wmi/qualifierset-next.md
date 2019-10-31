---
title: QualifierSet_Next – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: c9c824b0158618848c13183d92f88604460d5099
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141721"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next – funkce
Načte další kvalifikátor ve výčtu, který začal voláním funkce [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
pro Tento parametr se nepoužívá.

`ptr`   
pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`   
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`pstrName`   
mimo Název kvalifikátoru. Pokud `null`, tento parametr je ignorován. v opačném případě by `pstrName` neměla ukazovat na platný `BSTR` nebo dojde k nevrácení paměti. Pokud hodnota není null, funkce vždy přidělí novou `BSTR`, když vrátí `WBEM_S_NO_ERROR`.

`pVal`   
mimo Pokud je to úspěšné, hodnota kvalifikátoru. Pokud se funkce nezdařila, `VARIANT`, na kterou odkazuje `pVal`, se nezmění. Pokud je tento parametr `null`, parametr je ignorován.

`plFlavor`   
mimo Ukazatel na dlouhou hodnotu, který získá charakter kvalifikátoru. Pokud nejsou požadovány informace o charakteru, lze tento parametr `null`. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Volající nevolal [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Ve výčtu nezůstanou žádné další kvalifikátory. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) .

Voláním funkce `QualifierSet_Next` opakovaně vydáte výčet všech kvalifikátorů, dokud funkce nevrátí `WBEM_S_NO_MORE_DATA`. Chcete-li ukončit výčet na začátku, zavolejte funkci [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) .

Pořadí kvalifikátorů vrácených během výčtu není definováno.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
