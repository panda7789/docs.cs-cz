---
title: GetErrorInfo – funkce (odkaz na nespravované rozhraní API)
description: Funkce GetErrorInfo načte informace o chybě z předchozího volání funkce.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 062dc62dfe53af3bf5158cb1add0897eccc1df60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102617"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo – funkce
Načte informace o chybě z předchozího volání funkce.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) , pokud je volání funkce úspěšné, nebo `null`, pokud selže.
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IComThreadingInfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. def  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
