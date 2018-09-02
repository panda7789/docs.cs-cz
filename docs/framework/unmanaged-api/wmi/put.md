---
title: PUT – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce Put přiřadí novou hodnotu s názvem vlastnosti.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec8fe889885b555cbf9a95cd34b7330efff27f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43460982"
---
# <a name="put-function"></a>PUT – funkce
Pojmenovanou vlastnost nastaví na novou hodnotu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszName`  
[in] Název vlastnosti. Tento parametr nemůže mít `null`.

`lFlags`  
[in] Vyhrazená. Tento parametr musí být 0.

`pVal`   
[in] Ukazatel na platný `VARIANT` , který se stane hodnota nové vlastnosti. Pokud `pVal` je `null` nebo odkazuje `VARIANT` typu `VT_NULL`, je nastavena na `null`. 

`vtType`  
[in] Typ `VARIANT` odkazované `pVal`. Zobrazit [poznámky](#remarks) části Další informace.
 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Typ vlastnosti nebyl rozpoznán. Tato hodnota se vrátí při vytváření instance třídy, pokud třída již existuje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Pro instance: označuje, že `pVal` odkazuje `VARIANT` nesprávného typu pro vlastnost. <br/> Definice třídy: vlastnost již existuje v nadřazené třídě a nový typ modelu COM se liší od původní modelu COM typu. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.

Tato funkce vždy přepíše aktuální hodnota vlastnosti nové. Pokud [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na definici třídy `Put` vytvoří nebo aktualizuje hodnotu vlastnosti. Když [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na instanci CIM `Put` aktualizuje hodnotu vlastnosti. `Put` nelze vytvořit hodnotu vlastnosti.

`__CLASS` Vlastnost systému zapisovatelnou pouze při vytváření třídy, když ji nemůže být ponecháno prázdné. Všechny ostatní vlastnosti systému jsou jen pro čtení.

Uživatele nelze vytvořit vlastnosti s názvy, které začínat ani končit znakem podtržítka ("_"). To je vyhrazen pro systémové třídy a vlastnosti.

Pokud vlastnost nastavil `Put` funkce existuje v nadřazené třídě, výchozí hodnota vlastnosti je změnit, dokud se tento typ vlastnosti neodpovídá typu nadřazené třídy. Pokud vlastnost neexistuje a není v případě nesouladu typů, je vlastnost ceated.

Použití `vtType` parametr jenom při vytvoření nové vlastnosti v definici třídy CIM a `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`. V takovém případě `vType` parametr určuje typ CIM vlastnosti. V každém případě `vtType` musí být 0. `vtType` musí také být 0, pokud je podkladový objekt instancí (i v případě `Val` je `null`) vzhledem k tomu, že typ vlastnosti je pevná a nedá se změnit.   

## <a name="example"></a>Příklad

Příklad najdete v tématu [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
