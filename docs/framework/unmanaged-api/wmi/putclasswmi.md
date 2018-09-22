---
title: Funkce PutClassWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce PutClassWmi vytvoří novou třídu nebo aktualizuje nějakou existující.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de08662a825a84f19a40863cf73481d89364ebd0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568086"
---
# <a name="putclasswmi-function"></a>PutClassWmi – funkce
Vytvoří novou třídu nebo aktualizuje nějakou existující.  

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
[in] Ukazatel na platnou definicí třídy. To musí být správně inicializován se všemi hodnotami požadovaná vlastnost.

`lFlags`   
[in] Kombinace příznaků, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu: 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud sada WMI neukládá všechny kvalifikátory s upravenou charakter. </br> Pokud není sada, předpokládá se, že tento objekt není lokalizována, a všechny kvalifikátory jsou storedwith této instance. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Vytvořte třídu, pokud ho neexistuje, nebo ho přepíše, pokud již existuje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Aktualizace třídy. Třída musí existovat volání k dosažení úspěchu. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Vytvořte třídu. Volání selže, pokud třída již existuje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že volání semisynchronní volání. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Poskytovatelé nabízených oznámení musíte zadat Tento příznak, při volání metody `PutClassWmi` k označení, že došlo ke změně této třídy. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Umožňuje třídy aktualizace, pokud neexistují žádné odvozené třídy a bez instance dané třídy. Také umožňuje instalaci aktualizací ve všech případech, pokud se tato změna je to důležitý kvalifikátory, jako je například kvalifikátor popis. Pokud existuje instance dané třídy nebo změny jsou důležité kvalifikátory, že se aktualizace nezdaří. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Umožňuje instalaci aktualizací tříd, i když nejsou podřízené třídy za předpokladu, změna nezpůsobí žádné konflikty s podřízenými třídami. Tento příznak například umožňuje nové vlastnosti a přidat základní třídu, která se již bylo zmíněno dříve v některém z podřízených tříd. Pokud má třída instancí, že se aktualizace nezdaří. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | Vynutí aktualizace tříd, pokud existuje konfliktní podřízené třídy. Tento příznak například vynutí aktualizaci, pokud třída kvalifikátor je definována v podřízené třídy a základní třídy se pokusí přidat stejný kvalifikátor, který je v konfliktu s existující jeden thte. V režimu vynucení tis konflikt vyřešit odstraněním konfliktní kvalifikátoru v podřízené třídy. |

`pCtx`  
[in] Obvykle je tato hodnota `null`. V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy. 

`ppCallResult`  
[out] Pokud `null`, tento parametr se nepoužívá. Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí hodnotu okamžitě s `WBEM_S_NO_ERROR`. `ppCallResult` Parametr přijímá ukazatel na novou [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) objektu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k vytvoření nebo úpravě třídy. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k nespecifikované chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Zadaná třída není platná. Obvykle to znamená, že `pObject` určuje objekt instance. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Zadaná třída název je neplatný. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Byl proveden pokus o provést změny, které by způsobily neplatnost podtřídy. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, ale třída již existuje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` byl zadán v `lFlags`, a třída nebyla nalezena. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Požadované vlastnosti pro třídy jsou všechny nastavené. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) metody.

Uživatel nemůže vytvořit třídy s názvy, které začínat ani končit chacater podtržítko

Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
