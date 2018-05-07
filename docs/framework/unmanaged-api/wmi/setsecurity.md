---
title: Funkce SetSecurity (referenční dokumentace nespravovaného rozhraní API)
description: Funkce SetSecurity načte token zosobnění aktuální vlákno.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fd354e1103832abee7f634eace3dd6defa8b646
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="setsecurity-function"></a>SetSecurity – funkce
Načte token zosobnění přidružené k aktuální vlákno.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a>Parametry

`pNeedToReset` [out] Když funkce vrátí, obsahuje odkazy `boolean` určující, zda má být token resetovat voláním [ResetSecurity](resetsecurity.md) funkce.  

`token`  
[out] Když funkce vrátí hodnotu, obsahuje ukazatel na popisovač token zosobnění přidružené k aktuální vlákno. Jeho hodnota může být `null` Pokud neexistuje žádné token přidružené k aktuální vlákno. 

## <a name="return-value"></a>Návratová hodnota

Pokud funkci úspěšné, je vrácenou hodnotu `S_OK` (0).

V případě selhání funkce návratovou hodnotu je kód chyby nulová. Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
