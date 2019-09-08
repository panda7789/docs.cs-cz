---
title: GetMethod – funkce (nespravované reference rozhraní API)
description: Funkce GetMethod načte informace o metodě.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798564"
---
# <a name="getmethod-function"></a>Funkce GetMethod

Načte informace o zadané metodě.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
pro Název metody. Tento parametr nemůže být `null` a musí odkazovat na platný. `LPCWSTR`

`lFlags`\
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`ppInSignature`\
mimo Ukazatel na adresu instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , která popisuje parametry v parametrech metody. Tento parametr je ignorován, pokud je nastaven na `null`hodnotu.

`ppOutSignature`\
mimo Ukazatel na adresu instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , která popisuje výstupní parametry metody. Tento parametr je ignorován, pokud je nastaven na `null`hodnotu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost nebyla nalezena. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .

Správa systému Windows může nastavit ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) na `null` hodnotu, pokud metoda nemá žádné parametry.

V `ppInSignature` systémech `ppOutSignature` a popište parametry a výstupní parametry v uvedeném pořadí jako vlastnosti `IWbemClassObject` instance třídy System Class [_Parameters](/windows/desktop/WmiSdk/--parameters). `ppInSignature` Vlastnosti v `Param`mají název *n*, kde *n* je pozice parametru v signatuře metody (například `Param1`, `Param2`atd.). Vlastnosti v `ppOutSignature` jsou také pojmenované `Param` *n*a návratová hodnota je pojmenována `ReturnValue`. Další informace a příklad naleznete v tématu [Metoda IWbemclassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
