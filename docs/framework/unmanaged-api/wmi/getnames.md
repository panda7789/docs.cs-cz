---
title: GetNames – funkce (odkaz na nespravované rozhraní API)
description: Funkce GetNames načte názvy vlastností objektu.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b03ed6a68fbe288e93dedb4f425f1511563dfeb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102527"
---
# <a name="getnames-function"></a>Funkce GetNames
Načte buď podmnožinu, nebo všechny názvy vlastností objektu. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszQualifierName`  
pro Ukazatel na platný `LPCWSTR`, který určuje název kvalifikátoru, který funguje jako součást filtru. Další informace najdete v části [poznámky](#remarks) . Tento parametr může být `null`. 

`lFlags`  
pro Kombinace bitových polí. Další informace najdete v části [poznámky](#remarks) .

`pQualifierValue`   
pro Ukazatel na platnou strukturu `VARIANT` inicializovaný jako hodnota filtru. Tento parametr může být `null`. 

`pstrNames`  
mimo Struktura `SAFEARRAY`, která obsahuje názvy vlastností. U vstupu musí být tento parametr vždy ukazatelem na `null`. Další informace najdete v části [poznámky](#remarks) . 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů je neplatných nebo byla zadána nesprávná kombinace příznaků a parametrů. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .

Pojmenované vrácené jsou ovládány kombinací příznaků a parametrů. Funkce například může vracet názvy všech vlastností nebo pouze názvy vlastností klíče.  Primární filtr je uveden v parametru `lFlags` a ostatní parametry se liší v závislosti na tom.

Hodnoty příznaku v `lFlags` jsou bitová pole.

Příznaky, které mohou být předány jako argument `lEnumFlags`, jsou bitová pole, která jsou definována v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.  Můžete zkombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny. Příznaky ze stejné skupiny se však vzájemně vylučují. 

| Příznaky skupiny 1 |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0,8 | Vrátí všechny názvy vlastností. `strQualifierName` a `pQualifierVal` se nepoužívá. |
| `WBEM_FLAG_ONLY_IF_TRUE` | první | Vrátí pouze vlastnosti, které mají kvalifikátor názvu určený parametrem `strQualifierName`. Pokud je tento příznak použit, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | odst |  Vrátí pouze vlastnosti, které nemají kvalifikátor názvu určeného parametrem `strQualifierName`. Pokud je tento příznak použit, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Vrátí pouze vlastnosti, které mají kvalifikátor názvu zadaný parametrem `wszQualifierName` a mají také hodnotu shodnou s hodnotou určenou strukturou `pQualifierVal`. Pokud je tento příznak použit, je nutné zadat `wszQualifierName` i `pQualifierValue`. |

| Příznaky skupiny 2 |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Vrátí pouze názvy vlastností, které definují klíče. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Vrátí pouze názvy vlastností, které jsou odkazy na objekty. |

| Příznaky skupiny 3 |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátí pouze názvy vlastností, které patří do nejvyšší odvozené třídy. Vylučte vlastnosti z nadřazených tříd. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Vrátí pouze názvy vlastností, které patří do nadřazených tříd. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Vrátí pouze názvy systémových vlastností. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Vrátí pouze názvy nesystémových vlastností. |

Funkce vždy přidělí nový `SAFEARRAY`, pokud vrátí `WBEM_S_NO_ERROR`a `pstrNames` je vždy nastaven na odkaz. Vrácené pole může mít 0 prvků, pokud žádné vlastnosti neodpovídají zadaným filtrům. Vrátí-li funkce jinou hodnotu než `WBM_S_NO_ERROR`, nevrátí se nová struktura `SAFEARRAY`.
 
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
