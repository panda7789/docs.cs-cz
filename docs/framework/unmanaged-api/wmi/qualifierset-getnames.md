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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266462a5393c8e26aa2bc3f2ec8ab72d4410a431
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798292"
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

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|  | 0 | Vrátí názvy všech kvalifikátorů. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátí pouze názvy kvalifikátorů specifických pro aktuální vlastnost nebo objekt. <br/> Pro vlastnost: Vrátí pouze kvalifikátory specifické pro vlastnost (včetně přepsání), a ne tyto kvalifikátory šířené z definice třídy. <br/> Pro instanci: Vrátí pouze názvy kvalifikátorů specifických pro instanci. <br/> Pro třídu: Vrátí pouze kvalifikátory specifické pro odvozenou třídu.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Vrátí pouze názvy kvalifikátorů šířených z jiného objektu. <br/> Pro vlastnost: Vrátí pouze kvalifikátory šířené do této vlastnosti z definice třídy, nikoli z samotné vlastnosti. <br/> Pro instanci: Vrátí pouze ty kvalifikátory šířené z definice třídy. <br/> Pro třídu: Vrátí pouze ty názvy kvalifikátorů zděděné z nadřazených tříd. |

`pstrNames`\
mimo Nový `SAFEARRAY` , který obsahuje požadované názvy. Pole může mít 0 prvků. Pokud dojde k chybě, nevrátí `SAFEARRAY` se nový.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .

Jakmile nazískáte názvy kvalifikátorů, můžete k jednotlivým kvalifikátorům přistupovat pomocí volání funkce [QualifierSet_Get](qualifierset-get.md) .

Nejedná se o chybu pro daný objekt, který má nulové kvalifikátory, takže počet řetězců v `pstrNames` případě návratu může být 0, i když funkce vrací. `WBEM_S_NO_ERROR`

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
