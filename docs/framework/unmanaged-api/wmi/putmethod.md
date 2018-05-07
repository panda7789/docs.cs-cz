---
title: Funkce PutMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce PutMethod vytvoří metodu.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f74b0d30a1a8899d3c8d0a2bf0f108ea11165cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="putmethod-function"></a>PutMethod – funkce
Vytvoří metodu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr se nepoužívá.

`ptr`  
[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszName`  
[v] Název metody pro vytvoření. 

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`pSignatureIn`  
[v] Ukazatel na kopii [__Parameters systémové třídy](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) obsahující `in` parametry pro metodu. Tento parametr je ignorována, pokud nastavena na `null`.  

`pSignatureOut`  
[v]  Ukazatel na kopii [__Parameters systémové třídy](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) obsahující `out` parametry pro metodu. Tento parametr je ignorována, pokud nastavena na `null`.
 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]` Parametru metody, které jsou zadané v obou *pInSignature* a *pOutSignature* objekty mají různé kvalifikátory.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Chybí parametr metody specifikaci **ID** kvalifikátor. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | ID řady, která je přiřazena k parametrům metody není po sobě jdoucích nebo se nespustí na 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Návratovou hodnotu pro metodu má **ID** kvalifikátor. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Došlo k pokusu o opakované použití existujícího názvu metody od nadřazené třídy a podpisů se neshoduje. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metoda.

Toto volání metody je podporována pouze v případě `ptr` je definice třídy CIM. Manipulace s metoda není k dispozici z [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) ukazatele, které odkazují na modelu CIM instancí.

Uživatele nelze vytvořit metody s názvy, které začínat ani končit znakem podtržítka. Toto je vyhrazená pro systém třídy a vlastnosti.

Pro metodu `in` a `out` parametry jsou popsané v jako vlastnosti [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objekty.

`[in/out]` Parametr lze definovat přidáním stejnou vlastnost na oba objekty, na kterou odkazuje `pInSignature` a `pOutSignature` parametry. V takovém případě vlastnosti sdílet stejný **ID** kvalifikátor hodnotu.

Každou vlastnost v [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) třídy objektu jiné než `ReturnValue` musí mít **ID** kvalifikátor, počítáno od nuly číselnou hodnotu, která identifikuje pořadí, ve kterém se zobrazí parametry. Žádné dva parametry může mít stejný **ID** hodnota a ne **ID** hodnoty mohou být přeskočeny. Pokud dojde k buď podmínky, `PutMethod` funkce vrátí `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Příklad

Příklad, naleznete v části [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metoda.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
