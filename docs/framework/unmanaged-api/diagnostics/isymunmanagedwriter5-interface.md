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
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="54126-102">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54126-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="54126-103">Isymunmanagedwriter5 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="54126-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54126-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54126-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="54126-105">Metody</span><span class="sxs-lookup"><span data-stu-id="54126-105">Methods</span></span>  
 <span data-ttu-id="54126-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="54126-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="54126-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="54126-107">Method</span></span>|<span data-ttu-id="54126-108">Popis</span><span class="sxs-lookup"><span data-stu-id="54126-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54126-109">Closemaptokenstosourcespans – metoda</span><span class="sxs-lookup"><span data-stu-id="54126-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="54126-110">Zavřete speciální vlastní datové části pro token zdroj span informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="54126-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="54126-111">Po zavření, mohou být přidány žádné další informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="54126-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="54126-112">Maptokentosourcespan – metoda</span><span class="sxs-lookup"><span data-stu-id="54126-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="54126-113">Mapuje token daná metadata na ose zadaná zdrojová span v zadaný zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="54126-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="54126-114">Musí být voláno mezi volání [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="54126-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="54126-115">Openmaptokenstosourcespans – metoda</span><span class="sxs-lookup"><span data-stu-id="54126-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="54126-116">Otevřete část speciální vlastní data pro vydávání informace o tokenu zdroj značky span mapování do.</span><span class="sxs-lookup"><span data-stu-id="54126-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="54126-117">Otevírání v této části, když metoda je již otevřeno, nebo naopak, se o chybu.</span><span class="sxs-lookup"><span data-stu-id="54126-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54126-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54126-118">Requirements</span></span>  
 <span data-ttu-id="54126-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="54126-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54126-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="54126-120">See Also</span></span>  
 [<span data-ttu-id="54126-121">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="54126-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="54126-122">Isymunmanagedwriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54126-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
