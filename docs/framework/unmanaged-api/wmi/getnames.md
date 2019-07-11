---
title: Funkce GetNames (referenční dokumentace nespravovaného rozhraní API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e75bf9aab820216373f2f33fe8aa567f10befcb1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746515"
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
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszQualifierName`  
[in] Ukazatel na platný `LPCWSTR` , který určuje název kvalifikátor, který funguje jako součást filtr. Další informace najdete v tématu [poznámky](#remarks) oddílu. Tento parametr může být `null`. 

`lFlags`  
[in] Kombinací bitových polí. Další informace najdete v tématu [poznámky](#remarks) oddílu.

`pQualifierValue`   
[in] Ukazatel na platný `VARIANT` struktura inicializovány na hodnotu filtru. Tento parametr může být `null`. 

`pstrNames`  
[out] A `SAFEARRAY` strukturu, která obsahuje názvy vlastností. V položce, musí mít tento parametr vždy ukazatel na `null`. Zobrazit [poznámky](#remarks) části Další informace. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné, nebo byl zadán nesprávný kombinace příznaků a parametry. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) metody.

Pojmenované vrátil řízeno pomocí kombinace příznaků a parametry. Funkce může vrátit třeba názvy všech vlastností nebo pouze názvy vlastnosti klíče.  Primární filtru je zadán v `lFlags` parametru a dalších parametrů se liší v závislosti na jeho.

Příznak hodnoty v `lFlags` jsou bitová pole

Příznaky, které mohou být předány jako `lEnumFlags` argument jsou bitová pole, které jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.  Můžete kombinovat jeden příznak z každé skupiny s všechny příznaky z jiné skupiny. Ale příznaky ze stejné skupiny se vzájemně vylučují. 

| Příznaky skupiny 1 |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Vrátí všechny názvy vlastností. `strQualifierName` a `pQualifierVal` nejsou používány. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Vrátit pouze vlastnosti, které mají kvalifikátoru název určený `strQualifierName` parametru. Pokud tento příznak se používá, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Vrátit pouze vlastnosti, které nemají kvalifikátoru název určený `strQualifierName` parametru. Pokud tento příznak se používá, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Vrátit pouze vlastnosti, které mají kvalifikátoru název určený `wszQualifierName` parametr a také mít identické s klíči určenému hodnotu `pQualifierVal` struktury. Pokud tento příznak se používá, je nutné zadat obě `wszQualifierName` a `pQualifierValue`. |

| Příznaky skupiny 2 |Value  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Vrátíte pouze názvy vlastností, které definují klíče. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Vrácení pouze názvy vlastností, které jsou odkazy na objekty. |

| Příznaky skupiny 3 |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátíte pouze názvy vlastností, které patří k nejvíce odvozené třídy. Vyloučíte vlastnosti od nadřazených tříd. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Vrátíte pouze názvy vlastností, které patří do nadřazené třídy. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Vrátíte pouze názvy vlastností systému. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Vrátíte pouze názvy vlastností nesystémové. |

Funkce vždy přidělí novou `SAFEARRAY` vrátí-li `WBEM_S_NO_ERROR`, a `pstrNames` je vždycky nastavený tak, aby odkazoval na ni. Vrácené pole může obsahovat 0 elementy, pokud určenému filtru neodpovídají žádné vlastnosti. Pokud funkce vrátí hodnotu jiné než `WBM_S_NO_ERROR`, nový `SAFEARRAY` struktura nevrátí.
 
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
