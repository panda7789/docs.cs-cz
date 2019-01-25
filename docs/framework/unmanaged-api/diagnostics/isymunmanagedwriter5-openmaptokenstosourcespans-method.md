---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60c1984e6193481efdaaeb82a2bc025aef67a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534435"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="06e41-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="06e41-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="06e41-103">Otevřete část speciální vlastní data a vygenerovat token zdroj značky span mapování informace do.</span><span class="sxs-lookup"><span data-stu-id="06e41-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="06e41-104">Otevírání tohoto oddílu při metody je již otevřen nebo naopak, je chybou.</span><span class="sxs-lookup"><span data-stu-id="06e41-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e41-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06e41-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="06e41-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06e41-106">Return Value</span></span>  
 <span data-ttu-id="06e41-107">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="06e41-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06e41-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06e41-108">Requirements</span></span>  
 <span data-ttu-id="06e41-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06e41-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e41-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06e41-110">See also</span></span>
- [<span data-ttu-id="06e41-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06e41-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
