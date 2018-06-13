---
title: Funkce QualifierSet_GetNames (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_GetNames načte názvy kvalifikátory z na objekt nebo vlastnost.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7c96439cf50c18e336baa70cf463b9463203290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461175"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames – funkce
Načte názvy všech kvalifikátory nebo určitých kvalifikátory, které jsou k dispozici na aktuální objekt nebo vlastnost. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[v] Tento parametr se nepoužívá.

`ptr`   
[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`lFlags`   
[v] Jeden z následujících příznaků nebo hodnoty, které určuje jména, které chcete zahrnout do výčtu.

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|  | 0 | Vrátí názvy všech kvalifikátory. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Vraťte pouze názvy kvalifikátory specifické pro aktuální vlastnost nebo objekt. <br/> Pro vlastnost: vracet jenom kvalifikátory specifické pro vlastnost (včetně potlačení), a ne těchto kvalifikátory rozšíří z definice třídy. <br/> Pro instanci: vrátit pouze názvy kvalifikátor specifické pro instanci. <br/> Pro třídu: vracet jenom kvalifikátory specifické pro beiong třídy odvozené.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Vraťte se rozšíří pouze názvy kvalifikátory z jiného objektu. <br/> Pro vlastnost: vrátit se rozšíří pouze kvalifikátory k této vlastnosti z definice třídy a ne z samotné vlastnosti. <br/> Pro instanci: vrátí jenom ty kvalifikátory rozšíří z definice třídy. <br/> Pro třídu: vrátit pouze názvy kvalifikátor zděděn od nadřazené třídy. |

`pstrNames` [out] Nový `SAFEARRAY` obsahující požadované názvy. Pole může obsahovat 0 elementy. Pokud dojde k chybě, nový `SAFEARRAY` nevrátí.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici zahájíte nové – výčet není dostatek paměti. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) metoda.

Jakmile jste načíst názvy kvalifikátor, můžete přístup každý kvalifikátor podle názvu voláním [QualifierSet_Get](qualifierset-get.md) funkce. 

Není pro daný objekt má nulové kvalifikátory, takže chybu počet řetězců v `pstrNames` návratu z může být 0, i když funkce vrátí hodnotu `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
