---
title: _EFN_GetManagedObjectFieldInfo – funkce
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 182424632e4f81dfdf86e87dc6bb2c75c2780fce
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793760"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a>\_EFN\_GetManagedObjectFieldInfo Function
Získá posun od začátku objektu k poli a hodnotu pole pomocí zadaného ukazatele objektu a názvu pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Client`  
 pro Ukazatel na ladicího klienta.  
  
 `objAddr`  
 pro Ukazatel spravovaného objektu.  
  
 szFieldName  
 pro Ukazatel spravovaného objektu na název pole.  
  
 `pValue`  
 mimo Hodnota pole Tento parametr může mít hodnotu null.  
  
 `pOffset`  
 mimo Posun od `objAddr` k poli. Tento parametr může mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je posun 0, není zapsán žádný posun.  
  
 Pokud ve vlákně, který je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** SOS_Stacktrace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](debugging-global-static-functions.md)
