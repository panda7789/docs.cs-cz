---
title: ISymUnmanagedWriter::OpenScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ccaaee614b1ec4d03271e70338fff82d629a7c28
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468457"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope – metoda
Otevře se nový lexikální rozsah v aktuální metodě. Obor se stane novou aktuální obor a vloženo do zásobníku oborů. Obory musí tvořit hierarchii. Na stejné úrovni nemohou překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `startOffset`  
 [in] Posun první instrukce v lexikálním rozsahu, v bajtech od začátku metody.  
  
 `pRetVal`  
 [out] Ukazatel `ULONG32` , která přijímá identifikátor rozsahu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 `ISymUnmanagedWriter::OpenScope` Vrátí obor neprůhledný identifikátor, který lze použít s [isymunmanagedwriter::setscoperange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) a určete obor je počáteční a koncové posunutí později. V takovém případě posunutí předán `ISymUnmanagedWriter::OpenScope` a [isymunmanagedwriter::closescope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) jsou ignorovány. Identifikátory oboru jsou platné pouze v aktuální metodě.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
