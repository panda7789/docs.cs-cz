---
title: Funkci Next (referenční dokumentace nespravovaného rozhraní API)
description: Další funkce načte další vlastnosti ve výčtu.
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
ms.openlocfilehash: b5b456feeb1cb09e4957e470344146cf4358d8c7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636160"
---
# <a name="next-function"></a>Další funkce
Načte další vlastnosti ve výčtu, která začíná volání [funkce BeginEnumeration](beginenumeration.md).

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
[in] Tento parametr se nepoužívá.

`ptr`\
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`\
[in] Vyhrazená. Tento parametr musí být 0.

`pstrName`\
[out] Nový `BSTR` , který obsahuje název vlastnosti. Tento parametr lze nastavit na `null` Pokud název není povinné.

`pVal`\
[out] A `VARIANT` vyplněnou hodnotou vlastnosti. Tento parametr lze nastavit na `null` Pokud hodnota není povinné. Pokud funkce vrátí chybový kód, `VARIANT` předán `pVal` je bez jakýchkoli úprav vlevo.

`pvtType`\
[out] Ukazatel `CIMTYPE` proměnné ( `LONG` do typ vlastnosti je umístěn). Hodnota této vlastnosti může být `VT_NULL_VARIANT`, v takovém případě je potřeba určit skutečný typ vlastnosti. Tento parametr může být také `null`.

`plFlavor`\
[out] `null`, nebo hodnotu, která obdrží informace o původu vlastnosti. Možné hodnoty v části [poznámky].

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Došlo bez volání [ `BeginEnumeration` ](beginenumeration.md) funkce. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici zahájíte nový výčet. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Volání vzdálených procedur mezi aktuálním procesem a službou Windows Management se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nejsou žádné další vlastnosti ve výčtu. |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) metody.

Tato metoda také vrátí hodnotu vlastnosti systému.

Pokud základní typ vlastnosti je cesta k objektu, datum nebo čas nebo jiné speciální typ, pak vrácený typ neobsahuje dostatek informací. Volající musí zkontrolovat `CIMTYPE` zadané vlastnosti k určení, zda je odkaz na objekt, datum nebo čas nebo jiné speciální typ vlastnosti.

Pokud `plFlavor` není `null`, `LONG` hodnotu obdrží informace o původu vlastnost, následujícím způsobem:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systém vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: Vlastnost se dědí z nadřazené třídy. <br> Pro instanci: Vlastnost, zatímco zděděná z nadřazené třídy nebyl změněn instancí.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pro třídu: Vlastnost patří k odvozené třídě. <br> Pro instanci: Instance; je změněna vlastnost To znamená, že byla zadána hodnota nebo kvalifikátor byla přidána nebo upravena. |

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
