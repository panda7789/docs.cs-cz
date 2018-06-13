---
title: GetNames – funkce (referenční dokumentace nespravovaného rozhraní API)
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
ms.openlocfilehash: 108946428cdfadcfb9c653b7e444bf278dfa2782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461978"
---
# <a name="getnames-function"></a>GetNames – funkce
Načte podmnožinu nebo všechny názvy vlastností objektu. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
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
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszQualifierName`  
[v] Ukazatel na platnou `LPCWSTR` určující kvalifikátor název, který funguje jako součást filtru. Další informace najdete v tématu [poznámky](#remarks) části. Tento parametr může být `null`. 

`lFlags`  
[v] Kombinace bitových polí. Další informace najdete v tématu [poznámky](#remarks) části.

`pQualifierValue`   
[v] Ukazatel na platnou `VARIANT` struktura inicializována tak, aby hodnota filtru. Tento parametr může být `null`. 

`pstrNames`  
[out] A `SAFEARRAY` struktura, která obsahuje názvy vlastností. Na záznam, musí být tento parametr vždycky ukazatel na `null`. Najdete v článku [poznámky](#remarks) části Další informace. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné nebo byl zadán nesprávný kombinace příznaky a parametry. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) metoda.

Pojmenované vrátil jsou řízeny kombinaci příznaky a parametry. Například funkce může vrátit názvy všech vlastností nebo pouze názvy klíčové vlastnosti.  Primárním filtru je uveden v `lFlags` parametr a ostatní parametry lišit v závislosti na jeho.

Příznak hodnoty v `lFlags` jsou bitová pole


Příznaky, které lze předat jako `lEnumFlags` argument jsou bitová pole, které jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu.  Můžete kombinovat jeden příznak z každé skupiny libovolný příznakem z jiné skupiny. Příznaky ze stejné skupiny jsou však vzájemně vylučují. 

| Příznaky skupina 1 |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Vrátí všechny názvy vlastností. `strQualifierName` a `pQualifierVal` se nepoužívá. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Vrátí pouze vlastnosti, které mají kvalifikátor název určený správcem `strQualifierName` parametr. Pokud tento příznak se používá, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Vrátí pouze vlastnosti, které nemají kvalifikátor název zadaný `strQualifierName` parametr. Pokud tento příznak se používá, je nutné zadat `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Vrátí pouze vlastnosti, které mají kvalifikátor název zadaný `wszQualifierName` parametr a mají také stejná jako určeného hodnotu `pQualifierVal` struktura. Pokud tento příznak se používá, musíte zadat oba `wszQualifierName` a `pQualifierValue`. |

| Skupina 2 příznaky |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Vrátí pouze názvy vlastností, které definují klíče. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Návratový pouze názvy vlastností, které jsou odkazy na objekty. |

| Příznaky skupiny 3 |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátí pouze názvy vlastností, které patří do nejvíce odvozené třídy. Vlastnosti vylučte z nadřazené třídy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Vrátí pouze názvy vlastností, které patří do nadřazené třídy. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Vrátí pouze názvy vlastností systému. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Vrátí pouze názvy nesystémové vlastnosti. |

Funkce vždy přiděluje nový `SAFEARRAY` vrátí-li `WBEM_S_NO_ERROR`, a `pstrNames` je vždycky nastavený tak, aby odkazoval na ni. Pole vrácené může mít elementy 0, pokud žádné vlastnosti, které odpovídají zadané filtry. Pokud funkce vrátí hodnotu než `WBM_S_NO_ERROR`, nový `SAFEARRAY` struktura nevrátí.
 
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
