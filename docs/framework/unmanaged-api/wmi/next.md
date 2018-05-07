---
title: Funkce Next (referenční dokumentace nespravovaného rozhraní API)
description: Další funkce retireves další vlastnosti ve výčtu.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e945930a9a668d0a1c1e4c26bf3add9cc574c261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="next-function"></a>Další funkce
Načte další vlastnosti v výčet, který začíná volání [funkce BeginEnumeration](beginenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`pstrName`  
[out] Nový `BSTR` obsahující název vlastnosti. Tento parametr můžete nastavit `null` Pokud název není potřeba.

`pVal`  
[out] A `VARIANT` vyplněnou hodnotou vlastnosti. Tento parametr můžete nastavit `null` Pokud hodnota není potřeba. Pokud funkce vrátí kód chyby `VARIANT` předaný `pVal` je ponechat beze změny doleva. 

`pvtType`  
[out] Ukazatel na `CIMTYPE` proměnné ( `LONG` do které je umístěn typu vlastnosti). Hodnota této vlastnosti může být `VT_NULL_VARIANT`, v takovém případě je třeba určit skutečný typ vlastnosti. Tento parametr může být také `null`. 

`plFlavor`  
[out] `null`, nebo hodnotu, která přijímá informace o původu vlastnosti. Možné hodnoty v části [poznámky]. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Byl bez volání [ `BeginEnumeration` ](beginenumeration.md) funkce. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici zahájíte nové – výčet není dostatek paměti. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Vzdálené volání procedur od aktuálním procesem a správa systému Windows se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Ve výčtu nejsou žádné další vlastnosti. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) metoda.

Tato metoda také vrátí hodnotu vlastnosti systému.

Pokud základní typ vlastnosti je cesta k objektu, datum nebo čas nebo jiné speciální typ, pak typ vrácený neobsahuje dostatek informací. Volající musí zkontrolovat `CIMTYPE` pro zadanou vlastnost k určení, zda je vlastnost odkaz na objekt, datum nebo čas nebo jiné speciální typu.

Pokud `plFlavor` není `null`, `LONG` hodnota obdrží informace o zdroji vlastnosti, následujícím způsobem:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systém vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: vlastnost je zděděna od nadřazené třídy. </br> Pro instanci: vlastnost, zatímco zděděn od nadřazené třídy, se nezměnil instance.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pro třídu: vlastnost náleží do odvozené třídy. </br> Pro instanci: vlastnost je upravovat instance; To znamená, že byla zadána hodnota, nebo kvalifikátor byla přidána nebo upravena. |

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
