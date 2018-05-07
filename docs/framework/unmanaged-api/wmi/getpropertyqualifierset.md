---
title: Funkce GetPropertyQualifierSet (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetPropertyQualifierSet načte kvalifikátor nastavená pro vlastnost.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2951733211737f06cd737b20bd1537277be1be1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet – funkce
Načte kvalifikátor nastavit určité vlastnosti.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszMethod`  
[v] Název vlastnosti. `wszProperty` musí odkazovat na platný `LPCWSTR`. 

`ppQualSet`  
[out] Ukazatel rozhraní, které umožňuje přístup k kvalifikátory vlastnosti obdrží. `ppQualSet` nemůže být `null`. Pokud dojde k chybě, nevrátí nový objekt a ukazatel je nastaven tak, aby odkazoval na `null`. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná metoda neexistuje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | Funkce, pokusí se získat kvalifikátory vlastnosti systému. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) metoda. 

Volání této funkce je podporována pouze v případě, že je aktuální objekt definice třídy CIM. Není k dispozici pro manipulaci s metoda [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters, které odkazují na modelu CIM instancí.

Protože každá metoda může mít svůj vlastní kvalifikátory [IWbemQualifierSet ukazatel](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umožňuje přidat, upravit nebo odstranit tyto kvalifikátory volající.

Vzhledem k tomu, že vlastnosti systému žádné kvalifikátory, funkce vrátí hodnotu `WBEM_E_SYSTEM_PROPERTY` když se pokusí získat [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) ukazatele pro vlastnost systému.

## <a name="requirements"></a>Požadavky  
**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
