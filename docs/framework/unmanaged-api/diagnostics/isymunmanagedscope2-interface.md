---
title: "ISymUnmanagedScope2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2
helpviewer_keywords: ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d2ec846a34b2d3424f7bf8b54f1d4d12d4102e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="7fe18-102">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fe18-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="7fe18-103">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="7fe18-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="7fe18-104">Toto rozhraní rozšiřuje [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní s metody, které získat informace o konstanty definované v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="7fe18-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fe18-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7fe18-105">Methods</span></span>  
  
|<span data-ttu-id="7fe18-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7fe18-106">Method</span></span>|<span data-ttu-id="7fe18-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7fe18-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fe18-108">GetConstantCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7fe18-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="7fe18-109">Získá počet konstanty definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="7fe18-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="7fe18-110">GetConstants – metoda</span><span class="sxs-lookup"><span data-stu-id="7fe18-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="7fe18-111">Získá místní konstanty definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="7fe18-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fe18-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fe18-112">Requirements</span></span>  
 <span data-ttu-id="7fe18-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7fe18-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe18-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fe18-114">See Also</span></span>  
 [<span data-ttu-id="7fe18-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7fe18-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="7fe18-116">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fe18-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
