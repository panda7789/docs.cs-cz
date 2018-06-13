---
title: ISymUnmanagedWriter::Abort – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb6a3e65b1f1d59cde3bff99e491bcf09816c8ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428055"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort – metoda
Zavře zapisovače symbol bez potvrzení symboly pro úložiště symbolů. Po toto volání zapisovače symbol stává neplatným pro další aktualizace. Potvrdit symboly a zavřete zapisovače symbol, použijte [isymunmanagedwriter::Close –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
