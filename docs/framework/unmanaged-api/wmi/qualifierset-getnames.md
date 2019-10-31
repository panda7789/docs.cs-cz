---
title: QualifierSet_GetNames – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_GetNames načítá názvy kvalifikátorů z objektu nebo vlastnosti.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141690"
---
# <a name="qualifierset_getnames-function"></a>QualifierSet_GetNames – funkce

Načte názvy všech kvalifikátorů nebo určitých kvalifikátorů, které jsou k dispozici z aktuálního objektu nebo vlastnosti.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
pro Jeden z následujících příznaků nebo hodnot, které určují názvy, které mají být zahrnuty do výčtu.

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|  | 0,8 | Vrátí názvy všech kvalifikátorů. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátí pouze názvy kvalifikátorů specifických pro aktuální vlastnost nebo objekt. <br/> Pro vlastnost: vrátí pouze kvalifikátory specifické pro vlastnost (včetně přepsání), a nikoli tyto kvalifikátory šířené z definice třídy. <br/> Pro instanci: vracet pouze názvy kvalifikátorů specifických pro instanci. <br/> Pro třídu: vracet pouze kvalifikátory specifické pro odvozenou třídu.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Vrátí pouze názvy kvalifikátorů šířených z jiného objektu. <br/> Pro vlastnost: vrátí pouze kvalifikátory šířené do této vlastnosti z definice třídy, nikoli z samotné vlastnosti. <br/> Pro instanci: vrátí pouze ty kvalifikátory šířené z definice třídy. <br/> Pro třídu: vrátí pouze ty názvy kvalifikátorů zděděné z nadřazených tříd. |

`pstrNames`\
mimo Nový `SAFEARRAY`, který obsahuje požadované názvy. Pole může mít 0 prvků. Pokud dojde k chybě, nevrátí se nový `SAFEARRAY`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .

Jakmile nazískáte názvy kvalifikátorů, můžete k jednotlivým kvalifikátorům přistupovat pomocí volání funkce [QualifierSet_Get](qualifierset-get.md) .

Nejedná se o chybu pro daný objekt, který má nulové kvalifikátory, takže počet řetězců v `pstrNames` při návratu může být 0, i když funkce vrací `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
