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
ms.openlocfilehash: 2d20701237501834c611c4e498c39597cf275176
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407031"
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration – funkce
Návrat na začátek výčtu enumerátor kvalifikátory objektu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[in] Tento parametr se nepoužívá.

`ptr`   
[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`lFlags`   
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
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vrátíte pouze názvy kvalifikátory konkrétní aktuální vlastnost nebo objekt. <br/> Pro vlastnost: vracet jenom v kvalifikátorech specifické pro vlastnost (včetně potlačení), a ne těchto kvalifikátory rozšířena z definice třídy. <br/> Pro instanci: vrátit pouze názvy instancí kvalifikátoru. <br/> Pro třídu: vracet jenom kvalifikátory jsou specifické pro beiong třída odvozena.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Vrátit pouze názvy kvalifikátory rozšířena z jiného objektu. <br/> Pro vlastnost: vrátit jenom v kvalifikátorech rozšíří na tuto vlastnost z definice třídy a ne ty ze samotné vlastnosti. <br/> Pro instanci: vrátit pouze ty kvalifikátory rozšířena z definice třídy. <br/> Pro třídu: vrátit pouze názvy kvalifikátor zděděná z nadřazené třídy. |

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
