---
title: CloneEnumWbemClassObject (Nespravovaný odkaz na rozhraní API)
description: CloneEnumWbemClassObject funkce vytvoří logickou kopii čítače výčtu.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175015"
---
# <a name="cloneenumwbemclassobject-function"></a>Funkce CloneEnumWbemClassObject
Vytvoří logickou kopii čítače výčtu, zachování jeho aktuální pozici ve výčtu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a>Parametry

`ppEnum`\
[out] Obdrží ukazatel na nový [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).

`authLevel`\
[v] Úroveň autorizace.

`impLevel`\
[v] Úroveň zosobnění.

`pCurrentEnumWbemClassObject`\
[out] Ukazatel na instanci [IEnumWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) která má být klonována.

`strUser`\
[v] Uživatelské jméno. Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)

`strPassword`\
[v] Heslo. Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)

`strAuthority`\
[v] Název domény uživatele. Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecnému selhání. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Operace není k dispozici dostatek paměti. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Připojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a službou WMI se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [metody IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)

Tato metoda provede pouze "nejlepší úsilí" kopie. Vzhledem k dynamické povaze mnoho objektů CIM je možné, že nový čítač výčtu není výčet stejnou sadu objektů jako zdroj čítač výčtu.

Pokud volání funkce selže, můžete získat další informace o chybě voláním funkce [GetErrorInfo.](geterrorinfo.md)

## <a name="example"></a>Příklad

Příklad naleznete v metodě [IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)

## <a name="requirements"></a>Požadavky
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).

 **Záhlaví:** WMINet_Utils.idl

 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
