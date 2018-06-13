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
ms.openlocfilehash: 0460086874af38cad348c965237f8c423f18e868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435993"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="7f44a-102">ISymUnmanagedDocument::GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="7f44a-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="7f44a-103">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7f44a-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f44a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f44a-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f44a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f44a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7f44a-106">[out] Ukazatel na proměnnou, která přijímá typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7f44a-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f44a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7f44a-107">Return Value</span></span>  
 <span data-ttu-id="7f44a-108">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7f44a-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f44a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f44a-109">See Also</span></span>  
 [<span data-ttu-id="7f44a-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f44a-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
