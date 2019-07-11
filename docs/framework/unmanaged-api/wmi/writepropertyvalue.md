---
title: Funkce WritePropertyValue (referenční dokumentace nespravovaného rozhraní API)
description: Funkce WritePropertyValue zapíše bajty do vlastnosti.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47120ff9de9e6e4802c5aea990841b235cd6c74c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783057"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue – funkce
Zapíše zadaný počet bajtů na vlastnost identifikovaný popisovač vlastnosti.

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
[in] Tento parametr se nepoužívá.

`ptr`  
[in] Ukazatel [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.

`lHandle`  
[in] Celé číslo, které obsahuje popisovač identifikující tuto vlastnost. Popisovač může být načten voláním [GetPropertyHandle](getpropertyhandle.md) funkce.   

`lNumBytes`  
[in] Počet bajtů, které probíhá zápis do vlastnosti. Zobrazit [poznámky](#remarks) části Další informace.

`pHandle`   
[out] Ukazatel na pole bajtů obsahující data.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Došlo k neshodě typů. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) metody.

Pomocí této funkce můžete nastavit řetězec a všechny ostatní jinou hodnotu než`DWORD` nebo jiných-`QWORD` data.

Neřetězcový hodnoty vlastností `lNumBytes` musí mít velikost správného datového typu vlastnosti zadané. Pro řetězce hodnoty vlastnosti `lNumBytes` musí mít délku zadaného řetězce v bajtech a řetězce samostatně musí být i délka v bajtech a být následován znakem ukončení hodnotou null.

## <a name="requirements"></a>Požadavky  
**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
