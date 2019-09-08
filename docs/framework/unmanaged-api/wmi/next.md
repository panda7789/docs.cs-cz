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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95cea4cb3e7e7df2b6b52256a440b9a8d544f2db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798408"
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
mimo Nový `BSTR` , který obsahuje název vlastnosti. Tento parametr můžete nastavit na, `null` Pokud není název vyžadován.

`pVal`\
mimo `VARIANT` Vyplněný hodnotou vlastnosti. Tento parametr lze nastavit na `null` hodnotu, pokud není požadovaná hodnota. Pokud funkce vrátí kód chyby, `VARIANT` předané do `pVal` není ponecháno beze změny.

`pvtType`\
mimo Ukazatel na `CIMTYPE` proměnnou `LONG` (do které je umístěn typ vlastnosti). Hodnota této vlastnosti může být `VT_NULL_VARIANT`, v takovém případě je nutné určit skutečný typ vlastnosti. Tento parametr může být `null`také.

`plFlavor`\
mimo `null`nebo hodnota, která přijímá informace o původu vlastnosti. Možné hodnoty jsou uvedeny v části [poznámky].

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | [`BeginEnumeration`](beginenumeration.md) Funkci se nevolalo. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Vzdálené volání procedury mezi aktuálním procesem a správou systému Windows se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Ve výčtu nejsou žádné další vlastnosti. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .

Tato metoda také vrátí systémové vlastnosti.

Pokud podkladový typ vlastnosti je cesta objektu, datum nebo čas nebo jiný speciální typ, pak vrácený typ neobsahuje dostatek informací. Volající musí prostudovat `CIMTYPE` pro zadanou vlastnost, aby určil, zda je vlastnost odkaz na objekt, datum nebo čas nebo jiný speciální typ.

Pokud `plFlavor` není,`LONG`hodnota obdrží informace o původu vlastnosti, a to následujícím způsobem: `null`

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systémová vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: Vlastnost je zděděna z nadřazené třídy. <br> Pro instanci: Vlastnost, která byla zděděna z nadřazené třídy, nebyla upravena instancí.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pro třídu: Vlastnost patří do odvozené třídy. <br> Pro instanci: Vlastnost je upravena instancí. To znamená, že byla zadána hodnota nebo byl přidán nebo upraven kvalifikátor. |

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
