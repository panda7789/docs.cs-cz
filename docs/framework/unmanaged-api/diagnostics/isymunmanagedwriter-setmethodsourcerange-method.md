---
title: ISymUnmanagedWriter::SetMethodSourceRange – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d057201c7d7bec3070027bb1d9de62735d583cf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>ISymUnmanagedWriter::SetMethodSourceRange – metoda
Určuje hodnotu true počáteční a koncová metody v rámci zdrojového souboru. Tuto metodu použijte k určení rozsahu metoda nezávisle na pořadí body, které existují v rámci metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a>Parametry  
 `startDoc`  
 [v] Ukazatel na dokument obsahující počáteční pozici.  
  
 `startLine`  
 [v] Počáteční řádek číslo.  
  
 `startColumn`  
 [v] Počáteční sloupec.  
  
 `endDoc`  
 [v] Ukazatel na dokument obsahující koncovou pozici.  
  
 `endLine`  
 [v] Koncová číslo řádku.  
  
 `endColumn`  
 [v] Koncová číslo sloupce.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
