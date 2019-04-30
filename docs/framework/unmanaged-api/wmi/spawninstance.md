---
title: Funkce SpawnInstance (referenční dokumentace nespravovaného rozhraní API)
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
ms.openlocfilehash: 8056ef18089f56f1f9b6717d505fa3d058957541
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782523"
---
# <a name="spawninstance-function"></a>SpawnInstance – funkce
Vytvoří novou instanci třídy.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Vyhrazená. Tento parametr musí být 0.

`ppNewInstance`  
[out] Přijímá ukazatel na novou instanci třídy. Pokud dojde k chybě, není objekt vrácen, a `ppNewInstance` je bez jakýchkoli úprav vlevo.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` není platnou definicí třídy a nelze vytvořit podřízený nové instance. Je neúplný nebo nebyl zaregistrován pomocí Windows Management voláním [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` je `null`. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) metody.

`ptr` musí být definice třídy získat ze správy Windows. (Všimněte si, že vytváření podřízeného procesu instanci z instance je podporováno, ale vrácená instance je prázdný). Pak použijete této definici třídy k vytvoření nové instance. Volání [PutInstanceWmi](putinstancewmi.md) funkce je nutný, pokud máte v úmyslu instance zápisu ke správě Windows.

Nový objekt vrácený v `ppNewClass` automaticky stane podtřídu aktuálního objektu. Toto chování nelze přepsat. Neexistuje žádná další metoda, podle kterého je možné vytvořit podtřídy (odvozené třídy).

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
