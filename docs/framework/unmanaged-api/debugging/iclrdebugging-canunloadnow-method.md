---
title: ICLRDebugging::CanUnloadNow – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: 16d15101534b88d7da4093dab73b48b5c09a192c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860398"
---
# <a name="iclrdebuggingcanunloadnow-method"></a>ICLRDebugging::CanUnloadNow – metoda
Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a>Parametry  
 `hmodule`  
 pro Základní adresa modulu v cílovém procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Modul, na který je odkazováno, `hmodule` může být uvolněn.|  
|S_FALSE|Modul, na který se odkazuje `hmodule` , se stále používá.|  
|COR_E_NOT_CLR|Uvedený modul není modul CLR.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda kontroluje, zda byly uvolněny všechny `ICorDebug*` instance rozhraní a v současné době není v rámci volání metody [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) žádné vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
