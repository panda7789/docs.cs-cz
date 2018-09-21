---
title: Funkce CompareTo (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CompareTo porovná objekt na jiný objekt rozhraní WMI.
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
ms.openlocfilehash: bde25ae7455dd7fe35fe1a0a43bb2a6b560c0e3e
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480536"
---
# <a name="compareto-function"></a>Funkce CompareTo
Porovná objekt na jiný objekt správy Windows.  

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
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`flags`  
[in] Bitová kombinace příznaků, které určují vlastnosti objektu vzít v úvahu pro porovnání. Zobrazit [poznámky](#remarks) části Další informace.

`pCompareTo`  

[in] Objekt k porovnání. `pcompareTo` musí být platný [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; nemůže být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k nespecifikované chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` proběhla bez opětovné volání [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Objekty jsou odlišné. |
| `WBEM_S_SAME` | 0 | Objekty jsou stejné založené na porovnání příznaky. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) metody.

Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu. Vlastnosti jednotlivých součástí porovnání můžete zadat tak, že zadáte bitová kombinace hodnot následující příznaky:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignorujte zdroje (serveru a oboru názvů, které pocházejí z). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorovat všechny kvalifikátory (včetně **klíč** a **dynamické**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignorujte výchozí hodnoty vlastnosti. Tento příznak platí jenom pro porovnání třídy. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignorujte flavor. Tento příznak stále kvalifikátory bere v úvahu, ale bude ignorovat rozdíly charakter, jako jsou pravidla pro šíření a přepsat omezení. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignorujte velikost písmen v porovnání hodnot řetězců. Platí to i na řetězce a jednu hodnotu kvalifikátoru. Porovnání názvy vlastností a kvalifikátor je vždy bez ohledu na to, zda je tento příznak nastaven malá a velká písmena. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Předpokládají, že jsou objekty, který se porovnává instanes stejné třídy. V důsledku toho tento příznak porovnává instance informace týkající se pouze. Pomocí tohoto příznaku za účelem optimalizace výkonu. Pokud objekty nejsou stejné třídy, nejsou výsledky definovány. |

Nebo můžete zadat jeden složený příznak následujícím způsobem:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Vezměte v úvahu všechny funkce v porovnání. |

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
