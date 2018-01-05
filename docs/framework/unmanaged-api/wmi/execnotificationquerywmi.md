---
title: "Funkce ExecNotificationQueryWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce ExecNotificationQueryWmi provede dotaz přijímat události."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecNotificationQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecNotificationQueryWmi
helpviewer_keywords: ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6dd0926d2262f8d0aa125b86755017a65a95a7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi – funkce
Provede dotaz přijímat události. Volání vrátí okamžitě a volající může dotazovat vrácený enumerátor pro události, když dorazí. Uvolnění vrácený enumerátor zruší dotazu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExecNotificationQueryWmi (
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
[v] Kombinace následující dvěma příznaky, které ovlivňují chování této funkce. Tyto hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu. 

| Konstanta | Hodnota  | Popis  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že polosynchronní volání. Pokud není nastavený tento příznak, volání selže. Je to proto události při přijetí nepřetržitě, což znamená, že uživatel musí dotazovat vrácený enumerátor. Po neomezenou dobu blokování toto volání provádí, které znemožňuje. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Vrátí enumerátor dopředné. Obvykle dopředných enumerátory je rychlejší a využívají méně paměti než konvenční výčty, ale nepovoluje volání [klon](clone.md). |

`pCtx`  
[v] Obvykle je tato hodnota `null`. Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadovaný události. 

`ppEnum`  
[out] Pokud nedojde k žádné chybě, obdrží má ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu. Najdete v článku [poznámky](#remarks) části Další informace.

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
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které můžou vrátit funkce. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Dotaz Určuje třídu, která neexistuje. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Byla vyžádána příliš mnoho přesnost v doručení událostí. Větší tolerance dotazování musí být zadán. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | Requess dotaz může poskytovat další informace než Správa systému Windows. To `HRESULT` je vrácena, pokud dotaz událostí výsledkem požadavku dotazování všechny objekty v oboru názvů. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Dotaz byl chybu syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Jazyk požadovaný dotaz není podporován. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Dotaz je příliš složitý. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | Dotaz nelze analyzovat. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) metoda.

Po funkce vrátí hodnotu, volající předá pravidelně vrácený `ppEnum` do objektu [Další](next.md) funkce, které chcete zobrazit, pokud jsou k dispozici žádné události.

Existují omezení počtu `AND` a `OR` klíčová slova, která lze použít v dotazech WQL. Velké počty klíčová slova jazyka WQL v dotazu komplexní může způsobit rozhraní WMI se vrátíte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu. Limit klíčová slova jazyka WQL, závisí na tom, jak složitá je dotaz.

Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
