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
ms.openlocfilehash: 620d303bcd33a4d04155850ec2c1b6293bf788d1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493255"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="a35c7-102">ISymUnmanagedDocument::HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="a35c7-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="a35c7-103">Vrátí `true` Pokud dokument má zdroj součástí symboly ladění; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="a35c7-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a35c7-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a35c7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a35c7-106">[out] Ukazatel na proměnnou, která určuje, jestli má zdrojový dokument vložit symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="a35c7-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a35c7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a35c7-107">Return Value</span></span>  
 <span data-ttu-id="a35c7-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="a35c7-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35c7-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a35c7-109">See also</span></span>
- [<span data-ttu-id="a35c7-110">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a35c7-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
