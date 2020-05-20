---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 053727604c795bf43a9b1658d5841fe85f53090a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614627"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="0f250-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="0f250-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="0f250-103">Zavřete část speciální vlastní data pro informace o mapování rozsahu z tokenu na zdroj.</span><span class="sxs-lookup"><span data-stu-id="0f250-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="0f250-104">Po zavření nebudou moci být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="0f250-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f250-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f250-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0f250-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0f250-106">Return Value</span></span>  
 <span data-ttu-id="0f250-107">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0f250-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f250-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f250-108">Requirements</span></span>  
 <span data-ttu-id="0f250-109">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0f250-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f250-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f250-110">See also</span></span>

- [<span data-ttu-id="0f250-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f250-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
