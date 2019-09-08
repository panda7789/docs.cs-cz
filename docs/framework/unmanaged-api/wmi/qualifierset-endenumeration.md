---
title: QualifierSet_EndEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_EndEnumeration ukončí výčet.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5a817174ec4c4e4407c19bb1d6d2d852d86dd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798315"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration – funkce
Ukončí výčet zahájený voláním funkce [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
pro Tento parametr se nepoužívá.

`ptr`   
pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

## <a name="return-value"></a>Návratová hodnota

Následující hodnota vrácená touto funkcí je definována v souboru hlaviček *WbemCli. h* nebo ji můžete definovat jako konstantu v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemQualifierSet:: funkce EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .

Toto volání se doporučuje, ale není povinné. Okamžitě uvolňuje prostředky spojené s výčtem.

## <a name="requirements"></a>Požadavky  

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
**Hlaviček** WMINet_Utils.idl  
  
**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
