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
ms.openlocfilehash: 3def5db8912bc7e27c0c76898b7bafc8eb3ebbd1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449191"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="e67d9-102">ISymUnmanagedDocument::GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="e67d9-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="e67d9-103">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e67d9-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e67d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e67d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e67d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e67d9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e67d9-106">mimo Ukazatel na proměnnou, která přijímá typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e67d9-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e67d9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e67d9-107">Return Value</span></span>  
 <span data-ttu-id="e67d9-108">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e67d9-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67d9-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e67d9-109">See also</span></span>

- [<span data-ttu-id="e67d9-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e67d9-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
