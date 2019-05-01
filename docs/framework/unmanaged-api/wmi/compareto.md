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
ms.openlocfilehash: fb5a26fccf7ceb56089aae4bd4f0732b8a405ba0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049268"
---
# <a name="compareto-function"></a>Funkce CompareTo

Porovná objekt na jiný objekt správy Windows.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
[in] Tento parametr se nepoužívá.

`ptr`\
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`flags`\
[in] Bitová kombinace příznaků, které určují vlastnosti objektu vzít v úvahu pro porovnání. Zobrazit [poznámky](#remarks) části Další informace.

`pCompareTo`\
[in] Objekt k porovnání. `pCompareTo` musí být platný [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; nemůže být `null`.

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

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignorujte zdroje (serveru a oboru názvů, které pocházejí z). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorovat všechny kvalifikátory (včetně **klíč** a **dynamické**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignorujte výchozí hodnoty vlastnosti. Tento příznak platí jenom pro porovnání třídy. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignorujte flavor. Tento příznak stále kvalifikátory bere v úvahu, ale bude ignorovat rozdíly charakter, jako jsou pravidla pro šíření a přepsat omezení. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignorujte velikost písmen v porovnání hodnot řetězců. Platí to i na řetězce a jednu hodnotu kvalifikátoru. Porovnání názvy vlastností a kvalifikátor je vždy bez ohledu na to, zda je tento příznak nastaven malá a velká písmena. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Předpokládá, že porovnávaných objektů jsou instance stejné třídy. V důsledku toho tento příznak porovnává instance informace týkající se pouze. Pomocí tohoto příznaku za účelem optimalizace výkonu. Pokud objekty nejsou stejné třídy, nejsou výsledky definovány. |

Nebo můžete zadat jeden složený příznak následujícím způsobem:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Vezměte v úvahu všechny funkce v porovnání. |

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)