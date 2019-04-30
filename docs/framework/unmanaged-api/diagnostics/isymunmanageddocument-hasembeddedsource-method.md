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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939799"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="e1659-102">ISymUnmanagedDocument::HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="e1659-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="e1659-103">Vrátí `true` Pokud dokument má zdroj součástí symboly ladění; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="e1659-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1659-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1659-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1659-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1659-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e1659-106">[out] Ukazatel na proměnnou, která určuje, jestli má zdrojový dokument vložit symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e1659-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1659-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e1659-107">Return Value</span></span>  
 <span data-ttu-id="e1659-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="e1659-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1659-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1659-109">See also</span></span>

- [<span data-ttu-id="e1659-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1659-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
