---
title: ICLRDataTarget::Request – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: e5d7a6b9826a734363d6beeb2e3fab8422964558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113355"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request – metoda
Volá se službami CLR (Common Language Runtime) k vyžádání operace, jak jsou definované implementací.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `reqCode`  
 pro Definováno uživatelem.  
  
 `inBufferSize`  
 pro Velikost vstupní vyrovnávací paměti, která se používá pro příchozí požadavek.  
  
 `inBuffer`  
 pro Vyrovnávací paměť obsahující požadavek.  
  
 `outBufferSize`  
 pro Velikost výstupní vyrovnávací paměti, která se používá pro odpověď.  
  
 `outBuffer`  
 mimo Vyrovnávací paměť obsahující odpověď.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `Request` usnadňuje přidání nespecifikovaných vlastních operací. To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti Revize definice rozhraní.  
  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
