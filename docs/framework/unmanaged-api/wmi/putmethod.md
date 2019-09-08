---
title: PutMethod – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: a2b41cbbade9da5c2095309b9039b8ce2758f6f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798360"
---
# <a name="putmethod-function"></a>PutMethod – funkce
Vytvoří metodu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`  
pro Název metody, která se má vytvořit. 

`lFlags`  
pro Rezervovaný. Tento parametr musí mít hodnotu 0.

`pSignatureIn`  
pro Ukazatel na kopii [systémové třídy __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje `in` parametry pro metodu. Tento parametr je ignorován, pokud je `null`nastavena na.  

`pSignatureOut`  
pro  Ukazatel na kopii [systémové třídy __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje `out` parametry pro metodu. Tento parametr je ignorován, pokud je `null`nastavena na.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů je neplatných. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Parametr metody zadaný v objektech pInSignature i *pOutSignature* mají různé kvalifikátory. `[in, out]`
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | V parametru metody chybí specifikace kvalifikátoru **ID** . |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Série ID, která je přiřazena parametrům metody, není po sobě, nebo nezačíná na 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Návratová hodnota pro metodu má kvalifikátor **ID** . |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Došlo k pokusu o opětovné použití existujícího názvu metody z nadřazené třídy, přičemž signatury se neshodují. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

Toto volání metody je podporováno pouze v `ptr` případě, že je definice třídy CIM. Manipulace s metodou není k dispozici z ukazatelů [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazujících na instance CIM.

Uživatelé nemůžou vytvářet metody s názvy, které začínají nebo končí podtržítkem. Toto je vyhrazeno pro systémové třídy a vlastnosti.

V `in` případě metody jsou parametry a `out` popsány jako vlastnosti v objektech [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Parametr lze definovat přidáním stejné vlastnosti do obou objektů, na které `pInSignature` ukazuje parametry a `pOutSignature`. `[in/out]` V takovém případě vlastnosti sdílejí stejnou hodnotu kvalifikátoru **ID** .

Každá vlastnost v objektu třídy [__Parameters](/windows/desktop/WmiSdk/--parameters) , která je `ReturnValue` jiná než, musí mít kvalifikátor **ID** , číselnou hodnotu s nulovou hodnotou, která určuje pořadí, ve kterém jsou parametry zobrazeny. Žádné dva parametry nemohou mít stejnou hodnotu **ID** a žádná hodnota **ID** nemůže být vynechána. Pokud dojde k oběma podmínkám, `PutMethod` funkce vrátí `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Příklad

Příklad naleznete v tématu metoda [IWbemclassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
