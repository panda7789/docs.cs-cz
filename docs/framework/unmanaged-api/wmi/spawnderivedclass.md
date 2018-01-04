---
title: "Funkce SpawnDerivedClass (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce SpawnDerivedClass vytvoří nový objekt, který je odvozen z objektu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnDerivedClass
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnDerivedClass
helpviewer_keywords: SpawnDerivedClass function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51a0dd0013b1bb3898bcc81ee2d64be20a5b6ecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass – funkce
Vytvoří objekt nově odvozených tříd ze zadaného objektu.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`ppNewClass`  
[out] Obdrží má ukazatel na nový objekt – třída definice. Pokud dojde k chybě, nový objekt, který se vrátí, a `ppNewClass` je ponechat beze změny doleva. Jeho hodnota nemůže být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Neplatná operace, jako například vytvoření třídy z instance, byl požadován. |
| `WBEM_E_INCOMPLETE_CLASS` | Třída zdroje byla plně definována nebo zaregistrována Správa systému Windows, tak nové odvozené třídy není povoleno. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass`je `null`. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) metoda.

`ptr`musí být definice třídy, který se stane nadřazené třídy objektu vytvořeny. Vráceného objektu se změní na podtřídy aktuálního objektu.

Nový objekt vrácený v `ppNewClass` automaticky stane podtřídy aktuálního objektu. Toto chování nelze přepsat. Není k dispozici žádnou jinou metodu, pomocí kterého lze vytvořit podtřídy (odvozené třídy).

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
