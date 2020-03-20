---
title: Funkce BeginMethodEnumeration (Unmanaged API Reference)
description: Funkce BeginMethodEnumeration spustí výčet metod objektu.
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
ms.openlocfilehash: 876f5810fffab7fa98cd4d46715e13569ab95f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175041"
---
# <a name="beginmethodenumeration-function"></a>Funkce BeginMethodEnumeration
Začíná výčet metod, které jsou k dispozici pro objekt.  

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
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lEnumFlags`  
[v] Zero (0) pro všechny metody nebo příznak, který určuje rozsah výčtu. Následující příznaky jsou definovány v souboru hlavičky *WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Omezte výčet na metody, které jsou definovány v samotné třídě. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Omezte výčet na vlastnosti, které jsou zděděny ze základních tříd. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags`je nenulová a není jedním ze zadaných příznaků. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::BeginMethodEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration)

Toto volání metody je podporováno pouze v případě, že aktuální objekt je definice třídy. Manipulace s metodami není k dispozici z ukazatelů [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) které odkazují na instance. Pořadí, ve kterém jsou metody výčtu je zaručeno, že je invariantpro danou instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
