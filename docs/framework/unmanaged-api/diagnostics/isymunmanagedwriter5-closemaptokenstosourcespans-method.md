---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 43c35596d31842b85bbdc96a63413a176a59a172
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121645"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="8006b-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="8006b-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="8006b-103">Zavřete část speciální vlastní data pro informace o mapování rozsahu z tokenu na zdroj.</span><span class="sxs-lookup"><span data-stu-id="8006b-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="8006b-104">Po zavření nebudou moci být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="8006b-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8006b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8006b-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8006b-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8006b-106">Return Value</span></span>  
 <span data-ttu-id="8006b-107">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="8006b-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8006b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8006b-108">Requirements</span></span>  
 <span data-ttu-id="8006b-109">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8006b-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8006b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8006b-110">See also</span></span>

- [<span data-ttu-id="8006b-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8006b-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
