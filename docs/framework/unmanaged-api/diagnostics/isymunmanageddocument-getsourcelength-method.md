---
title: ISymUnmanagedDocument::GetSourceLength – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2717a279abf7fb1b704a769d54654d97949cc0a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939859"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a>ISymUnmanagedDocument::GetSourceLength – metoda
Získá délku v bajtech vloženého zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Ukazatel na proměnnou, která označuje délku v bajtech, vloženého zdroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda uspěje.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
