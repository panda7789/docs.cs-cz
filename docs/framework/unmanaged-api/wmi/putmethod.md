---
title: Funkce PutMethod (Unmanaged API Reference)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174911"
---
# <a name="putmethod-function"></a>PutMethod
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
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`  
[v] Název metody, která má být vytvořit.

`lFlags`  
[v] Vyhrazena. Tento parametr musí být 0.

`pSignatureIn`  
[v] Ukazatel na kopii [__Parameters systémové třídy,](/windows/desktop/WmiSdk/--parameters) která obsahuje `in` parametry pro metodu. Tento parametr je ignorován, `null`pokud je nastavenna .  

`pSignatureOut`  
[v]  Ukazatel na kopii [__Parameters systémové třídy,](/windows/desktop/WmiSdk/--parameters) která obsahuje `out` parametry pro metodu. Tento parametr je ignorován, `null`pokud je nastavenna .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden nebo více parametrů není platný. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Parametr `[in, out]` metody zadaný v *objektech pInSignature* i *pOutSignature* má různé kvalifikátory.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Parametr metody chybí specifikace kvalifikátoru **ID.** |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Řada ID, která je přiřazena parametrům metody, není po sobě jdoucí nebo nezačíná na hodnotě 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Vrácená hodnota metody má kvalifikátor **ID.** |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Došlo k pokusu o opětovné použití existujícího názvu metody z nadřazené třídy a podpisy se neshodují. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné. |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)

Toto volání metody `ptr` je podporováno pouze v případě, že je definice třídy CIM. Manipulace s metodami není k dispozici z ukazatelů [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) které odkazují na instance CIM.

Uživatelé nemohou vytvářet metody s názvy, které začínají nebo končí podtržítkem. To to je vyhrazeno pro systémové třídy a vlastnosti.

Pro metodu `in` a `out` parametry jsou popsány jako vlastnosti v [objektech IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

Parametr `[in/out]` lze definovat přidáním stejné vlastnosti do obou `pInSignature` `pOutSignature` objektů, na které se vztahuje parametry a. V tomto případě vlastnosti sdílejí stejnou hodnotu kvalifikátoru **ID.**

Každá vlastnost v [__Parameters](/windows/desktop/WmiSdk/--parameters) objektu třídy jiné než `ReturnValue` musí mít **id** kvalifikátor, nula číselná hodnota, která identifikuje pořadí, ve kterém se zobrazí parametry. Žádné dva parametry mohou mít stejnou hodnotu **ID** a nelze přeskočit žádnou hodnotu **ID.** Pokud dojde k některé `PutMethod` z `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`těchto podmínek, funkce vrátí .

## <a name="example"></a>Příklad

Příklad naleznete v metodě [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
