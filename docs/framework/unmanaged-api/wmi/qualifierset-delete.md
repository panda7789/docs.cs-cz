---
title: Funkce QualifierSet_Delete (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_Delete odstraní kvalifikátor podle názvu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca4cc9fb65d1a4bd8713f969bbda5551ce5a2e2
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325377"
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete – funkce
Odstraní zadaný kvalifikátor podle názvu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`   
[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`wszName`   
[in] Název kvalifikátor odstranit.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` Parametr není platný. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Odstraňuje se tento kvalifikátor je neplatný. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný kvalifikátor se nenašel. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Místní přepsání byl odstraněn a oboru došlo k obnovení původního kvalifikátor z nadřazeného objektu. |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) metody.

Z důvodu pravidla pro šíření kvalifikátor zejména kvalifikátor může byly zděděné z jiného objektu a pouze přepsání v aktuální třídě nebo instanci. V takovém případě `QualifierSet_Delete` způsob, obnovíte na původní hodnotu zděděného kvalifikátor. V tomto případě vrátí stavový kód `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
