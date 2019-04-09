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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094265"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="912ab-102">ISymUnmanagedDocument::HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="912ab-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="912ab-103">Vrátí `true` Pokud dokument má zdroj součástí symboly ladění; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="912ab-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="912ab-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="912ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="912ab-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="912ab-106">[out] Ukazatel na proměnnou, která určuje, jestli má zdrojový dokument vložit symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="912ab-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="912ab-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="912ab-107">Return Value</span></span>  
 <span data-ttu-id="912ab-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="912ab-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912ab-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="912ab-109">See also</span></span>

- [<span data-ttu-id="912ab-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="912ab-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
