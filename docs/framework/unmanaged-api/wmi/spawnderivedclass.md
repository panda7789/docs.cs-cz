---
title: SpawnDerivedClass – funkce (Reference nespravovaného rozhraní API)
description: Funkce SpawnDerivedClass vytvoří nový objekt, který je odvozen z objektu.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c213f311f1af1e56d0ce24eba3b76f33be541323
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798226"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass – funkce
Vytvoří nově odvozený objekt třídy ze zadaného objektu.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`ppNewClass`  
mimo Přijme ukazatel na nový objekt definice třídy. Pokud dojde k chybě, nový objekt se nevrátí a `ppNewClass` zůstane beze změny. Jeho hodnota nemůže být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Byla požadována neplatná operace, například vytvoření třídy z instance. |
| `WBEM_E_INCOMPLETE_CLASS` | Třída Source nebyla zcela definována ani registrována se správou systému Windows, takže nová odvozená třída není povolena. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass`je `null`. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .

`ptr`musí se jednat o definici třídy, která se stala nadřazenou třídou vytvořeného objektu. Vrácený objekt se bude podtřídou aktuálního objektu.

Nový objekt vrácený `ppNewClass` automaticky se stal podtřídou aktuálního objektu. Toto chování nelze přepsat. Neexistuje žádná jiná metoda, pomocí které by bylo možné vytvořit podtřídy (odvozené třídy).

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
