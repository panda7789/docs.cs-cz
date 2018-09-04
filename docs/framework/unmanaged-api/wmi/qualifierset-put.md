---
title: Funkce QualifierSet_Put (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_Put zapisuje s názvem kvalifikátoru a její hodnotu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b2e1b08d1091e482c6b02fe015a58219ff80768
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517558"
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put – funkce
Zapíše s názvem kvalifikátoru a hodnotu. Nový kvalifikátor přepíše předchozí hodnotu se stejným názvem. Pokud kvalifikátor buď neexistuje, vytvoří se. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[in] Tento parametr se nepoužívá.

`ptr`   
[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

`wszName`   
[in] Název kvalifikátor pro zápis.

`pVal` [in] Ukazatel na platný `VARIANT` , který obsahuje kvalifikátor pro zápis. Tento parametr nemůže mít `null`.

`lFlavor` [in] Jeden z následujících konstant, které definuje požadovaný flavor u tohoto kvalifikátoru. Výchozí hodnota je `WBEM_FLAVOR_OVERRIDABLE` (0).

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Kvalifikátor se dá přepsat v odvozené třídě nebo instanci. **Toto je výchozí hodnota.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Kvalifikátor je postoupena do instance. |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Kvalifikátor je postoupena do odvozené třídy. |
| "WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | Kvalifikátor nelze přepsat v odvozené třídě nebo instanci. |
| "WBEM_FLAVOR_AMENDED | 0x80 | Kvalifikátor je lokalizován. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Došlo k neplatnému pokusu určit **klíč** kvalifikátor na vlastnost, která nemůže být klíč. Klíče jsou zadány om c; detaily třídy definice objektu a nelze je měnit na základě jednotlivé instance. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametr není platný typ kvalifikátoru. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Není možné volat `QualifierSet_Put` metoda na kvalifikátor, protože vlastnící objekt nepovoluje přepíše. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) metody.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
