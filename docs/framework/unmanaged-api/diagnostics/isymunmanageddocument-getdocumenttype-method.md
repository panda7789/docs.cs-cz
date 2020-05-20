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
ms.openlocfilehash: 5ec69aa06816b117fb05853001e59532629504c4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614601"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="6bd14-102">ISymUnmanagedDocument::GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="6bd14-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="6bd14-103">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6bd14-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bd14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bd14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bd14-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6bd14-106">mimo Ukazatel na proměnnou, která přijímá typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6bd14-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bd14-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6bd14-107">Return Value</span></span>  
 <span data-ttu-id="6bd14-108">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6bd14-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd14-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bd14-109">See also</span></span>

- [<span data-ttu-id="6bd14-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bd14-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
