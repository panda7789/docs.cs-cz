---
title: ISymUnmanagedDocumentWriter::SetSource – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f25f66d7092c50247e24051280eaa7b714297c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424414"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="9c665-102">ISymUnmanagedDocumentWriter::SetSource – metoda</span><span class="sxs-lookup"><span data-stu-id="9c665-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="9c665-103">Nastaví vložený zdroj pro dokument, který se připravuje.</span><span class="sxs-lookup"><span data-stu-id="9c665-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c665-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c665-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c665-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c665-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="9c665-106">[v] A `ULONG32` obsahující velikost `source` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9c665-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="9c665-107">[v] Vyrovnávací paměť, která ukládá vložený zdroj.</span><span class="sxs-lookup"><span data-stu-id="9c665-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c665-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9c665-108">Return Value</span></span>  
 <span data-ttu-id="9c665-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9c665-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c665-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c665-110">Requirements</span></span>  
 <span data-ttu-id="9c665-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9c665-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c665-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c665-112">See Also</span></span>  
 [<span data-ttu-id="9c665-113">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c665-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
