---
title: BlessIWbemServices funkce (Unmanaged API Reference)
description: Funkce BlessIWbemServices označuje, zda pověření uživatele povolit přístup ke třídě IWbemServices.
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
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176861"
---
# <a name="blessiwbemservices-function"></a>Funkce BlessIWbemServices
Označuje, zda pověření uživatele povolit přístup k zadané [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) třídy.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
[v] Ukazatel na objekt [IWbemServices,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) pro který jsou vyžadována oprávnění.

`strUser`\
[v] Uživatelské jméno.

`strPassword`\
[v] Heslo přidružené `strUser`k souboru .

`strAuthority`\
[v] Název domény uživatele. Další informace naleznete ve funkci [ConnectServerWmi.](connectserverwmi.md)

`impLevel`\
[v] Úroveň zosobnění.

`authnLevel`\
[v] Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WinError.h* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Jeden nebo více argumentů je neplatných. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` je `null`. |
| `E_FAIL` | 0x80000008 | Došlo k nespecifikované chybě. |
| `E_OUTOFMEMORY` | 0x80000002 | K provedení operace není k dispozici dostatek paměti. |
| `S_OK` | 0 | Volání funkce bylo úspěšné. |

## <a name="requirements"></a>Požadavky  

 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
