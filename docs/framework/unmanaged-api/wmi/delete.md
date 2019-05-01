---
title: Odstranit funkci (referenční dokumentace nespravovaného rozhraní API)
description: Funkce Delete Odstraní zadané vlastnosti a všechny jeho kvalifikátory z definice třídy CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1a26db7785a8a378fa541308ecc6aee30fa87ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049281"
---
# <a name="delete-function"></a>Funkce Delete

Odstraní zadanou vlastnost a všechny jeho kvalifikátory z definice třídy CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
[in] Tento parametr se nepoužívá.

`ptr`\
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszName`\
[in] Název vlastnosti, která má odstranit. `wszName` musí být ukazatel na platný `LPCWSTR`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k nespecifikované chybě. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Vlastnost nelze odstranit. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Formát  `wszName` je neplatný. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Není k dispozici dostatek paměti k dokončení operace. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Vlastnost se dědí ze základní třídy. |
| `WBEM_E_SYSTEM_PROPERTY` | | Vlastnost je vlastnost systému. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | Funkce odstranit výchozí hodnotu pro aktuální třídu. Výchozí hodnota této vlastnosti v nadřazené třídě byl znovu aktivován. |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)