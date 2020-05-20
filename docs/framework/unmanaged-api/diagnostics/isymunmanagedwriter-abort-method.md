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
ms.openlocfilehash: 09f39d3b6486e2ec3c04c5d1858a85ce56895527
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610155"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort – metoda
Zavře zapisovač symbolů bez potvrzení symbolů do úložiště symbolů. Po tomto volání bude zapisovač symbolů pro další aktualizace neplatný. Chcete-li symboly potvrdit a zavřít zapisovač symbolů, použijte místo toho metodu [ISymUnmanagedWriter:: Close](isymunmanagedwriter-close-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
