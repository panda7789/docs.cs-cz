---
title: "Funkce QualifierSet_Delete (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_Delete odstraní kvalifikátor podle názvu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9245fc0ee109837249f1f3df400385c117a2f2d7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
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
[v] Tento parametr se nepoužívá.

`ptr`   
[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`wszName`   
[v] Název kvalifikátor odstranit.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` Parametr není platný. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Odstranění této kvalifikátor je neplatný. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nebyl nalezen zadaný kvalifikátor. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Místní přepsání bylo odstraněno a původní kvalifikátor z nadřazeného objektu došlo k obnovení oboru. |

## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) metoda.

Z důvodu kvalifikátor šíření pravidla kvalifikátor konkrétní může byly zděděno z jiného objektu a jenom přepsání v aktuální třídě nebo instanci. V takovém případě `QualifierSet_Delete` metoda obnoví kvalifikátor na jeho původní zděděná hodnota. Funkce v tomto případě vrátí stavový kód `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
