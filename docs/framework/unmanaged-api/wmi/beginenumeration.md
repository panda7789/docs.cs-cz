---
title: Funkce BeginEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce funkce BeginEnumeration resetuje enumerátor na začátek výčtu.
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
ms.openlocfilehash: 9e467234a45ae702a5b77a5f0fa8b75d4ff03c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124135"
---
# <a name="beginenumeration-function"></a>Funkce BeginEnumeration
Obnoví enumerátor zpět na začátek výčtu.  

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
pro Tento parametr se nepoužívá.

`ptr`\
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lEnumFlags`\
pro Bitová kombinace příznaků nebo hodnot popsaných v oddílu [poznámky](#remarks) , které řídí vlastnosti zahrnuté ve výčtu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinace příznaků v `lEnumFlags` je neplatná nebo byl zadán neplatný argument. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` bylo provedeno bez navýšení volání [`EndEnumeration`](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: funkce BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Příznaky, které mohou být předány jako argument `lEnumFlags`, jsou definovány v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.  Můžete zkombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny. Příznaky ze stejné skupiny se však vzájemně vylučují. 

**Skupina 1**

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zahrňte pouze vlastnosti, které tvoří klíč. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zahrnout vlastnosti, které jsou pouze odkazy na objekty. |

**Skupina 2**

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Omezte výčet jenom na systémové vlastnosti. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zahrnutí místních a rozšířících vlastností, ale vyloučení systémových vlastností z výčtu. |

Pro třídy:

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Omezte výčet na vlastnosti přepsané v definici třídy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Omezte výčet na vlastnosti přepsané v aktuální definici třídy a na nové vlastnosti definované ve třídě. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Maska (nikoli příznak), která se má použít u `lEnumFlags` hodnoty, aby zkontrolovala, jestli je nastavená možnost `WBEM_FLAG_CLASS_OVERRIDES_ONLY` nebo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na vlastnosti, které jsou definovány nebo změněny ve třídě samotné. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd. |

Instance:

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na vlastnosti, které jsou definovány nebo změněny ve třídě samotné. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd. |

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
