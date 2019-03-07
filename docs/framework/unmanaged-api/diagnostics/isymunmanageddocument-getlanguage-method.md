---
title: ISymUnmanagedDocument::GetLanguage – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fe5686f516f967ffd182788add643387cb8af9a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473965"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="4b580-102">ISymUnmanagedDocument::GetLanguage – metoda</span><span class="sxs-lookup"><span data-stu-id="4b580-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="4b580-103">Získá identifikátor jazyka tohoto dokumentu</span><span class="sxs-lookup"><span data-stu-id="4b580-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b580-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b580-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b580-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b580-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4b580-106">[out] Ukazovat na proměnnou, která přijímá identifikátor jazyka.</span><span class="sxs-lookup"><span data-stu-id="4b580-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b580-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4b580-107">Return Value</span></span>  
 <span data-ttu-id="4b580-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="4b580-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b580-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b580-109">See also</span></span>
- [<span data-ttu-id="4b580-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b580-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
