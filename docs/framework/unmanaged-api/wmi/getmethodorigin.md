---
title: Funkce GetMethodOrigin (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetMethodOrigin určuje třídy, ve kterém je deklarována metodu.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1cc754fcf7d1defa815bb0a74b7c2b4a6909478
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085751"
---
# <a name="getmethodorigin-function"></a>Funkce GetMethodOrigin
Určuje třídy, ve kterém je deklarována metodu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszMethodName`  
[in] Název metody pro objekt, jehož vlastnící třídy jsou požadovány. 

`pstrClassName`  
[out] Získá název třídy, která vlastní metodu.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná metoda nebyla nalezena. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.

Protože třída může dědit z jednoho nebo více základních tříd metody, vývojáři často chtějí určit třídu, ve kterém je definována dané metody.

`pstrClassName` Parametr nesmí odkazovat na platnou `BSTR` před voláním funkce, protože se jedná `out` parametr; tato ukazatel není uvolněný po vrácení funkce.

## <a name="requirements"></a>Požadavky  
**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
