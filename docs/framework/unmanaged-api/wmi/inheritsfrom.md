---
title: InheritsFrom funkce (Nespravované rozhraní API Reference)
description: Funkce InheritsFrom určuje, zda je třída nebo instance odvozena z určité nadřazené třídy.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174937"
---
# <a name="inheritsfrom-function"></a>InheritsFrom,
Určuje, zda aktuální třída nebo instance pochází z zadané nadřazené třídy.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszAncestor`  
[v] Název třídy. `wszAncestor`musí ukazovat na `LPCWSTR`platný .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | Aktuální objekt dědí `wszAncestor`z .  |
| `WBEM_S_FALSE` | 1 | Aktuální objekt nedědí `wszAncestor`z . |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` je `null`. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [metody IWbemClassObject::InheritsFrom.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
