---
title: SpawnInstance – funkce (Reference nespravovaného rozhraní API)
description: Funkce SpawnInstance vytvoří novou instanci třídy.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529905bd9286520a8e09479bfc95ef0b614f53e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798216"
---
# <a name="spawninstance-function"></a>SpawnInstance – funkce
Vytvoří novou instanci třídy.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`ppNewInstance`  
mimo Přijme ukazatel na novou instanci třídy. Pokud dojde k chybě, nový objekt se nevrátí a `ppNewInstance` zůstane beze změny.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`není platnou definicí třídy a nemůže vytvořit nové instance. Buď je neúplný, nebo nebyl zaregistrován u správy systému Windows voláním [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass`je `null`. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) .

`ptr`musí se jednat o definici třídy získanou ze správy systému Windows. (Všimněte si, že vytvoření instance z instance je podporováno, ale vrácená instance je prázdná.) Tuto definici třídy pak můžete použít k vytvoření nových instancí. Pokud máte v úmyslu zapsat instanci do správy systému Windows, je třeba zadat volání funkce [PutInstanceWmi](putinstancewmi.md) .

Nový objekt vrácený `ppNewClass` automaticky se stal podtřídou aktuálního objektu. Toto chování nelze přepsat. Neexistuje žádná jiná metoda, pomocí které by bylo možné vytvořit podtřídy (odvozené třídy).

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
