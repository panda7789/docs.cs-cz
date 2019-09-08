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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de36650aa2b206b5e9734b38c6067a3a79de610c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798791"
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

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinace příznaků v `lEnumFlags` není platná nebo byl zadán neplatný argument. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` bylo provedeno bez navýšení [`EndEnumeration`](endenumeration.md)volání. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K zahájení nového výčtu není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: funkce BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.  Můžete zkombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny. Příznaky ze stejné skupiny se však vzájemně vylučují. 

**Skupina 1**

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zahrňte pouze vlastnosti, které tvoří klíč. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zahrnout vlastnosti, které jsou pouze odkazy na objekty. |

**Skupina 2**

Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Omezte výčet jenom na systémové vlastnosti. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zahrnutí místních a rozšířících vlastností, ale vyloučení systémových vlastností z výčtu. |

Pro třídy:

Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Omezte výčet na vlastnosti přepsané v definici třídy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Omezte výčet na vlastnosti přepsané v aktuální definici třídy a na nové vlastnosti definované ve třídě. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Maska (nikoli příznak), která se má použít `lEnumFlags` na hodnotu, chcete- `WBEM_FLAG_CLASS_OVERRIDES_ONLY` li zjistit, `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` zda je nastavena hodnota nebo. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na vlastnosti, které jsou definovány nebo změněny ve třídě samotné. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd. |

Instance:

Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na vlastnosti, které jsou definovány nebo změněny ve třídě samotné. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd. |

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
