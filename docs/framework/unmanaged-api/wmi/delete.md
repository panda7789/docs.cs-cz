---
title: Delete – funkce (odkaz na nespravované rozhraní API)
description: Funkce delete odstraní zadanou vlastnost a všechny její kvalifikátory z definice třídy CIM.
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
ms.openlocfilehash: 6b8f287be831702dd31a8335f9b2f6447bcee540
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127667"
---
# <a name="delete-function"></a>Funkce Delete

Odstraní zadanou vlastnost a všechny její kvalifikátory z definice třídy CIM.

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
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
pro Název vlastnosti, která se má odstranit `wszName` musí být ukazatel na platný `LPCWSTR`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Vlastnost nelze odstranit. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Formát  `wszName` je neplatný. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení operace není dostatek paměti. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Vlastnost je zděděna ze základní třídy. |
| `WBEM_E_SYSTEM_PROPERTY` | | Vlastnost je systémová vlastnost. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | Funkce odstranila výchozí hodnotu přepisu pro aktuální třídu. Výchozí hodnota této vlastnosti v nadřazené třídě byla znovu aktivována. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject::D dstranit](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
