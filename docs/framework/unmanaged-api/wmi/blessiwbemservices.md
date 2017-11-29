---
title: "Funkce BlessIWbemServices (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce BlessIWbemServices označuje, zda přihlašovací údaje uživatele povolit přístup do služby IWbem třídy."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BlessIWbemServices
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BlessIWbemServices
helpviewer_keywords: BlessIWbemServices function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67431d4272ac1da4d400a5552c61cf464680b502
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices – funkce
Určuje, zda přihlašovací údaje uživatele povolit přístup k zadané [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) třídy.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parametry

`pIWbemServices`  
[v] Ukazatel [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objekt, pro které jsou potřeba oprávnění.

`strUser`  
[v] Uživatelské jméno.

`strPassword`  
[v] Heslo přidružené k `strUser`.

`strAuthority`[v] Název domény uživatele. Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`impLevel`[v] Úroveň zosobnění.

`authnLevel`[v] Úroveň ověřování.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WinError.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden nebo více argumenty nejsou platné. |
| `E_POINTER` | 0x80004003 | `pIWbemServices`je `null`. | 
| `E_FAIL` | 0x80000008 | Došlo k neurčené chybě. |
| `E_OUTOFMEMORY` | 0x80000002 | K provedení operace není dostatek paměti. | 
| `S_OK` | 0 | Volání funkce byla úspěšná. | 

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
