---
title: "Funkce QualifierSet_Put (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_Put zapíše pojmenované kvalifikátor a její hodnotu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Put
helpviewer_keywords: QualifierSet_Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bf5c6dbf0f707942d58f4d7cf155636f0532724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put – funkce
Zapíše kvalifikátor s názvem a hodnotou. Nový kvalifikátor přepíše předchozí hodnotu se stejným názvem. Pokud kvalifikátor neexistuje, vytvoří se. 

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
[v] Tento parametr se nepoužívá.

`ptr`   
[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`wszName`   
[v] Název kvalifikátor k zápisu.

`pVal`[v] Ukazatel na platnou `VARIANT` obsahující kvalifikátor k zápisu. Tento parametr nemůže být `null`.

`lFlavor`[v] Jeden z následujících konstanty, které definuje typů kvalifikátor požadované pro tento kvalifikátor. Výchozí hodnota je `WBEM_FLAVOR_OVERRIDABLE` (0).

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Kvalifikátor můžete přepsání v odvozené třídě nebo instanci. **Toto je výchozí hodnota.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Kvalifikátor je rozšířena do instance. |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Kvalifikátor je rozšířena do odvozené třídy. |
| ' WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | Kvalifikátor nelze přepsání v odvozené třídě nebo instanci. |
| ' WBEM_FLAVOR_AMENDED | 0x80 | Kvalifikátor je lokalizované. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Došlo k neplatnému pokusu zadejte **klíč** kvalifikátor u vlastnosti, která nemůže být klíčem. Klíče jsou zadány om c; ass definici objektu a nelze je měnit u jednotlivých instancí. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametr není platný typ kvalifikátoru. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Není možné volat `QualifierSet_Put` metodu kvalifikátor protože vlastnící objekt nepovoluje přepsání. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) metoda.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
