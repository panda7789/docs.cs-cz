---
title: ISymUnmanagedDocument::HasEmbeddedSource – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d6c79be95ff80c8de9b07cb33be46a5f5db22b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939799"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a>ISymUnmanagedDocument::HasEmbeddedSource – metoda
Vrátí `true` Pokud dokument má zdroj součástí symboly ladění; v opačném případě vrátí `false`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Ukazatel na proměnnou, která určuje, jestli má zdrojový dokument vložit symboly pro ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda uspěje.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
