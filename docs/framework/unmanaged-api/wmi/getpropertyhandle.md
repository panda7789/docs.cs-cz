---
title: GetPropertyHandle – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetPropertyHandle vrací jedinečný popisovač, který identifikuje vlastnost.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6dc2792b572aae30e9989c81967b86f340d7b83
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038264"
---
# <a name="getpropertyhandle-function"></a>Funkce GetPropertyHandle

Vrací jedinečný popisovač, který identifikuje vlastnost.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`wszPropertyName`\
pro Řetězec zakončený znakem null UTF16 znaků, který obsahuje název vlastnosti.

`pType`\
mimo Ukazatel na [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) člen výčtu, který představuje typ CIM vlastnosti.

`pHandle`\
mimo Ukazatel na celé číslo, které obsahuje popisovač vlastnosti.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný název vlastnosti nebyl nalezen. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | Požadovaná vlastnost je typu `CIM_OBJECT` nebo. `CIM_ARRAY` |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) .

Tento popisovač můžete použít k identifikaci vlastností při použití metod [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) ke čtení nebo zápisu hodnot vlastností.

Obslužné rutiny lze načíst pro vlastnosti všech datových typů, které `CIM_OBJECT` jsou `CIM_ARRAY`jiné než a. Vrácené obslužné rutiny fungují napříč všemi instancemi třídy.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
