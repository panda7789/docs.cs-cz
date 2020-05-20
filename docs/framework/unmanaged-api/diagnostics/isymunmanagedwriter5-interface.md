---
title: ISymUnmanagedWriter5 – rozhraní
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: bdc630c3c94c7d03b736efa0a95665f10aac7c6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609427"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="4fe93-102">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fe93-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="4fe93-103">Rozhraní ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="4fe93-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fe93-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="4fe93-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4fe93-105">Methods</span></span>  
 <span data-ttu-id="4fe93-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="4fe93-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="4fe93-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="4fe93-107">Method</span></span>|<span data-ttu-id="4fe93-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe93-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fe93-109">CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="4fe93-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="4fe93-110">Zavřete část speciální vlastní data pro informace o mapování rozsahu z tokenu na zdroj.</span><span class="sxs-lookup"><span data-stu-id="4fe93-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="4fe93-111">Po zavření nebudou moci být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="4fe93-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="4fe93-112">MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="4fe93-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="4fe93-113">Mapuje daný token metadat na zadaný rozsah řádku zdroje v zadaném zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="4fe93-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="4fe93-114">Musí být volána mezi voláním [metody openmaptokenstosourcespans –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [metodou closemaptokenstosourcespans –](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="4fe93-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="4fe93-115">OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="4fe93-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="4fe93-116">Otevřete zvláštní část s vlastními daty, která vygeneruje informace o mapování rozsahu z tokenu na zdroj do.</span><span class="sxs-lookup"><span data-stu-id="4fe93-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="4fe93-117">Otevření této části, pokud je již metoda otevřená, nebo naopak, je chyba.</span><span class="sxs-lookup"><span data-stu-id="4fe93-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fe93-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fe93-118">Requirements</span></span>  
 <span data-ttu-id="4fe93-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4fe93-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe93-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fe93-120">See also</span></span>

- [<span data-ttu-id="4fe93-121">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="4fe93-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="4fe93-122">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fe93-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
