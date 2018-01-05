---
title: "Funkce BlessIWbemServicesObject (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce BlessIWbemServicesObject označuje, zda přihlašovací údaje uživatele povolit přístup k objektu služby IWbem"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BlessIWbemServicesObject
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BlessIWbemServicesObject
helpviewer_keywords: BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2430358e5ea21468c2e975c2a26f20fe801ee546
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject – funkce
Určuje, zda pověření uživatelů povolit přístup k zadané [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objektu.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parametry

`pIWbemServices`  
[v] Ukazatel na objekt služby WMI.

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
