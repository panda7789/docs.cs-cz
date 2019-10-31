---
title: WritePropertyValue – funkce (Reference nespravovaného rozhraní API)
description: Funkce WritePropertyValue zapisuje bajty na vlastnost.
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
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107292"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue – funkce
Zapíše zadaný počet bajtů na vlastnost identifikovanou popisovačem vlastnosti.

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
pro Tento parametr se nepoužívá.

`ptr`  
pro Ukazatel na instanci [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`lHandle`  
pro Celé číslo obsahující popisovač, který identifikuje tuto vlastnost. Popisovač lze načíst voláním funkce [GetPropertyHandle](getpropertyhandle.md) .   

`lNumBytes`  
pro Počet bajtů zapsaných do vlastnosti. Další informace najdete v části [poznámky](#remarks) .

`pHandle`   
mimo Ukazatel na pole bajtů, které obsahuje data.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Došlo k neshodě typů. |
|`WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemclassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .

Pomocí této funkce lze nastavit řetězec a všechna ostatní data, která nejsou`DWORD` nebo nejsou`QWORD`.

Pro neřetězcové hodnoty vlastností musí být `lNumBytes` správná velikost dat zadaného typu vlastnosti. U hodnot řetězcových vlastností musí být `lNumBytes` délka zadaného řetězce v bajtech a samotný řetězec musí mít stejnou délku v bajtech a musí následovat po znaku pro ukončení hodnoty null.

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
