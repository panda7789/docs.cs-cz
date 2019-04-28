---
title: ISymUnmanagedScope – rozhraní
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 809368ea19528a7ce00d4fcada06ef5724eb79a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761634"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="cd3de-102">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd3de-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="cd3de-103">Představuje lexikální rozsah v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="cd3de-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd3de-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cd3de-104">Methods</span></span>  
  
|<span data-ttu-id="cd3de-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-105">Method</span></span>|<span data-ttu-id="cd3de-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cd3de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd3de-107">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="cd3de-108">Získá podřízené objekty tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cd3de-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="cd3de-109">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="cd3de-110">Získá koncové odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="cd3de-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="cd3de-111">GetLocalCount – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="cd3de-112">Získá počet místních proměnných definovaných v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="cd3de-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="cd3de-113">GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="cd3de-114">Získá místní proměnné definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="cd3de-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="cd3de-115">GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="cd3de-116">Získá metody, která obsahuje tento obor.</span><span class="sxs-lookup"><span data-stu-id="cd3de-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="cd3de-117">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="cd3de-118">Získá obory názvů, které se používají v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="cd3de-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="cd3de-119">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="cd3de-120">Získá nadřazený obor tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cd3de-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="cd3de-121">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="cd3de-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="cd3de-122">Získá počáteční odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="cd3de-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd3de-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd3de-123">Requirements</span></span>  
 <span data-ttu-id="cd3de-124">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cd3de-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3de-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd3de-125">See also</span></span>

- [<span data-ttu-id="cd3de-126">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="cd3de-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="cd3de-127">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd3de-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
