---
title: ISymUnmanagedWriter::CloseScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a11f689f1fa93e1122ffcc78187c4287db7ea534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope – metoda
Zavře aktuální lexikální obor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `endOffset`  
 [v] Posun od začátku metodu bodu na konci posledního instrukce v oboru lexikální v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Jakmile je uzavřený obor, může být definováno žádné další proměnné v něm.  
  
 [Isymunmanagedwriter::openscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí identifikátor neprůhledného obor, který lze použít s [isymunmanagedwriter::setscoperange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) k definování oboru později je počáteční a koncové posunutí. V takovém případě posunutí předaný `ISymUnmanagedWriter::OpenScope` a `ISymUnmanagedWriter::CloseScope` jsou ignorovány. Identifikátory oboru jsou platné pouze v aktuální metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
