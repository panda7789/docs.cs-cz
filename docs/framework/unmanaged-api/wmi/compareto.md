---
title: Funkce CompareTo (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CompareTo porovná objektu na jiný objekt rozhraní WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4431da90842f4f96a0f09a2f28dc473d956ee3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compareto-function"></a>CompareTo – funkce
Porovná objekt k jinému objektu správy systému Windows.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`flags`  
[v] Bitová kombinace příznaky, které určují vlastnosti objektu vzít v úvahu pro porovnání. Najdete v článku [poznámky](#remarks) části Další informace.

`pCompareTo`  

[v] Objekt k porovnání. `pcompareTo` musí být platná [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance; nemůže být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` byl proveden bez použité volání [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Objekty se liší. |
| `WBEM_S_SAME` | 0 | Objekty jsou stejné podle příznaky porovnání. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) metoda.

Příznaky, které lze předat jako `lEnumFlags` argument jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu. Zadávat lze jednotlivé vlastnosti zahrnutých v porovnání zadáním bitovou kombinaci následující příznaky:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignorujte zdroje (serveru a oboru názvů, které pocházejí z). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorovat všechny kvalifikátory (včetně **klíč** a **dynamické**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignorujte výchozí hodnoty vlastností. Tento příznak se vztahuje pouze k porovnání tříd. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignorujte kvalifikátor typů. Tento příznak stále kvalifikátory bere v úvahu, ale ignoruje příchuť rozdíly, jako například šíření pravidla a přepsání omezení. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignorujte velká písmena v porovnání hodnot řetězců. To se vztahuje jak na řetězce a kvalifikátor hodnoty. Porovnání názvů vlastností a kvalifikátor je vždy bez ohledu na to, jestli je nastavený tento příznak malá a velká písmena. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Předpokládejme, že porovnávaných objektů jsou instanes stejné třídy. V důsledku toho tento příznak porovná instance informace týkající se jenom. Pomocí této příznaků za účelem optimalizace výkonu. Pokud objekty nejsou stejné třídy, není definován výsledky. |

Nebo můžete zadat jeden složený příznak následujícím způsobem:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Vezměte v úvahu všechny funkce v porovnání. |

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
