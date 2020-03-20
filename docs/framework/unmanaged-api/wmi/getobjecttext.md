---
title: Funkce GetObjectText (Nespravovaný odkaz na rozhraní API)
description: Funkce GetObjectText vrátí textové vykreslování objektu v syntaxi MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176783"
---
# <a name="getobjecttext-function"></a>Funkce GetObjectText
Vrátí textové vykreslování objektu v syntaxi formátu spravovaného objektu (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[v] Normálně 0. Pokud `WBEM_FLAG_NO_FLAVORS` (nebo 0x1) je zadán, kvalifikátory jsou zahrnuty bez šíření nebo informace o příchuť.

`pstrObjectText`[out] Ukazatel na `null` položku při vstupu. Při návratu nově přidělené, `BSTR` který obsahuje vykreslování syntaxe MOF objektu.  

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecnému selhání. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení operace není k dispozici dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::GetObjectText.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)

Vrácený text MOF neobsahuje všechny informace o objektu, ale pouze dostatek informací pro kompilátor MOF, aby bylo možné znovu vytvořit původní objekt. Například nejsou zahrnuty žádné rozšířené kvalifikátory nebo vlastnosti nadřazené třídy.

Následující algoritmus se používá k rekonstrukci textu parametrů metody:

1. Parametry jsou resequenced v pořadí jejich hodnoty identifikátoru.
1. Parametry, které `[in]` jsou `[out]` určeny jako a jsou kombinovány do jednoho parametru.

`pstrObjectText`musí být ukazatel `null` na při volání funkce; nesmí ukazovat na řetězec, který je platný před voláním metody, protože ukazatel nebude přidělen.

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
