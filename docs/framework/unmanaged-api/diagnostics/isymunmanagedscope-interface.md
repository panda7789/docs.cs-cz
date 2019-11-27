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
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446262"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="531f0-102">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="531f0-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="531f0-103">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="531f0-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="531f0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="531f0-104">Methods</span></span>  
  
|<span data-ttu-id="531f0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-105">Method</span></span>|<span data-ttu-id="531f0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="531f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="531f0-107">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="531f0-108">Získá podřízené objekty tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="531f0-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="531f0-109">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="531f0-110">Získá posunutí konce tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="531f0-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="531f0-111">GetLocalCount – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="531f0-112">Získá počet místních proměnných definovaných v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="531f0-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="531f0-113">GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="531f0-114">Získá místní proměnné definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="531f0-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="531f0-115">GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="531f0-116">Získá metodu, která obsahuje tento obor.</span><span class="sxs-lookup"><span data-stu-id="531f0-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="531f0-117">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="531f0-118">Načte obory názvů, které jsou používány v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="531f0-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="531f0-119">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="531f0-120">Získá nadřazený obor tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="531f0-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="531f0-121">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="531f0-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="531f0-122">Získá posun začátku tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="531f0-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="531f0-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="531f0-123">Requirements</span></span>  
 <span data-ttu-id="531f0-124">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="531f0-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531f0-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="531f0-125">See also</span></span>

- [<span data-ttu-id="531f0-126">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="531f0-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="531f0-127">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="531f0-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
