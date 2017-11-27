---
title: "ISymUnmanagedScope – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope
helpviewer_keywords: ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d25d62dd42e3e93124c9a3bd8945be265f192663
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="efe10-102">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efe10-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="efe10-103">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="efe10-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efe10-104">Metody</span><span class="sxs-lookup"><span data-stu-id="efe10-104">Methods</span></span>  
  
|<span data-ttu-id="efe10-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-105">Method</span></span>|<span data-ttu-id="efe10-106">Popis</span><span class="sxs-lookup"><span data-stu-id="efe10-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efe10-107">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="efe10-108">Získá podřízené objekty tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="efe10-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="efe10-109">Getendoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="efe10-110">Získá posun end pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="efe10-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="efe10-111">Getlocalcount – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="efe10-112">Získá počet místní proměnné definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="efe10-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="efe10-113">GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="efe10-114">Získá místní proměnné definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="efe10-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="efe10-115">Getmethod – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="efe10-116">Získá metody, která obsahuje tento obor.</span><span class="sxs-lookup"><span data-stu-id="efe10-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="efe10-117">Getnamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="efe10-118">Získá obory názvů, které se používají v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="efe10-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="efe10-119">Getparent – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="efe10-120">Získá nadřazený obor tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="efe10-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="efe10-121">Getstartoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="efe10-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="efe10-122">Získá počáteční odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="efe10-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="efe10-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efe10-123">Requirements</span></span>  
 <span data-ttu-id="efe10-124">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="efe10-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe10-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="efe10-125">See Also</span></span>  
 [<span data-ttu-id="efe10-126">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="efe10-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="efe10-127">Isymunmanagedscope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efe10-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
