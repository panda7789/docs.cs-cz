---
title: ISymUnmanagedDocument::FindClosestLine – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f31dad53f42fdd8f7ac3a0cb995b507ecc3590d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentfindclosestline-method"></a>ISymUnmanagedDocument::FindClosestLine – metoda
Vrátí nejbližší řádek, který je bod pořadí na základě řádku v tomto dokumentu, který může nebo nemusí být bodu sekvence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `line`  
 [v] Řádek v tomto dokumentu.  
  
 `pRetVal`  
 [out] Ukazatel na proměnnou, která přijímá řádku.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. jinak kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
