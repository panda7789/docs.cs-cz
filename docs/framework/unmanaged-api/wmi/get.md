---
title: "Get – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce Get načte zadanou hodnotu vlastnosti."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Get
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Get
helpviewer_keywords: Get function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75329ee4ee925f4eb74d96d8ce7ef3145eb4a966
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="get-function"></a>Get – funkce
Pokud existuje, načte zadanou hodnotu vlastnosti.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
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

`wszName`  
[v] Název vlastnosti.

`lFlags`[v] Vyhrazena. Tento parametr musí být 0.

`pVal`[out] Pokud funkce vrátí úspěšně, obsahuje hodnotu `wszName` vlastnost. `pval` Argument je přiřazen správný typ a hodnotu pro kvalifikátor.

`pvtType`[out] Pokud funkce vrátí úspěšně, obsahuje [typ modelu CIM konstanta](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) určující typ vlastnosti. Jeho hodnota může být také `null`. 

`plFlavor`[out] Pokud funkce vrátí úspěšně, obdrží informace o zdroji vlastnosti. Jeho hodnota může být `null`, nebo jeden z následujících WBEM_FLAVOR_TYPE konstanty definované v *WbemCli.h* hlavičkový soubor: 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systém vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: vlastnost je zděděna od nadřazené třídy. </br> Pro instanci: vlastnost, zatímco zděděn od nadřazené třídy, se nezměnil instance.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pro třídu: vlastnost náleží do odvozené třídy. </br> Pro instanci: vlastnost je upravovat instance; To znamená, že byla zadána hodnota, nebo kvalifikátor byla přidána nebo upravena. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost nebyla nalezena. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) metoda.

`Get` Funkce mohou vracet vlastnosti systému.

`pVal` Argument je přiřazen správný typ a hodnotu pro kvalifikátor a knihovny COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) – funkce

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
