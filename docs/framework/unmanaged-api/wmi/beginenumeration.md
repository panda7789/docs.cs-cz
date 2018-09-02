---
title: Funkce BeginEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce BeginEnumeration návrat na začátek výčtu enumerátor
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
ms.openlocfilehash: 08406f7d93671b406b3c7cd8719a7a0e5e423184
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392354"
---
# <a name="beginenumeration-function"></a>Funkce BeginEnumeration
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
[in] Tento parametr se nepoužívá.

`ptr` [in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lEnumFlags`  
[in] Bitová kombinace příznaků nebo podle hodnoty [poznámky](#remarks) oddíl, který řídí vlastností obsažených ve výčtu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinace příznaků v `lEnumFlags` není platný nebo neplatný argument byl zadán. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Druhé volání `BeginEnumeration` proběhla bez opětovné volání [ `EndEnumeration` ](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici zahájíte nový výčet. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) metody.

Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.  Můžete kombinovat jeden příznak z každé skupiny s všechny příznaky z jiné skupiny. Ale příznaky ze stejné skupiny se vzájemně vylučují. 

**Skupina 1**

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Obsahovat vlastnosti, které tvoří pouze klíč. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zahrnují vlastnosti, které jsou pouze odkazy na objekty. |

**Skupina 2**

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Omezte výčet pouze vlastnosti systému. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zahrnují vlastnosti místní a rozšíří ale vyloučit vlastnosti systému z výčtu. |

Pro třídy:

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Omezte výčet vlastností přepsat v definici třídy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Omezte výčet vlastností přepsat v aktuální definici třídy a nové vlastnosti definované ve třídě. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | A maskování (místo příznak) Chcete-li použít proti `lEnumFlags` hodnotu a zkontrolujte, zda buď `WBEM_FLAG_CLASS_OVERRIDES_ONLY` nebo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` nastavena. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet vlastností, které jsou definovány nebo upraveny v samotné třídě. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet vlastností, které se dědí ze základní třídy. |

Pro instance:

Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet vlastností, které jsou definovány nebo upraveny v samotné třídě. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet vlastností, které se dědí ze základní třídy. |


## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
