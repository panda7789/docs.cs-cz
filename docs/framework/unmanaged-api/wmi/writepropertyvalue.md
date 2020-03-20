---
title: WritePropertyValue function (Unmanaged API Reference)
description: Funkce WritePropertyValue zapisuje bajty do vlastnosti.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174833"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue
Zapíše zadaný počet bajtů do vlastnosti identifikované popisovačem vlastnosti.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr není použit.

`ptr`  
[v] Ukazatel na instanci [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)

`lHandle`  
[v] Celé číslo, které obsahuje popisovač, který identifikuje tuto vlastnost. Popisovač lze načíst voláním funkce [GetPropertyHandle.](getpropertyhandle.md)

`lNumBytes`  
[v] Počet bajtů zapisováno do vlastnosti. Další informace naleznete v části [Poznámky.](#remarks)

`pHandle`[out] Ukazatel na bajtové pole, které obsahuje data.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Došlo k neshodě typů. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání metody [IWbemClassObject::WritePropertyValue.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)

Tato funkce slouží k nastavení řetězce`DWORD` a`QWORD` všech ostatních nedat.

Pro hodnoty vlastností `lNumBytes` nonstring musí být správná velikost dat zadaného typu vlastnosti. Pro hodnoty vlastností řetězce `lNumBytes` musí být délka zadaného řetězce v bajtů a samotný řetězec musí mít rovnou délku v bajtů a musí být následován znakem null-termination.

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
