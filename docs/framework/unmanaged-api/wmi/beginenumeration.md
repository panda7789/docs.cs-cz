---
title: Funkce BeginEnumeration (Unmanaged API Reference)
description: Funkce BeginEnumeration resetuje čítač výčtu na začátek výčtu.
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176874"
---
# <a name="beginenumeration-function"></a>Funkce BeginEnumeration
Obnoví čítač výčtu zpět na začátek výčtu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>Parametry

`vFunc`\
[v] Tento parametr není použit.

`ptr`\
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lEnumFlags`\
[v] Bitová kombinace příznaků nebo hodnot popsaných v části [Poznámky,](#remarks) která řídí vlastnosti zahrnuté ve výčtu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinace příznaků v `lEnumFlags` aplikaci je neplatná nebo byl zadán neplatný argument. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` bylo provedeno bez zasahování volání [`EndEnumeration`](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Není k dispozici dostatek paměti pro zahájení nového výčtu. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [metody IWbemClassObject::BeginEnumeration.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

Příznaky, které mohou být `lEnumFlags` předány jako argument jsou definovány v souboru hlavičky *WbemCli.h,* nebo je můžete definovat jako konstanty v kódu.  Můžete kombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny. Příznaky ze stejné skupiny se však vzájemně vylučují.

**Skupina 1**

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zahrnout vlastnosti, které tvoří pouze klíč. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zahrnout vlastnosti, které jsou pouze odkazy na objekty. |

**Skupina 2**

Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Omezte výčet pouze na systémové vlastnosti. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zahrnout místní a rozšířené vlastnosti, ale vyloučit vlastnosti systému z výčtu. |

Pro třídy:

Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Omezte výčet na vlastnosti přepsané v definici třídy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Omezte výčet na vlastnosti přepsané v aktuální definici třídy a na nové vlastnosti definované ve třídě. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Maska (spíše než příznak) použít `lEnumFlags` proti hodnotu `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` zkontrolovat, zda buď nebo je nastavena. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na vlastnosti, které jsou definovány nebo změněny v samotné třídě. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděny ze základních tříd. |

Například:

Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na vlastnosti, které jsou definovány nebo změněny v samotné třídě. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděny ze základních tříd. |

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
