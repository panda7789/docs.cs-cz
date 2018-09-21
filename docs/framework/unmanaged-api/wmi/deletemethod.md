---
title: Funkce DeleteMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce DeleteMethod odstraní zadanou metodu z definice třídy CIM.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5996ce41c80cb54c4fcb9104c2993c85bcc2b466
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46526468"
---
# <a name="deletemethod-function"></a>Funkce DeleteMethod
Odstraní zadanou metodu z definice třídy CIM.

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
[in] Název metody, která odebere z tabulky třídy. `wszName` musí být ukazatel na platný `LPCWSTR`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná metoda neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Není k dispozici dostatek paměti k dokončení operace. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) metody.

Metoda odstranění není podporováno pro [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ukazatele, které odkazují na instance CIM.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
