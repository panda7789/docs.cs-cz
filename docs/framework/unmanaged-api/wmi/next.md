---
title: Next – funkce (odkaz na nespravované rozhraní API)
description: Funkce Next načte další vlastnost ve výčtu.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 587e085f6fe9f6c19d3605c673cd3bd6f68162f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127381"
---
# <a name="next-function"></a>Funkce Next
Načte další vlastnost ve výčtu, který začíná voláním [funkce BeginEnumeration](beginenumeration.md).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`\
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`pstrName`\
mimo Nový `BSTR`, který obsahuje název vlastnosti. Tento parametr můžete nastavit tak, aby `null`, pokud název není povinný.

`pVal`\
mimo `VARIANT` vyplněno hodnotou vlastnosti. Tento parametr můžete nastavit tak, aby `null`, pokud není požadovaná hodnota. Pokud funkce vrátí chybový kód, `VARIANT` předané do `pVal` zůstane beze změny.

`pvtType`\
mimo Ukazatel na `CIMTYPE` proměnnou (`LONG`, do které je umístěn typ vlastnosti). Hodnota této vlastnosti může být `VT_NULL_VARIANT`. v takovém případě je nutné určit skutečný typ vlastnosti. Tento parametr může být také `null`.

`plFlavor`\
[out] `null`nebo hodnota, která přijímá informace o původu vlastnosti. Možné hodnoty jsou uvedeny v části [poznámky].

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Nedošlo k volání funkce [`BeginEnumeration`](beginenumeration.md) . |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Vzdálené volání procedury mezi aktuálním procesem a správou systému Windows se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Ve výčtu nejsou žádné další vlastnosti. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .

Tato metoda také vrátí systémové vlastnosti.

Pokud podkladový typ vlastnosti je cesta objektu, datum nebo čas nebo jiný speciální typ, pak vrácený typ neobsahuje dostatek informací. Volající musí prostudovat `CIMTYPE` pro zadanou vlastnost k určení, zda je vlastnost odkaz na objekt, datum nebo čas nebo jiný speciální typ.

Pokud `plFlavor` není `null`, hodnota `LONG` obdrží informace o původu vlastnosti, a to následujícím způsobem:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systémová vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: vlastnost je zděděna z nadřazené třídy. <br> Pro instanci: vlastnost, která byla zděděna z nadřazené třídy, nebyla upravena instancí.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0,8 | Pro třídu: vlastnost patří do odvozené třídy. <br> Pro instanci: vlastnost je upravena instancí. To znamená, že byla zadána hodnota nebo byl přidán nebo upraven kvalifikátor. |

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
