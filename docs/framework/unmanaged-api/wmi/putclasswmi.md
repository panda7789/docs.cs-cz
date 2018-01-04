---
title: "Funkce PutClassWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce PutClassWmi vytvoří novou třídu nebo aktualizuje stávající."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 219cec2096cd3d1dfe1e0d3c0903b62692e444e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="putclasswmi-function"></a>PutClassWmi – funkce
Vytvoří novou třídu nebo aktualizuje stávající.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parametry

`pObject`    
[v] Ukazatel na definici platnou třídu. Je nutné správně inicializovat hodnoty všech požadovaná vlastnost.

`lFlags`   
[v] Kombinace příznaky, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu: 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud sadu rozhraní WMI nejsou uložené žádné kvalifikátory s změněné příchuť. </br> Není-li sadu, se předpokládá, že není lokalizované tento objekt a všechny kvalifikátory jsou storedwith této instance. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Vytvořte třídu, pokud ji neexistuje, nebo ho přepíše, pokud již existuje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Aktualizace třídy. Třída musí existovat volání úspěšné. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Vytvořte třídu. Volání selže, pokud třída již existuje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že polosynchronní volání. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Zprostředkovatelé nabízené musíte zadat Tento příznak při volání metody `PutClassWmi` indikující, že tato třída se změnila. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Umožňuje aktualizovat, pokud nejsou žádné odvozené třídy a žádné instance této třídy třídu. Také umožňuje provést aktualizace ve všech případech, pokud tato změna se používá pouze pro důležitý kvalifikátory, například popis kvalifikátor. Pokud existuje instance dané třídy nebo změny mají důležité kvalifikátory, že se aktualizace nezdaří. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Umožňuje aktualizaci tříd, i když jsou podřízené třídy tak dlouho, dokud změnu nezpůsobí případné konflikty s podřízenými třídami. Tento příznak umožňuje například novou vlastnost být přidán do základní třídy, která nebyla dosud v některém z podřízené třídy. Pokud existuje instance dané třídy, že se aktualizace nezdaří. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | vynutí aktualizaci tříd, pokud existuje konflikt s podřízenými třídami. Tento příznak například vynutí aktualizaci, když třída kvalifikátor je definována v podřízené třídy a základní třídy se pokusí přidat stejné kvalifikátor, který je v konfliktu s existující jeden thte. V režimu force tis konflikt vyřešit odstraněním konfliktní kvalifikátor ve třídě podřízené. |

`pCtx`  
[v] Obvykle je tato hodnota `null`. Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadované třídy. 

`ppCallResult`  
[out] Pokud `null`, tento parametr se nepoužívá. Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí okamžitě s `WBEM_S_NO_ERROR`. `ppCallResult` Parametr obdrží ukazatel na novou [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objektu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k vytvoření nebo úpravě třídy. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Zadaná třída není platná. Obvykle, znamená to, že `pObject` určuje instanci objektu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Zadaná třída název je neplatný. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Došlo pokusu o provedení změny, které by způsobily neplatnost podtřídy. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, ale třída již existuje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`byl zadán v `lFlags`, a třída nebyla nalezena. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Požadované vlastnosti pro třídy, ne všechny byly nastaveny. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) metoda.

Uživatel nemusí vytvoření třídy s názvy, které začínat ani končit chacater podtržítko

Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
