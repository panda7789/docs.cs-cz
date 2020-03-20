---
title: Get funkce (Unmanaged API Reference)
description: Funkce Get načte zadanou hodnotu vlastnosti.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174976"
---
# <a name="get-function"></a>Funkce Get

Načte zadanou hodnotu vlastnosti, pokud existuje.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Get (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
[v] Tento parametr není použit.

`ptr`\
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`\
[v] Název vlastnosti.

`lFlags`\
[v] Vyhrazena. Tento parametr musí být 0.

`pVal`\
[out] Pokud funkce vrátí úspěšně, obsahuje hodnotu vlastnosti. `wszName` Argumentu `pval` je přiřazen správný typ a hodnota kvalifikátoru.

`pvtType`\
[out] Pokud funkce vrátí úspěšně, obsahuje [konstantu typu CIM,](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) která označuje typ vlastnosti. Jeho hodnota může `null`být také .

`plFlavor`\
[out] Pokud se funkce vrátí úspěšně, obdrží informace o původu vlastnosti. Jeho hodnota `null`může být , nebo jeden z následujících WBEM_FLAVOR_TYPE konstantdefinovaných v souboru hlavičky *WbemCli.h:*

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systémová vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: Vlastnost je zděděna z nadřazené třídy. <br> Pro instanci: Vlastnost, zatímco zděděné z nadřazené třídy, nebyla změněna instance.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pro třídu: Vlastnost patří do odvozené třídy. <br> Pro instanci: Vlastnost je upravena instance; to znamená, že byla zadána hodnota nebo byl přidán nebo změněn kvalifikátor. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecnému selhání. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů není platný. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost nebyla nalezena. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení operace není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [metody IWbemClassObject::Get.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)

Funkce `Get` může také vrátit vlastnosti systému.

Argumentu `pVal` je přiřazen správný typ a hodnota pro kvalifikátor a funkci COM [VariantInit.](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).

 **Záhlaví:** WMINet_Utils.idl

 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
