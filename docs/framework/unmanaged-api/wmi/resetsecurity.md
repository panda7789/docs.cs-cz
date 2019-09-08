---
title: ResetSecurity – funkce (Reference nespravovaného rozhraní API)
description: Funkce ResetSecurity přiřadí aktuálnímu vláknu token zosobnění.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798253"
---
# <a name="resetsecurity-function"></a>ResetSecurity – funkce
Přiřadí zadaný token zosobnění aktuálnímu vláknu.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>Parametry

`token`  
pro Token zosobnění, který má být přidružen k aktuálnímu vláknu. Jeho hodnota může být `null`. 

## <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je `S_OK` (0).

Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby. Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
