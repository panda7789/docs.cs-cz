---
title: "ISymUnmanagedScope – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e4d4c83b754945c126913a9d96db47966959fed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="80ddd-102">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80ddd-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="80ddd-103">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="80ddd-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80ddd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="80ddd-104">Methods</span></span>  
  
|<span data-ttu-id="80ddd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-105">Method</span></span>|<span data-ttu-id="80ddd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="80ddd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80ddd-107">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="80ddd-108">Získá podřízené objekty tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="80ddd-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="80ddd-109">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="80ddd-110">Získá posun end pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="80ddd-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="80ddd-111">GetLocalCount – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="80ddd-112">Získá počet místní proměnné definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="80ddd-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="80ddd-113">GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="80ddd-114">Získá místní proměnné definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="80ddd-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="80ddd-115">GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="80ddd-116">Získá metody, která obsahuje tento obor.</span><span class="sxs-lookup"><span data-stu-id="80ddd-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="80ddd-117">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="80ddd-118">Získá obory názvů, které se používají v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="80ddd-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="80ddd-119">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="80ddd-120">Získá nadřazený obor tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="80ddd-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="80ddd-121">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="80ddd-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="80ddd-122">Získá počáteční odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="80ddd-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80ddd-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80ddd-123">Requirements</span></span>  
 <span data-ttu-id="80ddd-124">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="80ddd-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ddd-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="80ddd-125">See Also</span></span>  
 [<span data-ttu-id="80ddd-126">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="80ddd-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="80ddd-127">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80ddd-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
