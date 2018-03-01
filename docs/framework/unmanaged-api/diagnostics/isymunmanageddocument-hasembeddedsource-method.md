---
title: "ISymUnmanagedDocument::HasEmbeddedSource – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2a903974ac5ac4182bb6fa1664d0c5954cefdb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="07cd8-102">ISymUnmanagedDocument::HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="07cd8-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="07cd8-103">Vrátí `true` jestli má dokument zdroj vložených v symboly pro ladění; jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="07cd8-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07cd8-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07cd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07cd8-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="07cd8-106">[out] Ukazatel na proměnnou, která určuje, jestli má dokument zdroj vložených v symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="07cd8-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07cd8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="07cd8-107">Return Value</span></span>  
 <span data-ttu-id="07cd8-108">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="07cd8-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07cd8-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="07cd8-109">See Also</span></span>  
 [<span data-ttu-id="07cd8-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07cd8-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
