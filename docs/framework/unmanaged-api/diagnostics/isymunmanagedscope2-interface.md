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
ms.openlocfilehash: 3374097c8d343fed6badf046742ca556d2a92f3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446226"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="b04a4-102">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b04a4-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="b04a4-103">Represents a lexical scope within a method.</span><span class="sxs-lookup"><span data-stu-id="b04a4-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="b04a4-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span><span class="sxs-lookup"><span data-stu-id="b04a4-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b04a4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b04a4-105">Methods</span></span>  
  
|<span data-ttu-id="b04a4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b04a4-106">Method</span></span>|<span data-ttu-id="b04a4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b04a4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b04a4-108">GetConstantCount – metoda</span><span class="sxs-lookup"><span data-stu-id="b04a4-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="b04a4-109">Gets a count of the constants defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="b04a4-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="b04a4-110">GetConstants – metoda</span><span class="sxs-lookup"><span data-stu-id="b04a4-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="b04a4-111">Gets the local constants defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="b04a4-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b04a4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b04a4-112">Requirements</span></span>  
 <span data-ttu-id="b04a4-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b04a4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04a4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b04a4-114">See also</span></span>

- [<span data-ttu-id="b04a4-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b04a4-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="b04a4-116">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b04a4-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
