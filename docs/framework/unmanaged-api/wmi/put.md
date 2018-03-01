---
title: "PUT – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce Put přiřadí novou hodnotu s názvem vlastnosti."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09d3edc74b34688d5cc36e688f634850cfb60910
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="put-function"></a>PUT – funkce
Nastaví vlastnost s názvem na novou hodnotu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszName`  
[v] Název vlastnosti. Tento parametr nemůže být `null`.

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`pVal`   
[v] Ukazatel na platnou `VARIANT` , stane se nová hodnota vlastnosti. Pokud `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`, je nastavena na `null`. 

`vtType`  
[v] Typ `VARIANT` na kterou odkazuje `pVal`. Najdete v článku [poznámky](#remarks) části Další informace.
 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Typ vlastnosti nebyl rozpoznán. Tato hodnota se vrátí při vytváření instancí třídy, pokud třída již existuje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Pro instance: Určuje, že `pVal` odkazuje na `VARIANT` nesprávného typu pro vlastnost. <br/> Definice třídy: vlastnost již existuje v nadřazené třídě a nový typ COM se liší od původního COM typu. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metoda.

Tato funkce vždy přepíše aktuální hodnota vlastnosti novou. Pokud [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) odkazuje na definice třídy, `Put` vytvoří nebo aktualizuje hodnotu vlastnosti. Když [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) odkazuje na instanci CIM, `Put` aktualizuje jenom; hodnota vlastnosti `Put` nelze vytvořit hodnotu vlastnosti.

`__CLASS` Systému vlastnost je pouze s možností zápisu během vytváření třídy, když se nemusí být ponecháno prázdné. Všechny ostatní vlastnosti systému jsou jen pro čtení.

Uživatele nelze vytvořit vlastnosti s názvy, které začínat ani končit podtržítko ("_"). Toto je vyhrazená pro systém třídy a vlastnosti.

Pokud je vlastnost nastavena `Put` funkce existuje v nadřazené třídě, výchozí hodnota vlastnosti je změnit, dokud se vlastnost typ neodpovídá typu nadřazené třídy. Pokud se nejedná o neshodě typů vlastnost neexistuje, je vlastnost ceated.

Použití `vtType` parametr pouze při vytváření nové vlastnosti v definici třídy CIM a `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`. V takovém případě `vType` parametr určuje typ modelu CIM vlastnosti. V každém případě `vtType` musí být 0. `vtType`musí také být 0, pokud je základní objekt instancí (i když `Val` je `null`) vzhledem k tomu, že typem vlastnosti je pevná a nelze změnit.   

## <a name="example"></a>Příklad

Příklad, naleznete v části [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metoda.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
