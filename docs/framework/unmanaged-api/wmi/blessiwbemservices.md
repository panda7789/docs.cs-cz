---
title: BlessIWbemServices – funkce (Reference nespravovaného rozhraní API)
description: Funkce BlessIWbemServices určuje, zda přihlašovací údaje uživatele povolují přístup ke třídě služby IWbem.
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
ms.openlocfilehash: 57ab5eb418b5f0a9175074c87837c7cac8936346
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799055"
---
# <a name="blessiwbemservices-function"></a>Funkce BlessIWbemServices
Určuje, zda přihlašovací údaje uživatele povolují přístup k zadané třídě [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) .   
  
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

`pIWbemServices`\
pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , pro který jsou požadována oprávnění.

`strUser`\
pro Uživatelské jméno

`strPassword`\
pro Heslo přidružené `strUser`k.

`strAuthority`\
pro Název domény uživatele Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

`impLevel`\
pro Úroveň zosobnění.

`authnLevel`\
pro Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *Winerror. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden nebo více argumentů je neplatných. |
| `E_POINTER` | 0x80004003 | `pIWbemServices`je `null`. | 
| `E_FAIL` | 0x80000008 | Došlo k neurčené chybě. |
| `E_OUTOFMEMORY` | 0x80000002 | K provedení této operace je k dispozici dostatek paměti. | 
| `S_OK` | 0 | Volání funkce bylo úspěšné. | 

## <a name="requirements"></a>Požadavky  

 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
