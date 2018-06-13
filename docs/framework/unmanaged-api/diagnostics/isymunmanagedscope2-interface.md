---
title: ISymUnmanagedScope2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a33d8b489551dc69542e1b12bcf83602ec5a2008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427245"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="52ae5-102">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52ae5-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="52ae5-103">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="52ae5-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="52ae5-104">Toto rozhraní rozšiřuje [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní s metody, které získat informace o konstanty definované v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="52ae5-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52ae5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="52ae5-105">Methods</span></span>  
  
|<span data-ttu-id="52ae5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="52ae5-106">Method</span></span>|<span data-ttu-id="52ae5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="52ae5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52ae5-108">GetConstantCount – metoda</span><span class="sxs-lookup"><span data-stu-id="52ae5-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="52ae5-109">Získá počet konstanty definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="52ae5-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="52ae5-110">GetConstants – metoda</span><span class="sxs-lookup"><span data-stu-id="52ae5-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="52ae5-111">Získá místní konstanty definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="52ae5-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52ae5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52ae5-112">Requirements</span></span>  
 <span data-ttu-id="52ae5-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="52ae5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ae5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="52ae5-114">See Also</span></span>  
 [<span data-ttu-id="52ae5-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="52ae5-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="52ae5-116">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52ae5-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
