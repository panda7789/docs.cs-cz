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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179115"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request – metoda
Volat služby přístupu k datům cltime společného jazyka (CLR) požádat o operaci, jak je definováno implementací.  
  
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
 [v] Definováno uživatelem.  
  
 `inBufferSize`  
 [v] Velikost vstupní vyrovnávací paměti, která se používá pro příchozí požadavek.  
  
 `inBuffer`  
 [v] Vyrovnávací paměť obsahující požadavek.  
  
 `outBufferSize`  
 [v] Velikost výstupní vyrovnávací paměti, která se používá pro odpověď.  
  
 `outBuffer`  
 [out] A Buffer obsahující odpověď.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `Request` usnadňuje přidání nespecifikovaných vlastních operací. To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti revize definice rozhraní.  
  
 Tato metoda je implementována zapisovače ladicí aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRDataTarget – rozhraní](iclrdatatarget-interface.md)
