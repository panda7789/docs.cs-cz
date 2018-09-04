---
title: Get – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce Get načte hodnotu zadané vlastnosti.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb7475623961fe2ee5fc821c5f237f0a2acfae1a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507659"
---
# <a name="get-function"></a>Get – funkce
Načte hodnotu zadané vlastnosti, pokud existuje.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszName`  
[in] Název vlastnosti.

`lFlags` [in] Vyhrazená. Tento parametr musí být 0.

`pVal` [out] Pokud funkce vrátí úspěšně, obsahuje hodnotu `wszName` vlastnost. `pval` Argument je přiřazena správný typ a hodnota pro kvalifikátor.

`pvtType` [out] Pokud funkce vrátí úspěšně, obsahuje [konstantní typ modelu CIM](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) , který určuje typ vlastnosti. Jeho hodnota může být také `null`. 

`plFlavor` [out] Pokud funkce vrátí úspěšně, obdrží informace o původu vlastnosti. Jeho hodnota může být `null`, nebo jednu z následujících konstant WBEM_FLAVOR_TYPE definované v *WbemCli.h* hlavičkový soubor: 

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Vlastnost je standardní systém vlastnost. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pro třídu: vlastnost je zděděná z nadřazené třídy. </br> Pro instanci: vlastnost, zatímco zděděná z nadřazené třídy nebyl změněn instancí.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pro třídu: vlastnost patří k odvozené třídě. </br> Instance: instance; je změněna vlastnost To znamená, že byla zadána hodnota nebo kvalifikátor byla přidána nebo upravena. |

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaná vlastnost nebyla nalezena. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) metody.

`Get` Funkce může vrátit také vlastnosti systému.

`pVal` Argument je přiřazena správný typ a hodnota pro kvalifikátor a modelu COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) – funkce

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
