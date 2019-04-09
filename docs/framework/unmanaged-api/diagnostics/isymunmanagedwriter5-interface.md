---
title: ISymUnmanagedWriter5 – rozhraní
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6ed8c6e61c558a4bc9e3f92d559615ac93ecff8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144232"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="3c539-102">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c539-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="3c539-103">Isymunmanagedwriter5 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3c539-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c539-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c539-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="3c539-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3c539-105">Methods</span></span>  
 <span data-ttu-id="3c539-106">Toto rozhraní obsahuje následující dvě metody:</span><span class="sxs-lookup"><span data-stu-id="3c539-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="3c539-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c539-107">Method</span></span>|<span data-ttu-id="3c539-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3c539-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c539-109">CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="3c539-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="3c539-110">Zavřete speciální vlastní datové části pro token zdroj zahrnovat informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="3c539-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="3c539-111">Po propojení se zavře, je možné přidat žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="3c539-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="3c539-112">MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="3c539-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="3c539-113">Mapy token daná metadata do daného zdroje řádku span zadaného zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="3c539-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="3c539-114">Musí být volána mezi voláními [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c539-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="3c539-115">OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="3c539-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="3c539-116">Otevřete část speciální vlastní data a vygenerovat token zdroj značky span mapování informace do.</span><span class="sxs-lookup"><span data-stu-id="3c539-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="3c539-117">Otevírání tohoto oddílu při metody je již otevřen nebo naopak, je chybou.</span><span class="sxs-lookup"><span data-stu-id="3c539-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c539-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c539-118">Requirements</span></span>  
 <span data-ttu-id="3c539-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3c539-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c539-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c539-120">See also</span></span>

- [<span data-ttu-id="3c539-121">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="3c539-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3c539-122">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c539-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
