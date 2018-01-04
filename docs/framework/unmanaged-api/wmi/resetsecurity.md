---
title: "Funkce ResetSecurity (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce ResetSecurity přiřadí token zosobnění aktuální vlákno."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bacee65633d25e705d978d3902a6804516a88bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="resetsecurity-function"></a>ResetSecurity – funkce
Přiřadí token poskytnutý zosobnění aktuální vlákno.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>Parametry

`token`  
[v] Token zosobnění pro přidružení aktuální vlákno. Jeho hodnota může být `null`. 

## <a name="return-value"></a>Návratová hodnota

Pokud funkci úspěšné, je vrácenou hodnotu `S_OK` (0).

V případě selhání funkce návratovou hodnotu je kód chyby nulová. Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
