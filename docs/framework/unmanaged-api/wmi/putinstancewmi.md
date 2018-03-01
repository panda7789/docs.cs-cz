---
title: "Funkce PutInstanceWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce PutInstanceWmi vytvoří nebo aktualizuje existující třídy instance."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1996103eea87562226537f9aa90dc337c56313c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi – funkce
Vytvoří nebo aktualizuje existující třídy instance. Instance je zapsán do úložiště služby WMI. 

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
[v] Ukazatel na instanci být writen.

`lFlags`   
[v] Kombinace příznaky, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu: 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud nastavíte, rozhraní WMI nejsou uložené žádné kvalifikátory s **Amended** příchuť. </br> Není-li sadu, se předpokládá, že není lokalizované tento objekt a všechny kvalifikátory jsou storedwith této instance. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Vytvořte instanci, pokud ji neexistuje, nebo ho přepíše, pokud již existuje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Aktualizace instance. Instance musí existovat volání úspěšné. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Vytvoření instance. Volání selže, pokud instance již existuje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že polosynchronní volání. |

`pCtx`  
[v] Obvykle je tato hodnota `null`. Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadované třídy. 

`ppCallResult`  
[out] Pokud `null`, tento parametr se nepoužívá. Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí okamžitě s `WBEM_S_NO_ERROR`. `ppCallResult` Parametr obdrží ukazatel na novou [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objektu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k aktualizaci instanci zadané třídy. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Třída podporuje tato instance není platný. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null` zadaná pro vlastnost, která nemůže být `null`, například u takové, která je označena kvalifikátorem **indexované** nebo **Not_Null** kvalifikátor. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Zadaná instance není platný. (Například volání `PutInstanceWmi` s třídou vrací hodnotu této.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, instance však již existuje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`byl zadán v `lFlags`, ale instance neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) metoda.

`PutInstanceWmi` Funkce podporuje vytváření instancí a aktualizace instancí pouze existující třídy.  V závislosti na tom, jak `pCtx` parametr je nastaven, jsou aktualizovány některé nebo všechny vlastnosti instance. 

Pokud instance na kterou odkazuje `pInst` patří do podtřídy, Správa systému Windows volání všech poskytovatelů zodpovědná za třídy, ze kterých je odvozena podtřídy. Všechny tyto zprostředkovatele musí být úspěšně pro původní `PutInstanceWmi` žádost proběhla úspěšně. Zprostředkovatel podpora nejhornější třídy v hierarchii jako první. Pořadí volání pokračuje podtřídou třídy nejhornější a pokračuje shora dolů, dokud nedosáhne Správa systému Windows zprostředkovatele pro třídu vlastnící instanci, na kterou odkazuje `pInst`.
Správa systému Windows nevyvolá pro některý z podřízených tříd instance zprostředkovatele. 

Když se aplikace musí aktualizace instanci, která patří do hierarchie tříd, `pInst` parametr musí odkazovat na instanci obsahující vlastnosti, které chcete upravit. To znamená, zvažte cílová instance, které patří do **ClassB**. **ClassB** instance je odvozena z **ClassA**, a **ClassA** definuje vlastnost **PropA**. Pokud aplikace chce změňte na hodnotu **PropA** v **ClassB** instanci, je nutné nastavit `pInst` do této instance, a nikoli instanci **ClassA** .

Volání metody `PutInstanceWmi` v instanci abstraktní třídy není povoleno.

Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
