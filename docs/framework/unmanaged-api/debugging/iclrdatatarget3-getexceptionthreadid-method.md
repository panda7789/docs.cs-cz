---
title: ICLRDataTarget3::GetExceptionThreadID – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
ms.openlocfilehash: 961e74551ae7fc170e443c632ca11598f1494a39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785209"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a>ICLRDataTarget3::GetExceptionThreadID – metoda
Voláno pomocí služby Common Language Runtime (CLR) pro získání ID vlákna, které vyvolalo výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 mimo ID vlákna, které vyvolalo výjimku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` při úspěchu nebo selhání `HRESULT` kódu při selhání. Kódy `HRESULT` mohou zahrnovat, ale nejsou omezeny na následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Pro výjimku se nepovedlo najít platné ID vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget3 – rozhraní](iclrdatatarget3-interface.md)
- [GetExceptionContextRecord – metoda](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionRecord – metoda](iclrdatatarget3-getexceptionrecord-method.md)
