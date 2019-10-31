---
title: QualifierSet_Get – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_Get Získá pojmenovaný kvalifikátor.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: dc09cd30c43647fa00cccc1dc00da4f8de367e84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127276"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get – funkce
Získá zadaný pojmenovaný kvalifikátor.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
pro Tento parametr se nepoužívá.

`ptr`   
pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`   
pro Název kvalifikátoru, jehož hodnota je požadována.

`lFlags`   
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`pVal`   
mimo Pokud je to úspěšné, správný typ a hodnotu kvalifikátoru. Pokud se funkce nezdařila, `VARIANT`, na kterou odkazuje `pVal`, se nezmění. Pokud je tento parametr `null`, parametr je ignorován.

`plFlavor`   
mimo Ukazatel na dlouhou dobu, který obdrží kvalifikátor charakteru pro požadovaný kvalifikátor. Pokud nejsou požadovány informace o charakteru, lze tento parametr `null`. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný kvalifikátor neexistuje. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
