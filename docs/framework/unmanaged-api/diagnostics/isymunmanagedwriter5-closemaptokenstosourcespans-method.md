---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce4b41854d5d9324169b1873f431ef81c0a4c5be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677915"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="a29ae-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="a29ae-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="a29ae-103">Zavřete speciální vlastní datové části pro token zdroj zahrnovat informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="a29ae-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="a29ae-104">Po propojení se zavře, je možné přidat žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="a29ae-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29ae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a29ae-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a29ae-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a29ae-106">Return Value</span></span>  
 <span data-ttu-id="a29ae-107">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="a29ae-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a29ae-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a29ae-108">Requirements</span></span>  
 <span data-ttu-id="a29ae-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a29ae-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29ae-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a29ae-110">See also</span></span>
- [<span data-ttu-id="a29ae-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a29ae-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
