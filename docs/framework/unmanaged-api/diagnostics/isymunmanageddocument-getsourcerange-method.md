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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a89c706ece0949ffa3c182d53b57221acf81b18d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515064"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange – metoda
Vrátí zadaný rozsah vloženého zdroje do daného vyrovnávací paměti. Vyrovnávací paměť musí být dostatečně velký pro umístění zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `startLine`  
 [in] Počáteční řádek v aktuálním dokumentu.  
  
 `startColumn`  
 [in] Počáteční sloupec v aktuálním dokumentu.  
  
 `endLine`  
 [in] Poslední řádek v aktuálním dokumentu.  
  
 `endColumn`  
 [in] Poslední sloupec v aktuálním dokumentu.  
  
 `cSourceBytes`  
 [in] Velikost zdroje, v bajtech.  
  
 `pcSourceBytes`  
 [out] Ukazovat na proměnnou, která bude přijímat velikost zdroje.  
  
 `source`  
 [out] Velikost a délku zadaného rozsahu ve zdrojovém dokumentu, v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda uspěje.  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
