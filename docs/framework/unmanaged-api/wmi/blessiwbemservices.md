---
title: Funkce BlessIWbemServices (referenční dokumentace nespravovaného rozhraní API)
description: Funkce BlessIWbemServices označuje, jestli přihlašovací údaje uživatele povolit přístup do služby IWbem třídy.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a65c3c14507b2520c69875a1bc101ce826ace7ba
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934301"
---
# <a name="blessiwbemservices-function"></a>Funkce BlessIWbemServices
Určuje, zda pověření uživatelů odkudkoli přístup k zadané [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) třídy.   
  
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
[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objektu, pro které jsou potřeba oprávnění.

`strUser`  
[in] Uživatelské jméno.

`strPassword`  
[in] Heslo přidružené k `strUser`.

`strAuthority` [in] Název domény uživatele. Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`impLevel` [in] Úroveň zosobnění.

`authnLevel` [in] Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WinError.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden nebo více argumentů nejsou platné. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` je `null`. | 
| `E_FAIL` | 0x80000008 | Došlo k nespecifikované chybě. |
| `E_OUTOFMEMORY` | 0x80000002 | K provedení této operace není dostatek paměti. | 
| `S_OK` | 0 | Volání funkce byla úspěšná. | 

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
