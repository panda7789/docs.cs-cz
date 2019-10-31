---
title: Put – funkce (odkaz nespravovaného rozhraní API)
description: Funkce put přiřadí novou hodnotu pojmenované vlastnosti.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f1bb8aa09a269e3b8fd23f393d63a275d308a77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127407"
---
# <a name="put-function"></a>Put – funkce

Nastaví vlastnost s názvem na novou hodnotu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
pro Název vlastnosti. Tento parametr nelze `null`.

`lFlags`\
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`pVal`\
pro Ukazatel na platný `VARIANT`, který se změní na novou hodnotu vlastnosti. Pokud je `pVal` `null` nebo odkazuje na `VARIANT` typu `VT_NULL`, vlastnost je nastavena na hodnotu `null`.

`vtType`\
pro Typ `VARIANT` odkazoval na `pVal`. Další informace najdete v části [poznámky](#remarks) .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů je neplatných. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Typ vlastnosti nebyl rozpoznán. Tato hodnota je vrácena při vytváření instancí třídy, pokud třída již existuje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | For Instances: označuje, že `pVal` odkazuje na `VARIANT` nesprávného typu pro vlastnost. <br/> Pro definice tříd: vlastnost již v nadřazené třídě existuje a nový typ COM se liší od starého typu modelu COM. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

Tato funkce vždy přepíše aktuální hodnotu vlastnosti novou hodnotou. Pokud [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na definici třídy, `Put` vytvoří nebo aktualizuje hodnotu vlastnosti. Když [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na instanci CIM, `Put` aktualizuje pouze hodnotu vlastnosti. `Put` nemůže vytvořit hodnotu vlastnosti.

Vlastnost System `__CLASS` je zapisovatelné pouze během vytváření třídy, pokud nemusí být ponechána prázdná. Všechny ostatní vlastnosti systému jsou jen pro čtení.

Uživatel nemůže vytvořit vlastnosti s názvy, které začínají nebo končí podtržítkem ("_"). Toto je vyhrazeno pro systémové třídy a vlastnosti.

Pokud vlastnost nastavená funkcí `Put` existuje v nadřazené třídě, je výchozí hodnota vlastnosti změněna, pokud se typ vlastnosti neshoduje s typem nadřazené třídy. Pokud vlastnost neexistuje a nejedná se o neshodu typů, je vytvořena vlastnost.

Parametr `vtType` použijte pouze při vytváření nových vlastností v definici třídy CIM a `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`. V tomto případě parametr `vType` určuje typ CIM vlastnosti. V každém případě `vtType` musí být 0. `vtType` musí být také 0, pokud je podkladovým objektem instance (i když je `Val` `null`), protože typ vlastnosti je pevný a nelze jej změnit.

## <a name="example"></a>Příklad

Příklad naleznete v metodě [IWbemclassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
