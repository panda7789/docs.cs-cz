---
title: ISymUnmanagedDocument::GetSourceRange – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 841379702e24428a8092cfd1d2cbd3c5b4e17ba4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615602"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange – metoda
Vrátí zadaný rozsah vloženého zdroje do dané vyrovnávací paměti. Vyrovnávací paměť musí být dostatečně velká pro uložení zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `startLine`  
 pro Počáteční řádek v aktuálním dokumentu.  
  
 `startColumn`  
 pro Počáteční sloupec v aktuálním dokumentu.  
  
 `endLine`  
 pro Poslední řádek v aktuálním dokumentu.  
  
 `endColumn`  
 pro Konečný sloupec v aktuálním dokumentu.  
  
 `cSourceBytes`  
 pro Velikost zdroje (v bajtech).  
  
 `pcSourceBytes`  
 mimo Ukazatel na proměnnou, která přijímá velikost zdroje.  
  
 `source`  
 mimo Velikost a délka zadaného rozsahu zdrojového dokumentu (v bajtech).  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedDocument – rozhraní](isymunmanageddocument-interface.md)
