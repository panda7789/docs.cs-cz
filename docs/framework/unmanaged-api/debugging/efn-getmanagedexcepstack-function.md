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
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789150"
---
# <a name="_efn_getmanagedexcepstack-function"></a>\_EFN\_GetManagedExcepStack Function
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
 Pokud ve vlákně, který je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** SOS_Stacktrace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](debugging-global-static-functions.md)
