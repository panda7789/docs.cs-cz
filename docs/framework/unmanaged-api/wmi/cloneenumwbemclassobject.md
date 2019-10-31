---
title: CloneEnumWbemClassObject – funkce (Reference nespravovaného rozhraní API)
description: Funkce CloneEnumWbemClassObject vytvoří logickou kopii enumerátoru.
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
ms.openlocfilehash: 9d2442161aaa83693a33f9efc230c09b8c4426e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128724"
---
# <a name="cloneenumwbemclassobject-function"></a>Funkce CloneEnumWbemClassObject
Vytvoří logickou kopii enumerátoru a uchová jeho aktuální pozici ve výčtu.

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
mimo Přijme ukazatel na nový [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).

`authLevel`\
pro Úroveň autorizace.

`impLevel`\
pro Úroveň zosobnění.

`pCurrentEnumWbemClassObject`\
mimo Ukazatel na instanci [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) , která se má klonovat

`strUser`\
pro Uživatelské jméno Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

`strPassword`\
pro Heslo. Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

`strAuthority`\ [in] název domény uživatele. Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení operace není k dispozici dostatek paměti. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .

Tato metoda vytvoří pouze "nejlepší úsilí". Vzhledem k dynamické povaze mnoha objektů CIM je možné, že nový enumerátor nevytvoří výčet stejné sady objektů jako zdrojový enumerátor.

Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .

## <a name="example"></a>Příklad

Příklad naleznete v tématu metoda [IEnumWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .

## <a name="requirements"></a>Požadavky
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** WMINet_Utils. idl

 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
