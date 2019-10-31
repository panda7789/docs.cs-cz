---
title: BlessIWbemServicesObject – funkce (Reference nespravovaného rozhraní API)
description: Funkce BlessIWbemServicesObject určuje, jestli přihlašovací údaje uživatele povolují přístup k objektu služby IWbem.
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
ms.openlocfilehash: f77ff394668a235dd63cf0cddf71ea418a28125b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141681"
---
# <a name="blessiwbemservicesobject-function"></a>Funkce BlessIWbemServicesObject
Určuje, zda přihlašovací údaje uživatele povolují přístup k zadanému objektu [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) . 

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
pro Ukazatel na objekt služby WMI.

`strUser`\
pro Uživatelské jméno

`strPassword`\
pro Heslo přidružené k `strUser`

`strAuthority`\
pro Název domény uživatele Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

`impLevel`\
pro Úroveň zosobnění.

`authnLevel`\
pro Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *Winerror. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden nebo více argumentů je neplatných. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` je `null`. | 
| `E_FAIL` | 0x80000008 | Došlo k neurčené chybě. |
| `E_OUTOFMEMORY` | 0x80000002 | K provedení této operace je k dispozici dostatek paměti. | 
| `S_OK` | 0,8 | Volání funkce bylo úspěšné. | 

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** WMINet_Utils. idl

 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
