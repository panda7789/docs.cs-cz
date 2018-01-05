---
title: "Funkce CreateInstanceEnumWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce CreateInstanceEnumWmi vrací enumerátor obsahující instance dané třídy, které splňují kritéria pro výběr."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateInstanceEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateInstanceEnumWmi
helpviewer_keywords: CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b796771b07dee28470d37ca3e4292c0a244e056b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createinstanceenumwmi-function"></a>CreateInstanceEnumWmi – funkce
Vrátí enumerátor, který vrátí instance dané třídy, které splňují kritéria zadaná výběru. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a>Parametry

`strFilter`    
[v] Název třídy, pro kterou instancí potřeby. Tento parametr nemůže být `null`.

`lFlags`   
[v] Kombinace příznaky, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu: 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud sadu, funkce načte doplněné kvalifikátory uložené v lokalizovaných obor názvů národního prostředí aktuálního připojení. <br/> Pokud není sada, funkce načte pouze kvalifikátory uložené v oboru názvů okamžitou. |
| `WBEM_FLAG_DEEP` | 0 | Výčet obsahuje tento a všechny podtřídy v hierarchii. |
| `WBEM_FLAG_SHALLOW` | 1 | Výčet obsahuje pouze čistý instance této třídy a vyloučí všechny instance podtříd zadat vlastnosti nebyl nalezen v této třídě. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že polosynchronní volání. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Vrátí enumerátor dopředné. Obvykle dopředných enumerátory je rychlejší a využívají méně paměti než konvenční výčty, ale nepovoluje volání [klon](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Rozhraní WMI zachová ukazatelé na objekty v enumration, dokud jejich vydání. | 

Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.

`pCtx`  
[v] Obvykle je tato hodnota `null`. Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která může být používán zprostředkovatele, který poskytuje požadovaný instancí.

`ppEnum`  
[out] Obdrží má ukazatel na enumerátor.

`authLevel`  
[v] Úroveň ověřování.

`impLevel`[v] Úroveň zosobnění.

`pCurrentNamespace`   
[v] Ukazatel na [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objekt, který představuje aktuální obor názvů.

`strUser`   
[v] Uživatelské jméno. Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`strPassword`   
[v] Heslo. Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`strAuthority`   
[v] Název domény uživatele. Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k zobrazení instance pro zadanou třídu. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strFilter`neexistuje. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) metoda.

Všimněte si, že vrácený enumerátor může mít nulovým počtem elementů.

Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
