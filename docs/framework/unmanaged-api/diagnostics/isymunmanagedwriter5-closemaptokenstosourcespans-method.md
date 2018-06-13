---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 653dd933066898c1954cfbcc57c0c0493e47b4be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428609"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="e5d3f-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="e5d3f-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="e5d3f-103">Zavřete speciální vlastní datové části pro token zdroj span informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="e5d3f-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="e5d3f-104">Po zavření, mohou být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="e5d3f-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d3f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5d3f-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e5d3f-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5d3f-106">Return Value</span></span>  
 <span data-ttu-id="e5d3f-107">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e5d3f-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5d3f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5d3f-108">Requirements</span></span>  
 <span data-ttu-id="e5d3f-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e5d3f-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d3f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5d3f-110">See Also</span></span>  
 [<span data-ttu-id="e5d3f-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5d3f-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
