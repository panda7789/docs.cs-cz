---
title: Funkce GetObjectText (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetObjectText vrací textové vykreslování objektu v syntaxi MOF.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d34cb399ac0e8780c442eeb2e95cebfd0a22ca02
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208316"
---
# <a name="getobjecttext-function"></a>Funkce GetObjectText
Vrátí textovou vykreslování objektu v syntaxi formátu MOF (Managed Object).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Obvykle 0. Pokud `WBEM_FLAG_NO_FLAVORS` (nebo 0x1) je zadán kvalifikátory jsou zahrnuty bez informací o šíření nebo flavor.

`pstrObjectText`   
[out] Ukazatel `null` při vstupu. Na vrátit, nově přidělenou `BSTR` , který obsahuje syntaxi MOF vykreslení objektu.  

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) metody.

MOF text vracený při neobsahuje všechny informace o objektu, ale pouze dostatek informací pro kompilátoru MOF být schopni obnovit na původní objekt. Žádné rozšíří kvalifikátory nebo vlastnosti nadřazené třídu pro instanci, jsou zahrnuté.

Následující požadovaný algoritmus se používá k rekonstrukci text parametry metody:

1. Parametry jsou resequenced v pořadí hodnot jejich identifikátoru.
1. Parametry, které jsou určeny jako `[in]` a `[out]` jsou sloučeny do jediného parametru.
 
`pstrObjectText` musí být ukazatel `null` při volání funkce; nesmí odkazovat na řetězec, který je platný před voláním metody, protože ukazatel nebudou uvolněný.

## <a name="requirements"></a>Požadavky  
**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
