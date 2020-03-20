---
title: NextMethod function (Unmanaged API Reference)
description: Funkce NextMethod načte další metodu ve výčtu.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174924"
---
# <a name="nextmethod-function"></a>NextMethod
Načte další metodu ve výčtu, který začíná [voláníbeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`pName`  
[out] Ukazatel, který `null` odkazuje na před voláním. Když funkce vrátí, adresa nového, `BSTR` který obsahuje název metody.

`ppSignatureIn`  
[out] Ukazatel, který obdrží ukazatel [na IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) který obsahuje `in` parametry pro metodu.

`ppSignatureOut`  
[out] Ukazatel, který obdrží ukazatel [na IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) který obsahuje `out` parametry pro metodu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Nebyla žádná výzva [`BeginEnumeration`](beginenumeration.md) k funkci. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Neexistují žádné další vlastnosti ve výčtu. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)

Volající zahájí pořadí výčtu voláním funkce [BeginMethodEnumeration](beginmethodenumeration.md) a poté zavolá funkci [NextMethod], dokud funkce nevrátí `WBEM_S_NO_MORE_DATA`. Volitelně volající dokončí pořadí voláním [EndMethodEnumeration](endmethodenumeration.md). Volající může ukončit výčet brzy voláním [EndMethodEnumeration](endmethodenumeration.md) kdykoli.

## <a name="example"></a>Příklad

Příklad jazyka C++ naleznete v metodě [IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
