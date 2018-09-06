---
title: Funkce GetPropertyQualifierSet (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetPropertyQualifierSet načte kvalifikátor pro vlastnost nastavit.
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
ms.openlocfilehash: fcddca2e435a3f5bf4b8d083784613254d9801a4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880312"
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
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszMethod`  
[in] Název vlastnosti. `wszProperty` musí odkazovat na platný `LPCWSTR`. 

`ppQualSet`  
[out] Přijímá ukazatel rozhraní, která umožňuje přístup k kvalifikátory vlastnost. `ppQualSet` nemůže být `null`. Pokud dojde k chybě, není vrátí nový objekt a ukazatel je nastaven tak, aby odkazoval na `null`. 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná metoda neexistuje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | Funkce se pokusí získat kvalifikátory vlastnost systému. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) metody. 

Voláním této funkce je podporována pouze v případě, že je aktuální objekt definice třídy CIM. Není k dispozici pro manipulaci s metoda [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters odkazující na instance CIM.

Protože každá metoda může mít svůj vlastní kvalifikátory [IWbemQualifierSet ukazatel](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit kvalifikátory.

Vzhledem k tomu, že vlastnosti systému bez kvalifikátorů, funkce vrátí `WBEM_E_SYSTEM_PROPERTY` při pokusu o získání [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) ukazatel pro vlastnost systému.

## <a name="requirements"></a>Požadavky  
**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
