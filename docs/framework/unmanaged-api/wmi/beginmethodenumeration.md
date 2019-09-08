---
title: BeginMethodEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce BeginMethodEnumeration zahájí výčet metod objektu.
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a7b93bacabdfdd0551418644a7d9a4b1643c3d9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798760"
---
# <a name="beginenumeration-function"></a>Funkce BeginEnumeration
Spustí výčet metod, které jsou k dispozici pro objekt.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lEnumFlags`  
pro Nula (0) pro všechny metody nebo příznak, který určuje rozsah výčtu. Následující příznaky jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na metody, které jsou definovány ve třídě samotné. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags`je nenulová a není jedním z určených příznaků. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .

Toto volání metody je podporováno pouze v případě, že aktuální objekt je definice třídy. Manipulace s metodou není k dispozici z ukazatelů [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , které odkazují na instance. Pořadí, ve kterém jsou metody výčty, je zaručené pro danou instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)jako invariantní.

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
