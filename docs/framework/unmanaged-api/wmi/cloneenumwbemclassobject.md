---
title: Funkce CloneEnumWbemClassObject (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CloneEnumWbemClassObject vytvoří kopii logické enumerátor.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e881eca541d6a987fa7d27e1d73903f843e26a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject – funkce
Vytvoří kopii logické enumerátor zachovat své aktuální pozici ve výčtu.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```  

## <a name="parameters"></a>Parametry

`ppEnum`  
[out] Obdrží ukazatel na novou [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx).

`authLevel`  
[v] Úroveň ověřování.

`impLevel` [v] Úroveň zosobnění.

`pCurrentEnumWbemClassObject`  
[out] Ukazatel [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) instance ke klonování.

`strUser`   
[v] Uživatelské jméno. Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`strPassword`   
[v] Heslo. Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`strAuthority`   
[v] Název domény uživatele. Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr je neplatný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici není dostatek paměti dokončit operaci. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) metoda.

Tato metoda umožňuje pouze kopie "co možná nejlepší". Z důvodu dynamické povaha mnoho objektů CIM je možné, že nový enumerátor neprovede výčet stejnou sadu objektů jako enumerátoru zdroje.  

Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="example"></a>Příklad

Příklad, naleznete v části [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) metoda.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
