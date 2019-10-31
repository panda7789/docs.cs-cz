---
title: GetPropertyQualifierSet – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetPropertyQualifierSet načte kvalifikátor sady pro vlastnost.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4133145c7bea1fb3c018d809b9fea3de38270619
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127459"
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet – funkce

Načte kvalifikátor sady pro konkrétní vlastnost.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszMethod`\
pro Název vlastnosti `wszProperty` musí ukazovat na platný `LPCWSTR`.

`ppQualSet`\
mimo Přijímá ukazatel rozhraní, který umožňuje přístup k kvalifikátorům vlastnosti. `ppQualSet` nelze `null`. Pokud dojde k chybě, nový objekt se nevrátí a ukazatel je nastaven tak, aby odkazoval na `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná metoda neexistuje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | Funkce se pokusí získat kvalifikátory systémové vlastnosti. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) .

Volání této funkce je podporováno pouze v případě, že aktuální objekt je definice třídy modelu CIM. Manipulace s metodou není k dispozici pro ukazatele [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , které odkazují na instance CIM.

Vzhledem k tomu, že každá metoda může mít své vlastní kvalifikátory, [ukazatel IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit tyto kvalifikátory.

Vzhledem k tomu, že systémové vlastnosti nemají žádné kvalifikátory, funkce vrátí `WBEM_E_SYSTEM_PROPERTY`, pokud se pokusíte získat ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pro vlastnost systému.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
