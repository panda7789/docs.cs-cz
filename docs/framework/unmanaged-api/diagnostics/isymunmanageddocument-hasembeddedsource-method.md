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
ms.openlocfilehash: 350aecb9f9c99c9aa44ae6df6d31c7cb69ae5760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430342"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="677fe-102">ISymUnmanagedDocument::HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="677fe-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="677fe-103">Vrátí `true` jestli má dokument zdroj vložených v symboly pro ladění; jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="677fe-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="677fe-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="677fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="677fe-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="677fe-106">[out] Ukazatel na proměnnou, která určuje, jestli má dokument zdroj vložených v symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="677fe-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="677fe-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="677fe-107">Return Value</span></span>  
 <span data-ttu-id="677fe-108">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="677fe-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677fe-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="677fe-109">See Also</span></span>  
 [<span data-ttu-id="677fe-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="677fe-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
