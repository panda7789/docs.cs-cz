---
title: Odstranit funkci (referenční dokumentace nespravovaného rozhraní API)
description: Funkce Delete Odstraní zadané vlastnosti a všechny jeho kvalifikátory z definice třídy CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 791e75aa60fd651dde1555339e31664a3523e1eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046224"
---
# <a name="delete-function"></a>Odstranit funkci
Odstraní zadanou vlastnost a všechny jeho kvalifikátory z definice třídy CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszName`  
[in] Název vlastnosti, která má odstranit. `wszName` musí být ukazatel na platný `LPCWSTR`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k nespecifikované chybě. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Vlastnost nelze odstranit. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Formát  `wszzName` je neplatný. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Není k dispozici dostatek paměti k dokončení operace. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Vlastnost se dědí ze základní třídy. |
| `WBEM_E_SYSTEM_PROPERTY` | | Vlastnost je vlastnost systému. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | Funkce odstranit výchozí hodnotu pro aktuální třídu. Výchozí hodnota této vlastnosti v nadřazené třídě byl reactiviated. | 

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) metody.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
