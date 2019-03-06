---
title: Funkce QualifierSet_BeginEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_BeginEnumeration resetuje enumerátor kvalifikátory objektu.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375412"
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration – funkce

Návrat na začátek výčtu enumerátor kvalifikátory objektu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
[in] Tento parametr se nepoužívá.

`ptr`\
[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`lFlags`\
[in] Bitová kombinace příznaků nebo podle hodnoty [poznámky](#remarks) oddíl, který určuje kvalifikátory zahrnout do výčtu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametr není platný. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `QualifierSet_BeginEnumeration` proběhla bez opětovné volání [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici zahájíte nový výčet. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) metody.

K vytvoření výčtu všech kvalifikátory pro objekt, musí tuto metodu volat před prvním volání [QualifierSet_Next](qualifierset-next.md). Pořadí, ve kterém jsou uvedené kvalifikátory je zaručeno, že bude neutrální pro daný výčet.

Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|  | 0 | Vrátí názvy všech kvalifikátory. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátíte pouze názvy kvalifikátory konkrétní aktuální vlastnost nebo objekt. <br/> Pro vlastnost: Vrátí jenom v kvalifikátorech specifické pro vlastnost (včetně potlačení) a ne kvalifikátory, rozšířena z definice třídy. <br/> Pro instanci: Vrátíte pouze názvy instancí kvalifikátoru. <br/> Pro třídu: Vrátíte pouze kvalifikátory konkrétní třídy je odvozený.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Vrátit pouze názvy kvalifikátory rozšířena z jiného objektu. <br/> Pro vlastnost: Vrátit se rozšířit jenom v kvalifikátorech k této vlastnosti z definice třídy a ne ty ze samotné vlastnosti. <br/> Pro instanci: Vrátit pouze ty kvalifikátory rozšířena z definice třídy. <br/> Pro třídu: Vrátit pouze názvy kvalifikátor zděděná z nadřazené třídy. |

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)