---
title: ISymUnmanagedMethod::GetSourceStartEnd – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 01ab69b73a7bc4929e2ebd49b3847f8d7c4646a2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448860"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a>ISymUnmanagedMethod::GetSourceStartEnd – metoda
Získá pozice počátečního a koncového dokumentu pro zdroj této metody. První pozice pole je začátek a druhá pozice pole je konec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `docs`  
 pro Počáteční a koncové zdrojové dokumenty.  
  
 `lines`  
 pro Počáteční a koncové řádky v odpovídajících zdrojových dokumentech.  
  
 `columns`  
 pro Počáteční a koncové sloupce v odpovídajících zdrojových dokumentech.  
  
 `pRetVal`  
 [out] `true`, pokud byly definovány pozice; v opačném případě `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
