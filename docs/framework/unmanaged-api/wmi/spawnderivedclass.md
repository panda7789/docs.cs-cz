---
title: Funkce SpawnDerivedClass (Nespravovaný odkaz na rozhraní API)
description: Funkce SpawnDerivedClass vytvoří nový objekt, který je odvozen od objektu.
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
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174846"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass
Vytvoří nově odvozený objekt třídy z určeného objektu.
  
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
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`ppNewClass`  
[out] Obdrží ukazatel na nový objekt definice třídy. Pokud dojde k chybě, nový objekt není `ppNewClass` vrácena a je ponechána beze změny. Jeho hodnota `null`nemůže být .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecnému selhání. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Byla požadována neplatná operace, například vytvoření třídy z instance. |
| `WBEM_E_INCOMPLETE_CLASS` | Source třída nebyla zcela definována nebo registrována pomocí správy systému Windows, takže nová odvozená třída není povolena. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení operace není k dispozici dostatek paměti. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` je `null`. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [metody IWbemClassObject::SpawnDerivedClass.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)

`ptr`musí být definice třídy, která se stane nadřazenou třídou objektu spawned. Vrácený objekt se stane podtřídou aktuálního objektu.

Nový objekt vrácený automaticky `ppNewClass` se stane podtřídou aktuálního objektu. Toto chování nelze přepsat. Neexistuje žádná jiná metoda, kterou lze vytvořit podtřídy (odvozené třídy).

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
