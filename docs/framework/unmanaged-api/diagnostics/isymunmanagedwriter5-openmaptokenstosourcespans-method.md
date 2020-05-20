---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 82b46ea315009b65254735d44e355154b83b22e2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609492"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="99d85-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="99d85-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="99d85-103">Otevřete zvláštní část s vlastními daty, která vygeneruje informace o mapování rozsahu z tokenu na zdroj do.</span><span class="sxs-lookup"><span data-stu-id="99d85-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="99d85-104">Otevření této části, pokud je již metoda otevřená, nebo naopak, je chyba.</span><span class="sxs-lookup"><span data-stu-id="99d85-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d85-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99d85-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="99d85-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="99d85-106">Return Value</span></span>  
 <span data-ttu-id="99d85-107">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="99d85-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99d85-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99d85-108">Requirements</span></span>  
 <span data-ttu-id="99d85-109">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="99d85-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d85-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="99d85-110">See also</span></span>

- [<span data-ttu-id="99d85-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99d85-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
