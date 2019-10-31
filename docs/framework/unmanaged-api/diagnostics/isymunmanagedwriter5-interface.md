---
title: ISymUnmanagedWriter5 – rozhraní
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 18371b6aefb002f5adf27d43f85194c6c35f6ef5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121643"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="57174-102">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57174-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="57174-103">Rozhraní ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="57174-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57174-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57174-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="57174-105">Metody</span><span class="sxs-lookup"><span data-stu-id="57174-105">Methods</span></span>  
 <span data-ttu-id="57174-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="57174-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="57174-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="57174-107">Method</span></span>|<span data-ttu-id="57174-108">Popis</span><span class="sxs-lookup"><span data-stu-id="57174-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57174-109">CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="57174-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="57174-110">Zavřete část speciální vlastní data pro informace o mapování rozsahu z tokenu na zdroj.</span><span class="sxs-lookup"><span data-stu-id="57174-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="57174-111">Po zavření nebudou moci být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="57174-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="57174-112">MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="57174-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="57174-113">Mapuje daný token metadat na zadaný rozsah řádku zdroje v zadaném zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="57174-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="57174-114">Musí být volána mezi voláním [metody openmaptokenstosourcespans –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [metodou closemaptokenstosourcespans –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="57174-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="57174-115">OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="57174-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="57174-116">Otevřete zvláštní část s vlastními daty, která vygeneruje informace o mapování rozsahu z tokenu na zdroj do.</span><span class="sxs-lookup"><span data-stu-id="57174-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="57174-117">Otevření této části, pokud je již metoda otevřená, nebo naopak, je chyba.</span><span class="sxs-lookup"><span data-stu-id="57174-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57174-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57174-118">Requirements</span></span>  
 <span data-ttu-id="57174-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="57174-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57174-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57174-120">See also</span></span>

- [<span data-ttu-id="57174-121">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="57174-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="57174-122">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57174-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
