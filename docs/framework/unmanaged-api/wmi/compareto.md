---
title: CompareTo – funkce (Reference nespravovaného rozhraní API)
description: Funkce CompareTo porovná objekt s jiným objektem WMI.
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
ms.openlocfilehash: 2ec42dff333422e247a11b4a3a5b9aed9bd316fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798774"
---
# <a name="compareto-function"></a>Funkce CompareTo

Porovná objekt s jiným objektem správy systému Windows.

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
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`flags`\
pro Bitová kombinace příznaků, které určují vlastnosti objektu, které je třeba vzít v úvahu pro porovnání. Další informace najdete v části [poznámky](#remarks) .

`pCompareTo`\
pro Objekt pro porovnání. `pCompareTo`musí se jednat o platnou instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ; nemůže být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` bylo provedeno bez navýšení [`EndEnumeration`](endenumeration.md)volání. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Objekty jsou odlišné. |
| `WBEM_S_SAME` | 0 | Objekty jsou stejné na základě příznaků porovnávání. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .

Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty. Můžete určit jednotlivé charakteristiky, které se týkají porovnání, zadáním bitové kombinace následujících příznaků:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignorujte zdroj (Server a obor názvů, ze kterého pochází). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorovat všechny kvalifikátory (včetně **klíčového** a **dynamického**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignoruje výchozí hodnoty vlastností. Tento příznak se vztahuje pouze na porovnání tříd. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignorovat charakter kvalifikátoru. Tento příznak stále používá kvalifikátory, ale ignoruje rozdíly v charakteru, jako jsou pravidla šíření a omezení přepisování. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignoruje velikost písmen v porovnání řetězcových hodnot. To platí pro řetězce a hodnoty kvalifikátoru. Porovnání názvů vlastností a kvalifikátorů je vždy rozlišovat velká a malá písmena bez ohledu na to, zda je tento příznak nastaven. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Předpokládá, že porovnávané objekty jsou instancemi stejné třídy. Proto tento příznak porovnává pouze informace týkající se instancí. Pomocí těchto příznaků Optimalizujte výkon. Pokud objekty nejsou stejné třídy, výsledky nejsou definovány. |

Můžete také zadat jeden složený příznak následujícím způsobem:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Zvažte všechny funkce v porovnání. |

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
