---
title: Funkce ExecQueryWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ExecQueryWmi provede dotaz pro načtení objektů.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b482f2ca2e2d5c06e69945adb71aa6c0f5d26465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="execquerywmi-function"></a>ExecQueryWmi – funkce
Provede dotaz pro načtení objektů.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

`strQueryLanguage`    
[v] Řetězec s platný dotaz jazyk podporovaný Správa systému Windows. Musí být "WQL", zkratka pro rozhraní WMI Query Language.

`strQuery`  
[v] Text dotazu. Tento parametr nemůže být `null`.

`lFlags`   
[v] Kombinace příznaky, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu: 

| Konstanta | Hodnota  | Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud sadu, funkce načte doplněné kvalifikátory uložené v lokalizovaných obor názvů národního prostředí aktuálního připojení. <br/> Pokud není sada, funkce načte pouze kvalifikátory uložené v oboru názvů okamžitou. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že polosynchronní volání. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Vrátí enumerátor dopředné. Obvykle dopředných enumerátory je rychlejší a využívají méně paměti než konvenční výčty, ale nepovoluje volání [klon](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Rozhraní WMI zachová ukazatelé na objekty v enumration, dokud jejich vydání. | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Zajišťuje, že všechny vrátí objekty mají dostatek informací v nich proto této vlastnosti systému, jako například **__PATH**, **__RELPATH**, a **__SERVER**, nejsou `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Tento příznak se používá pro při vytváření prototypu. Ho nepracuje dotaz a místo toho vrátí objekt, který vypadá jako objekt obvykle za následek. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Příčiny přímý přístup k poskytovateli pro zadaná třída bez ohledu na své nadřazené třídy nebo všechny podtřídy. |

Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.

`pCtx`  
[v] Obvykle je tato hodnota `null`. Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadované třídy. 

`ppEnum`  
[out] Pokud nedojde k žádné chybě, obdrží má ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu. Dotaz může mít nulový počet instancí sadě výsledků dotazu. Najdete v článku [poznámky](#remarks) části Další informace.

`authLevel`  
[v] Úroveň ověřování.

`impLevel` [v] Úroveň zosobnění.

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
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které můžou vrátit funkce. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Dotaz byl chybu syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Jazyk požadovaný dotaz není podporován. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Dotaz je příliš složitý. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Dotaz Určuje třídu, která neexistuje. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) metoda.

Tato funkce zpracovává zadaný v dotazu `strQuery` parametr a vytvoří enumerátor, pomocí kterého můžete volající přístup výsledky dotazu. Enumerátor je ukazatel na [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) rozhraní; dotaz výsledky jsou instancemi třídy objektů, které jsou dostupné prostřednictvím [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) rozhraní.

Existují omezení počtu `AND` a `OR` klíčová slova, která lze použít v dotazech WQL. Velké počty klíčová slova jazyka WQL v dotazu komplexní může způsobit rozhraní WMI se vrátíte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu. Limit klíčová slova jazyka WQL, závisí na tom, jak složitá je dotaz.

Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
