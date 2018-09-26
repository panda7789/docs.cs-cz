---
title: Funkce PutInstanceWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce PutInstanceWmi vytvoří nebo aktualizuje instance existující třídy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67abf017040b9e6bbe9b10e560c8d57c124ae84e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196639"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi – funkce
Vytvoří nebo aktualizuje instance existující třídy. Instance se zapisují do úložiště služby WMI. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parametry

`pInst`    
[in] Ukazatel na instance, která má být writen.

`lFlags`   
[in] Kombinace příznaků, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu: 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud nastavíte, WMI neukládá všechny kvalifikátory s **Amended** charakter. </br> Pokud není sada, předpokládá se, že tento objekt není lokalizována, a všechny kvalifikátory jsou storedwith této instance. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Vytvořte instanci, pokud ho neexistuje, nebo ho přepíše, pokud již existuje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Aktualizace instance. Instance musí existovat volání k dosažení úspěchu. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Vytvoření instance. Volání selže, pokud instanci již existuje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že volání semisynchronní volání. |

`pCtx`  
[in] Obvykle je tato hodnota `null`. V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy. 

`ppCallResult`  
[out] Pokud `null`, tento parametr se nepoužívá. Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí hodnotu okamžitě s `WBEM_S_NO_ERROR`. `ppCallResult` Parametr přijímá ukazatel na novou [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) objektu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k aktualizaci instance dané třídy. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k nespecifikované chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Třídu podporující tuto instanci není platný. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null` zadaná pro vlastnost, která nemůže být `null`, jako je ten, který je označen **indexovat** nebo **Not_Null** kvalifikátoru. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Zadaná instance není platný. (Například voláním `PutInstanceWmi` s třídou vrátí tuto hodnotu.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, ale instanci již existuje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` byl zadán v `lFlags`, ale instance neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) metody.

`PutInstanceWmi` Funkce podporuje vytváření instancí a aktualizaci instance pouze existující třídy.  V závislosti na tom, jak `pCtx` parametr je nastaven, některé nebo všechny vlastnosti instance se aktualizují. 

Když instance odkazované `pInst` patří na podtřídu Windows Management volání všichni poskytovatelé za tříd, z něhož pochází podtřídy. Všechny tyto zprostředkovatele musí být úspěšně pro původní `PutInstanceWmi` žádost proběhla úspěšně. Nejprve se nazývá poskytovatele podpora nejvyšší třídy v hierarchii. Pořadí volání pokračuje podtřídou třídy nejvyšší třídy a pokračuje shora dolů, dokud nedosáhne Windows Management provider pro třídu vlastnící instanci, na které odkazuje `pInst`.
Správa Windows nevolá zprostředkovatele pro všechny instance podřízené třídy. 

Pokud aplikace musí aktualizovat instance, která patří do hierarchie tříd `pInst` parametr musí odkazovat na instanci obsahující vlastnosti, které chcete upravit. To znamená, vezměte v úvahu cílová instance, která patří do **ClassB**. **ClassB** instance je odvozena z **ClassA**, a **ClassA** definuje vlastnost **PropA**. Pokud aplikace chce provést změnu na hodnotu **PropA** v **ClassB** instance, je nutné nastavit `pInst` pro tuto instanci spíše než instance **ClassA** .

Volání `PutInstanceWmi` na instanci abstraktní třídy není povolený.

Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
