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
ms.openlocfilehash: bcdda6f8cdd0fc0b333b81d58a8bff7c21aa1fef
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486404"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="9065d-102">ISymUnmanagedDocumentWriter::SetSource – metoda</span><span class="sxs-lookup"><span data-stu-id="9065d-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="9065d-103">Nastaví vložený zdroj pro dokument, u kterého probíhá zápis.</span><span class="sxs-lookup"><span data-stu-id="9065d-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9065d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9065d-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9065d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9065d-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="9065d-106">[in] A `ULONG32` , který obsahuje velikost `source` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9065d-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="9065d-107">[in] Vyrovnávací paměť, která ukládá vloženého zdroje.</span><span class="sxs-lookup"><span data-stu-id="9065d-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9065d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9065d-108">Return Value</span></span>  
 <span data-ttu-id="9065d-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9065d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9065d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9065d-110">Requirements</span></span>  
 <span data-ttu-id="9065d-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9065d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9065d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9065d-112">See also</span></span>
- [<span data-ttu-id="9065d-113">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9065d-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
