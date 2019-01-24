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
ms.openlocfilehash: da19a77637e64fec676fdaac7ba56d47b5b07769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549886"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="f57f0-102">ISymUnmanagedDocumentWriter::SetSource – metoda</span><span class="sxs-lookup"><span data-stu-id="f57f0-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="f57f0-103">Nastaví vložený zdroj pro dokument, u kterého probíhá zápis.</span><span class="sxs-lookup"><span data-stu-id="f57f0-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f57f0-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f57f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f57f0-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="f57f0-106">[in] A `ULONG32` , který obsahuje velikost `source` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f57f0-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="f57f0-107">[in] Vyrovnávací paměť, která ukládá vloženého zdroje.</span><span class="sxs-lookup"><span data-stu-id="f57f0-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f57f0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f57f0-108">Return Value</span></span>  
 <span data-ttu-id="f57f0-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f57f0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f57f0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f57f0-110">Requirements</span></span>  
 <span data-ttu-id="f57f0-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f57f0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57f0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f57f0-112">See also</span></span>
- [<span data-ttu-id="f57f0-113">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f57f0-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
