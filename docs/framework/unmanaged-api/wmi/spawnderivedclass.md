---
title: Funkce SpawnDerivedClass (referenční dokumentace nespravovaného rozhraní API)
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
ms.openlocfilehash: 6f05f349699b28262c1628cadc6e9a0fb0a3459c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783105"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass – funkce
Vytvoří objekt nově odvozené třídy ze zadaného objektu.    
  
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
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Vyhrazená. Tento parametr musí být 0.

`ppNewClass`  
[out] Přijímá ukazatel na nový objekt definice třídy. Pokud dojde k chybě, není objekt vrácen, a `ppNewClass` je bez jakýchkoli úprav vlevo. Jeho hodnota nemůže být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Neplatná operace, jako je například vytvoření třídy z instance, byl požadován. |
| `WBEM_E_INCOMPLETE_CLASS` | Zdrojovou třídu se není úplně definované nebo zaregistrován prostřednictvím služby Windows Management, tak novou odvozenou třídu není povolený. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` je `null`. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) metody.

`ptr` musí být definice třídy, která se stává nadřazené třídu vytvořenému objektu. Vrácený objekt se stane podtřídu aktuálního objektu.

Nový objekt vrácený v `ppNewClass` automaticky stane podtřídu aktuálního objektu. Toto chování nelze přepsat. Neexistuje žádná další metoda, podle kterého je možné vytvořit podtřídy (odvozené třídy).

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
