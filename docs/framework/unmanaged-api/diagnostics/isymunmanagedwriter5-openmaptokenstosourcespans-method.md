---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 004e1ddae8a6c0262846422a2eeb4314a4c82f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121611"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="dda8e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="dda8e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="dda8e-103">Otevřete zvláštní část s vlastními daty, která vygeneruje informace o mapování rozsahu z tokenu na zdroj do.</span><span class="sxs-lookup"><span data-stu-id="dda8e-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="dda8e-104">Otevření této části, pokud je již metoda otevřená, nebo naopak, je chyba.</span><span class="sxs-lookup"><span data-stu-id="dda8e-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda8e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dda8e-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dda8e-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dda8e-106">Return Value</span></span>  
 <span data-ttu-id="dda8e-107">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="dda8e-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda8e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dda8e-108">Requirements</span></span>  
 <span data-ttu-id="dda8e-109">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dda8e-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda8e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dda8e-110">See also</span></span>

- [<span data-ttu-id="dda8e-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dda8e-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
