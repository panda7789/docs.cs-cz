---
title: Funkce GetNames (Nespravovaný odkaz na rozhraní API)
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174950"
---
# <a name="getnames-function"></a>Funkce GetNames
Načte podmnožinu nebo všechny názvy vlastností objektu.

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
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszQualifierName`  
[v] Ukazatel na platný, `LPCWSTR` který určuje název kvalifikátoru, který funguje jako součást filtru. Další informace naleznete v části [Poznámky.](#remarks) Tento parametr `null`může být .

`lFlags`  
[v] Kombinace bitových polí. Další informace naleznete v části [Poznámky.](#remarks)

`pQualifierValue`[v] Ukazatel na platnou `VARIANT` strukturu inicializovanou na hodnotu filtru. Tento parametr `null`může být .

`pstrNames`  
[out] Struktura, `SAFEARRAY` která obsahuje názvy vlastností. Při zadávání musí být tento parametr `null`vždy ukazatelem . Další informace naleznete v části [Poznámky.](#remarks)

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecnému selhání. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů není platné nebo byla zadána nesprávná kombinace příznaků a parametrů. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení operace není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::GetNames.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)

Pojmenované vrácené jsou řízeny kombinací příznaků a parametrů. Funkce může například vrátit názvy všech vlastností nebo pouze názvy vlastností klíče.  Primární filtr je určen `lFlags` v parametru a ostatní parametry se liší v závislosti na něm.

Hodnoty příznaku `lFlags` v jsou bitová pole

Příznaky, které mohou být `lEnumFlags` předány jako argument jsou bitová pole, které jsou definovány v souboru hlavičky *WbemCli.h,* nebo je můžete definovat jako konstanty v kódu.  Můžete kombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny. Příznaky ze stejné skupiny se však vzájemně vylučují.

| Příznaky skupiny 1 |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Vrátí všechny názvy vlastností. `strQualifierName`a `pQualifierVal` jsou nevyužity. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Vrátí pouze vlastnosti, které mají kvalifikátor názvu určeného parametrem. `strQualifierName` Pokud je tento příznak použit, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Vrátí pouze vlastnosti, které nemají kvalifikátor názvu určeného parametrem. `strQualifierName` Pokud je tento příznak použit, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Vrátí pouze vlastnosti, které mají kvalifikátor názvu určeného `wszQualifierName` parametrem `pQualifierVal` a mají také hodnotu shodnou s hodnotou určenou strukturou. Pokud je tento příznak použit, `wszQualifierName` je `pQualifierValue`nutné zadat a a . |

| Příznaky skupiny 2 |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Vrátí pouze názvy vlastností, které definují klíče. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Vrátí pouze názvy vlastností, které jsou odkazy na objekty. |

| Příznaky skupiny 3 |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátí pouze názvy vlastností, které patří do nejvíce odvozené třídy. Vyloučit vlastnosti z nadřazených tříd. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Vrátí pouze názvy vlastností, které patří do nadřazených tříd. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Vrátí pouze názvy vlastností systému. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Vrátí pouze názvy nesystémových vlastností. |

Funkce vždy přiděluje nový, `SAFEARRAY` pokud se vrátí `WBEM_S_NO_ERROR`a `pstrNames` je vždy nastavena na odkaz. Vrácené pole může mít 0 prvků, pokud žádné vlastnosti neodpovídají zadaným filtrům. Pokud funkce vrátí jinou `WBM_S_NO_ERROR`hodnotu `SAFEARRAY` než , není vrácena nová struktura.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
