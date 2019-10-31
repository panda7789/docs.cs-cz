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
ms.openlocfilehash: 1d409507de593cf198fe87340eece6820eaefc63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127334"
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
pro Ukazatel na kopii [systémové třídy __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje parametry `in` pro metodu. Tento parametr je ignorován, pokud je nastavena na `null`.  

`pSignatureOut`  
pro  Ukazatel na kopii [systémové třídy __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje parametry `out` pro metodu. Tento parametr je ignorován, pokud je nastavena na `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů je neplatných. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Parametr metody `[in, out]` zadaný v objektech *pInSignature* i *pOutSignature* mají různé kvalifikátory.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | V parametru metody chybí specifikace kvalifikátoru **ID** . |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Série ID, která je přiřazena parametrům metody, není po sobě, nebo nezačíná na 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Návratová hodnota pro metodu má kvalifikátor **ID** . |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Došlo k pokusu o opětovné použití existujícího názvu metody z nadřazené třídy, přičemž signatury se neshodují. |
| `WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

Toto volání metody je podporováno pouze v případě, `ptr` je definice třídy CIM. Manipulace s metodou není k dispozici z ukazatelů [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazujících na instance CIM.

Uživatelé nemůžou vytvářet metody s názvy, které začínají nebo končí podtržítkem. Toto je vyhrazeno pro systémové třídy a vlastnosti.

V případě metody jsou parametry `in` a `out` popsány jako vlastnosti v objektech [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Parametr `[in/out]` lze definovat přidáním stejné vlastnosti do obou objektů, na které odkazují parametry `pInSignature` a `pOutSignature`. V takovém případě vlastnosti sdílejí stejnou hodnotu kvalifikátoru **ID** .

Každá vlastnost v jiném objektu třídy [__Parameters](/windows/desktop/WmiSdk/--parameters) , než `ReturnValue`, musí mít kvalifikátor **ID** , číselnou hodnotu s nulovou hodnotou, která určuje pořadí, ve kterém se budou parametry zobrazovat. Žádné dva parametry nemohou mít stejnou hodnotu **ID** a žádná hodnota **ID** nemůže být vynechána. Pokud dojde k oběma podmínkám, funkce `PutMethod` vrátí `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Příklad

Příklad naleznete v tématu metoda [IWbemclassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
