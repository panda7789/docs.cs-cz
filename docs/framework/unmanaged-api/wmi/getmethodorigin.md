---
title: Funkce GetMethodOrigin (Unmanaged API Reference)
description: Funkce GetMethodOrigin určuje třídu, ve které je deklarována metoda.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176796"
---
# <a name="getmethodorigin-function"></a>Funkce GetMethodOrigin
Určuje třídu, ve které je deklarována metoda.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszMethodName`  
[v] Název metody pro objekt, jehož vlastnící třídy je požadováno.

`pstrClassName`  
[out] Obdrží název třídy, která vlastní metodu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná metoda nebyla nalezena. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů není platný. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::GetMethodOrigin.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)

Vzhledem k tomu, že třída může dědit metody z jedné nebo více základních tříd, vývojáři často chtějí určit třídu, ve které je daná metoda definována.

Parametr `pstrClassName` nesmí ukazovat na `BSTR` platný před voláním funkce, `out` protože se jedná o parametr; tento ukazatel není přidělena po vrátí funkce.

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
