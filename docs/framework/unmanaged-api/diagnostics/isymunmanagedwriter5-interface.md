---
title: "ISymUnmanagedWriter5 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 701b8de977d49a7d93f393b320bcb9d0d780c7bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="b7568-102">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7568-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="b7568-103">Isymunmanagedwriter5 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7568-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7568-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7568-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="b7568-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b7568-105">Methods</span></span>  
 <span data-ttu-id="b7568-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="b7568-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="b7568-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="b7568-107">Method</span></span>|<span data-ttu-id="b7568-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b7568-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7568-109">CloseMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="b7568-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="b7568-110">Zavřete speciální vlastní datové části pro token zdroj span informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="b7568-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="b7568-111">Po zavření, mohou být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="b7568-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="b7568-112">MapTokenToSourceSpan – metoda</span><span class="sxs-lookup"><span data-stu-id="b7568-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="b7568-113">Mapuje token daná metadata na ose zadaná zdrojová span v zadaný zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="b7568-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="b7568-114">Musí být voláno mezi volání [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="b7568-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="b7568-115">OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="b7568-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="b7568-116">Otevřete část speciální vlastní data pro vydávání informace o tokenu zdroj značky span mapování do.</span><span class="sxs-lookup"><span data-stu-id="b7568-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="b7568-117">Otevírání v této části, když metoda je již otevřeno, nebo naopak, se o chybu.</span><span class="sxs-lookup"><span data-stu-id="b7568-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7568-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7568-118">Requirements</span></span>  
 <span data-ttu-id="b7568-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b7568-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7568-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7568-120">See Also</span></span>  
 [<span data-ttu-id="b7568-121">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b7568-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="b7568-122">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7568-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
