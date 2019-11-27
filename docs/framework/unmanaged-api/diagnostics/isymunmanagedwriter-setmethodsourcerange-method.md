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
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427875"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>ISymUnmanagedWriter::SetMethodSourceRange – metoda
Určuje skutečný začátek a konec metody ve zdrojovém souboru. Tuto metodu použijte, chcete-li určit rozsah metody nezávisle na sekvenčních bodech, které existují v rámci metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a>Parametry  
 `startDoc`  
 pro Ukazatel na dokument obsahující počáteční pozici.  
  
 `startLine`  
 pro Číslo počátečního řádku  
  
 `startColumn`  
 pro Počáteční sloupec  
  
 `endDoc`  
 pro Ukazatel na dokument, který obsahuje koncovou pozici.  
  
 `endLine`  
 pro Koncové číslo řádku  
  
 `endColumn`  
 pro Číslo koncového sloupce  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
