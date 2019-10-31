---
title: Get – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 60f29b91000fd3c07efea88dcc319eb283a4af78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120328"
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
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
pro Název vlastnosti.

`lFlags`\
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`pVal`\
mimo Pokud se funkce vrátí úspěšně, obsahuje hodnotu vlastnosti `wszName`. Argumentu `pval` je přiřazen správný typ a hodnota kvalifikátoru.

`pvtType`\
mimo Pokud se funkce vrátí úspěšně, obsahuje [konstantu typu CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) , která označuje typ vlastnosti. Její hodnota může být také `null`. 

`plFlavor`\
mimo Pokud se funkce vrátí úspěšně, obdrží informace o původu vlastnosti. Jeho hodnota může být `null`nebo jedna z následujících konstant WBEM_FLAVOR_TYPE definovaných v souboru hlaviček *WbemCli. h* : 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systémová vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: vlastnost je zděděna z nadřazené třídy. <br> Pro instanci: vlastnost, která byla zděděna z nadřazené třídy, nebyla upravena instancí.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0,8 | Pro třídu: vlastnost patří do odvozené třídy. <br> Pro instanci: vlastnost je upravena instancí. To znamená, že byla zadána hodnota nebo byl přidán nebo upraven kvalifikátor. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů je neplatných. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost nebyla nalezena. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .

Funkce `Get` může také vracet systémové vlastnosti.

Argumentu `pVal` je přiřazen správný typ a hodnota kvalifikátoru a funkce [VARIANTINIT](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) com.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** WMINet_Utils. idl

 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
