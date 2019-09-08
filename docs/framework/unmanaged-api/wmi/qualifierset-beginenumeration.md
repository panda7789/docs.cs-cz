---
title: QualifierSet_BeginEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_BeginEnumeration obnoví enumerátor kvalifikátorů objektu.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798343"
---
# <a name="qualifierset_beginenumeration-function"></a>QualifierSet_BeginEnumeration – funkce

Obnoví enumerátor kvalifikátorů objektu na začátek výčtu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
pro Bitová kombinace příznaků nebo hodnot popsaných v části [poznámky](#remarks) , které určují kvalifikátory, které mají být zahrnuty do výčtu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametr není platný. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `QualifierSet_BeginEnumeration` bylo provedeno bez navýšení [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)volání. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet:: funkce BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .

Chcete-li vytvořit výčet všech kvalifikátorů objektu, musí být tato metoda volána před prvním voláním [QualifierSet_Next](qualifierset-next.md). Pořadí, ve kterém jsou kvalifikátory výčty, je zaručené pro daný výčet jako invariantní.

Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|  | 0 | Vrátí názvy všech kvalifikátorů. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátí pouze názvy kvalifikátorů specifických pro aktuální vlastnost nebo objekt. <br/> Pro vlastnost: Vrátí pouze kvalifikátory specifické pro vlastnost (včetně přepsání), a ne tyto kvalifikátory šířené z definice třídy. <br/> Pro instanci: Vrátí pouze názvy kvalifikátorů specifických pro instanci. <br/> Pro třídu: Vrátí pouze kvalifikátory specifické pro odvozenou třídu.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Vrátí pouze názvy kvalifikátorů šířených z jiného objektu. <br/> Pro vlastnost: Vrátí pouze kvalifikátory šířené do této vlastnosti z definice třídy, nikoli z samotné vlastnosti. <br/> Pro instanci: Vrátí pouze ty kvalifikátory šířené z definice třídy. <br/> Pro třídu: Vrátí pouze ty názvy kvalifikátorů zděděné z nadřazených tříd. |

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
