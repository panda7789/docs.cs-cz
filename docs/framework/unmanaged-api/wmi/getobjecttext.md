---
title: GetObjectText – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetObjectText vrací textové vykreslování objektu v syntaxi MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102456"
---
# <a name="getobjecttext-function"></a>Funkce GetObjectText
Vrátí textové vykreslování objektu v syntaxi formát MOF (Managed Object Format) (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
pro Normálně 0. Jsou-li zadány `WBEM_FLAG_NO_FLAVORS` (nebo 0x1), jsou kvalifikátory zahrnuty bez informací o šíření nebo charakteru.

`pstrObjectText`   
mimo Ukazatel na `null` na vstupu. Při návratu se nově přidělená `BSTR`, která obsahuje vykreslování syntaxe MOF objektu.  

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) .

Vrácený text MOF neobsahuje všechny informace o objektu, ale pouze dostatek informací pro kompilátor MOF, aby bylo možné znovu vytvořit původní objekt. Například nejsou zahrnuty žádné šířené vlastnosti kvalifikátorů nebo nadřazené třídy.

Následující algoritmus slouží k rekonstrukci textu parametrů metody:

1. Parametry se přesekvencují v pořadí jejich hodnot identifikátorů.
1. Parametry, které jsou zadány jako `[in]` a `[out]` jsou zkombinovány do jednoho parametru.
 
`pstrObjectText` musí být ukazatel na `null` při volání funkce. nesmí ukazovat na řetězec, který je platný před voláním metody, protože ukazatel nebude navrácen.

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
