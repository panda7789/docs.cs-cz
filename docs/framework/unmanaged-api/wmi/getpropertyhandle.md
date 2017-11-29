---
title: "Funkce GetPropertyHandle (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetPropertyHandle vrací jedinečný popisovač identit, že bude vlastnost."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyHandle
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyHandle
helpviewer_keywords: GetPropertyHandle function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ab3df6d2233059de76036da7ff27f5cc1808aaf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle – funkce
Vrací jedinečný popisovač, který identifikuje vlastnost.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.

`wszPropertyName`  
[v] Řetězec kódovaný jazykem UTF16 characaters, který obsahuje název vlastnosti ukončené hodnotou null.   

`pType`  
[out] Ukazatel [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) člen výčtu, který představuje typ modelu CIM vlastnosti.

`pHandle`   
[out] Ukazatel na celé číslo, které obsahuje popisovače vlastnosti.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný název vlastnosti nebyl nalezen. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | Požadovaná vlastnost je typu jsou `CIM_OBJECT` nebo `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) metoda.

Tento popisovač můžete použít k identifikaci vlastnosti při použití [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) metody pro čtení nebo zápis hodnot vlastností.

Zpracovává se nedají načíst pro vlastnosti všech typů dat než `CIM_OBJECT` a `CIM_ARRAY`. Vrátí popisovače pracovní napříč všemi instancemi třídy.

## <a name="requirements"></a>Požadavky  
**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
