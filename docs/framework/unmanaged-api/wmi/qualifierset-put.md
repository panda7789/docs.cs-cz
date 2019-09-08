---
title: QualifierSet_Put – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_Put zapisuje pojmenovaný kvalifikátor a jeho hodnotu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798269"
---
# <a name="qualifierset_put-function"></a>QualifierSet_Put – funkce

Zapíše pojmenovaný kvalifikátor a hodnotu. Nový kvalifikátor přepíše předchozí hodnotu se stejným názvem. Pokud kvalifikátor neexistuje, vytvoří se.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`\
pro Název kvalifikátoru, který se má zapsat

`pVal`\
pro Ukazatel na platný `VARIANT` , který obsahuje kvalifikátor k zápisu. Tento parametr nemůže být `null`.

`lFlavor`\
pro Jedna z následujících konstant definující požadované charakter kvalifikátoru pro tento kvalifikátor. Výchozí hodnota je `WBEM_FLAVOR_OVERRIDABLE` (0).

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Kvalifikátor lze přepsat v odvozené třídě nebo instanci. **Toto je výchozí hodnota.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Kvalifikátor je šířen do instancí. |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Kvalifikátor je šířen na odvozené třídy. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | Kvalifikátor nelze přepsat v odvozené třídě nebo instanci. |
| `WBEM_FLAVOR_AMENDED` | 0x80 | Kvalifikátor je lokalizován. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Byl proveden Neplatný pokus o zadání kvalifikátoru **klíče** u vlastnosti, která nemůže být klíčem. Klíče jsou zadány v definici třídy pro objekt a nelze je měnit na základě jednotlivých instancí. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametr není platným typem kvalifikátoru. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Není možné volat `QualifierSet_Put` metodu na kvalifikátoru, protože vlastnící objekt nepovoluje přepsání. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
