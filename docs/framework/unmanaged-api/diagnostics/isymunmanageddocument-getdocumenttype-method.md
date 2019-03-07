---
title: ISymUnmanagedDocument::GetDocumentType – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 107039643e097ada1756054b2d14fcf0cbb71c00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493372"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="68478-102">ISymUnmanagedDocument::GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="68478-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="68478-103">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="68478-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68478-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68478-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68478-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68478-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="68478-106">[out] Ukazovat na proměnnou, která přijímá typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="68478-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68478-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="68478-107">Return Value</span></span>  
 <span data-ttu-id="68478-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="68478-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68478-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68478-109">See also</span></span>
- [<span data-ttu-id="68478-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68478-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
