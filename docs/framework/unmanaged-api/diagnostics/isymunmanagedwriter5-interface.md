---
title: ISymUnmanagedWriter5 – rozhraní
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493575"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="1e3c4-102">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e3c4-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="1e3c4-103">Rozhraní ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="1e3c4-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e3c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e3c4-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="1e3c4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1e3c4-105">Methods</span></span>  
 <span data-ttu-id="1e3c4-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="1e3c4-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="1e3c4-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="1e3c4-107">Method</span></span>|<span data-ttu-id="1e3c4-108">Description</span><span class="sxs-lookup"><span data-stu-id="1e3c4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e3c4-109">CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="1e3c4-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="1e3c4-110">Zavřete část speciální vlastní data pro informace o mapování rozsahu z tokenu na zdroj.</span><span class="sxs-lookup"><span data-stu-id="1e3c4-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="1e3c4-111">Po zavření nebudou moci být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="1e3c4-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="1e3c4-112">MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="1e3c4-112">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="1e3c4-113">Mapuje daný token metadat na zadaný rozsah řádku zdroje v zadaném zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="1e3c4-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="1e3c4-114">Musí být volána mezi voláním [metody openmaptokenstosourcespans –](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [metodou closemaptokenstosourcespans –](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="1e3c4-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="1e3c4-115">OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="1e3c4-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="1e3c4-116">Otevřete zvláštní část s vlastními daty, která vygeneruje informace o mapování rozsahu z tokenu na zdroj do.</span><span class="sxs-lookup"><span data-stu-id="1e3c4-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="1e3c4-117">Otevření této části, pokud je již metoda otevřená, nebo naopak, je chyba.</span><span class="sxs-lookup"><span data-stu-id="1e3c4-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e3c4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e3c4-118">Requirements</span></span>  
 <span data-ttu-id="1e3c4-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1e3c4-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e3c4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e3c4-120">See also</span></span>

- [<span data-ttu-id="1e3c4-121">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="1e3c4-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="1e3c4-122">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e3c4-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
