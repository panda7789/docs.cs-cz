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
ms.openlocfilehash: 7cdf34ff6ae506ba209300685da3752820b250a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516747"
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
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszName`  
[in] Název metody k vytvoření. 

`lFlags`  
[in] Vyhrazená. Tento parametr musí být 0.

`pSignatureIn`  
[in] Ukazatel na kopii [třída systému __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje `in` parametrů metody. Tento parametr se ignoruje, pokud nastavit `null`.  

`pSignatureOut`  
[in]  Ukazatel na kopii [třída systému __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje `out` parametrů metody. Tento parametr se ignoruje, pokud nastavit `null`.
 

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů nejsou platné. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]` Parametr metody určené v i *pInSignature* a *pOutSignature* objekty mají různé kvalifikátory.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Parametr metody chybí specifikace **ID** kvalifikátoru. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | ID série, která je přiřazena k parametrům metody není po sobě jdoucích nebo není začínají hodnotou 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Návratová hodnota metody má **ID** kvalifikátoru. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Byl proveden pokus o opakované použití existující název metody od nadřazené třídy a podpisy se neshodují. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.

Volání této metody je podporována pouze v případě `ptr` je definice třídy CIM. Zpracování metody není k dispozici [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) ukazatele, které odkazují na instance CIM.

Uživatelé nemůžou vytvářet metody s názvy, které začínat ani končit podtržítkem. To je vyhrazen pro systémové třídy a vlastnosti.

Pro metodu `in` a `out` jsou popsány parametry jako vlastnosti v [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objekty.

`[in/out]` Parametr může být definován tak, že přidáte na oba objekty, na které odkazují stejnou vlastnost `pInSignature` a `pOutSignature` parametry. V takovém případě vlastnosti sdílet stejný **ID** hodnotu kvalifikátoru.

Každou vlastnost v [__Parameters](/windows/desktop/WmiSdk/--parameters) třídy objektů jiných než `ReturnValue` musí mít **ID** kvalifikátor, založený na nule, který identifikuje pořadí parametrů číselnou hodnotu. Žádné dva parametry můžou mít stejný **ID** hodnotu a ne **ID** hodnoty mohou být přeskočeny. Pokud dojde k některou z podmínek, `PutMethod` vrací funkce `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Příklad

Příklad najdete v tématu [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.

## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
