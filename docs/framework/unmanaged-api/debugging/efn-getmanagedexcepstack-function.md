---
title: _EFN_GetManagedExcepStack – funkce
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: 9bcc03cc97a62b4c1cadacd7c0b2bc46b9fec470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134132"
---
# <a name="_efn_getmanagedexcepstack-function"></a>\_EFN\_funkce GetManagedExcepStack
Pokud je zadána adresa spravovaného objektu výjimky, vrátí verzi řetězce trasování zásobníku obsaženého v rámci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Client`  
 pro Probíhá ladění klienta.  
  
 `StackObjAddr`  
 pro Ukazatel spravovaného objektu odvozený z <xref:System.Exception>.  
  
 szStackString  
 mimo Vrácený řetězec.  
  
 `cbString`  
 mimo Počet znaků, které jsou k dispozici v bufferu řetězce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud ve vlákně, které je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** SOS_Stacktrace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
