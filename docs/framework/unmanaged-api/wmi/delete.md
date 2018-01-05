---
title: "Odstranit funkci (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce odstranění odstraní zadanou vlastnost a všechny jeho kvalifikátory z definice třídy CIM."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30f5bf651990cafe06811019cf2b3d92f866f646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="delete-function"></a>Odstranit – funkce
Odstraní zadanou vlastnost a všechny jeho kvalifikátory z definice třídy CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszName`  
[v] Název vlastnosti, která má odstranit. `wszName`musí být ukazatel na platnou `LPCWSTR`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Vlastnost nelze odstranit. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Formát  `wszzName` je neplatný. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Není k dispozici dostatek paměti pro dokončení operace. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Vlastnost je zděděn ze základní třídy. |
| `WBEM_E_SYSTEM_PROPERTY` | | Vlastnost je vlastnost systému. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | Funkce odstranit výchozí hodnotu přepsání pro aktuální třídu. Výchozí hodnota pro tuto vlastnost v nadřazené třídě byl reactiviated. | 

## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) metoda.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
