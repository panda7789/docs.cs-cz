---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d3bc8b00b568f96cd55b7811f310d34c1ff700d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428645"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="43ce4-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="43ce4-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="43ce4-103">Otevřete část speciální vlastní data pro vydávání informace o tokenu zdroj značky span mapování do.</span><span class="sxs-lookup"><span data-stu-id="43ce4-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="43ce4-104">Otevírání v této části, když metoda je již otevřeno, nebo naopak, se o chybu.</span><span class="sxs-lookup"><span data-stu-id="43ce4-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ce4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43ce4-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="43ce4-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="43ce4-106">Return Value</span></span>  
 <span data-ttu-id="43ce4-107">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="43ce4-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ce4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43ce4-108">Requirements</span></span>  
 <span data-ttu-id="43ce4-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="43ce4-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ce4-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="43ce4-110">See Also</span></span>  
 [<span data-ttu-id="43ce4-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43ce4-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
