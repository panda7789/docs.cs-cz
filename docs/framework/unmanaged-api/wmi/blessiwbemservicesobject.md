---
title: BlessIWbemServicesObject function (Unmanaged API Reference)
description: Funkce BlessIWbemServicesObject označuje, zda pověření uživatele povolují přístup k objektu IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175028"
---
# <a name="blessiwbemservicesobject-function"></a>Funkce BlessIWbemServicesObject
Označuje, zda pověření uživatele povolit přístup k zadanému objektu [IWbemServices.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>Parametry

`pIWbemServices`\
[v] Ukazatel na objekt služby služby Služby WMI.

`strUser`\
[v] Uživatelské jméno.

`strPassword`\
[v] Heslo přidružené `strUser`k souboru .

`strAuthority`\
[v] Název domény uživatele. Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)

`impLevel`\
[v] Úroveň zosobnění.

`authnLevel`\
[v] Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WinError.h* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden nebo více argumentů je neplatných. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` je `null`. |
| `E_FAIL` | 0x80000008 | Došlo k nespecifikované chybě. |
| `E_OUTOFMEMORY` | 0x80000002 | K provedení operace není k dispozici dostatek paměti. |
| `S_OK` | 0 | Volání funkce bylo úspěšné. |

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).

 **Záhlaví:** WMINet_Utils.idl

 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
