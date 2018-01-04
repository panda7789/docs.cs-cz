---
title: "Funkce BeginEnumeration – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce funkce BeginEnumeration obnoví enumerátor na začátku výčtu"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginEnumeration
helpviewer_keywords: BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90c3e8448a61145290ea4a75b1d38f7ae010cb9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="beginenumeration-function"></a>Funkce BeginEnumeration – funkce
Obnoví enumerátor zpět na začátek výčtu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`lEnumFlags`  
[v] Bitová kombinace příznaků nebo hodnoty, které jsou popsané v [poznámky](#remarks) oddíl, který určuje vlastnosti zahrnuté ve výčtu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Zadaná kombinace příznaků v `lEnumFlags` je neplatný nebo neplatný argument byl zadán. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` byl proveden bez použité volání [ `EndEnumeration` ](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici zahájíte nové – výčet není dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) metoda.

Příznaky, které lze předat jako `lEnumFlags` argument jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu.  Můžete kombinovat jeden příznak z každé skupiny libovolný příznakem z jiné skupiny. Příznaky ze stejné skupiny jsou však vzájemně vylučují. 

**Skupina 1**

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Obsahovat vlastnosti, které tvoří pouze klíč. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Obsahovat vlastnosti, které jsou pouze odkazy na objekty. |

**Skupina 2**

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Omezte výčtu pouze vlastnosti systému. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Obsahovat místní a šířený vlastnosti ale vyloučit vlastnosti systému z výčtu. |

Pro třídy:

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Omezte výčtu vlastnosti přepsání v definici třídy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Omezte výčtu vlastnosti přepsání v aktuální definici třídy a vlastnosti nového definovaný ve třídě. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | A maskování (místo příznak) použít proti `lEnumFlags` hodnota ke kontrole, pokud má jedna `WBEM_FLAG_CLASS_OVERRIDES_ONLY` nebo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` nastavena. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet vlastností, které jsou definované ani upravit v vlastní třídy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet vlastností, které se dědí z třídy base. |

Pro instance:

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet vlastností, které jsou definované ani upravit v vlastní třídy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet vlastností, které se dědí z třídy base. |


## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
