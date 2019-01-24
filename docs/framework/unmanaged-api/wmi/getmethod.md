---
title: Funkce GetMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetMethod načte informace o metodě.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a405c5e245558e6b8d1b389bfc143faae4550a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577591"
---
# <a name="getmethod-function"></a>Funkce GetMethod
Načte informace o zadané metodě.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszName`  
[in] Název metody. Tento parametr nemůže mít `null` a musí odkazovat na platný `LPCWSTR`.

`lFlags`  
[in] Vyhrazená. Tento parametr musí být 0.

`ppInSignature`   
[out] Ukazatel na adresu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instanci, která popisuje v paramteers metody. Tento parametr se ignoruje, pokud je nastaveno na `null`. 

`ppOutSignature`  
[out] Ukazatel na adresu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instanci, která popisuje výstupní parametry metody. Tento parametr se ignoruje, pokud je nastaveno na `null`. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost nebyla nalezena. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.

Můžete nastavit správu Windows [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ukazatel na `null` Pokud metoda nemá žádné parametry. v.

V `ppInSignature` a `ppOutSignature` popisují ani výstupní parametry, v uvedeném pořadí, v jako vlastnosti `IWbemClassObject` instance třídy systému [_Parameters](/windows/desktop/WmiSdk/--parameters). Vlastnosti v `ppInsignature` jsou pojmenovány `Param` *n*, kde *n* je pozice parametru v podpisu metody (například `Param1`, `Param2`atd.). Vlastnosti v `ppOutSignature` se také nazývají `Param` *n*, a návratová hodnota se nazývá `ReturnValue`. Další informace a příklad najdete v tématu [IWbemClassObject::GetMethod metoda](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Požadavky  
**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:
- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
