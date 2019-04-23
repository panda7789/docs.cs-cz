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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228156"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="f868d-102">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f868d-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="f868d-103">Představuje lexikální rozsah v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="f868d-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f868d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f868d-104">Methods</span></span>  
  
|<span data-ttu-id="f868d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-105">Method</span></span>|<span data-ttu-id="f868d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f868d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f868d-107">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="f868d-108">Získá podřízené objekty tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="f868d-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="f868d-109">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="f868d-110">Získá koncové odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="f868d-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="f868d-111">GetLocalCount – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="f868d-112">Získá počet místních proměnných definovaných v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="f868d-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="f868d-113">GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="f868d-114">Získá místní proměnné definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="f868d-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="f868d-115">GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="f868d-116">Získá metody, která obsahuje tento obor.</span><span class="sxs-lookup"><span data-stu-id="f868d-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="f868d-117">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="f868d-118">Získá obory názvů, které se používají v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="f868d-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="f868d-119">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="f868d-120">Získá nadřazený obor tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="f868d-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="f868d-121">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f868d-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="f868d-122">Získá počáteční odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="f868d-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f868d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f868d-123">Requirements</span></span>  
 <span data-ttu-id="f868d-124">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f868d-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f868d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f868d-125">See also</span></span>

- [<span data-ttu-id="f868d-126">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f868d-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f868d-127">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f868d-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
