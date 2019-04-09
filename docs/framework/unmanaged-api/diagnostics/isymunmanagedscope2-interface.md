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
ms.openlocfilehash: 0109b25b1cdc42204fc4873577e495641c4ec4fd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131453"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="8aa11-102">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8aa11-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="8aa11-103">Představuje lexikální rozsah v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="8aa11-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="8aa11-104">Toto rozhraní rozšiřuje [isymunmanagedscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní s metodami, které získávají informace o konstanty definované v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="8aa11-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8aa11-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8aa11-105">Methods</span></span>  
  
|<span data-ttu-id="8aa11-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8aa11-106">Method</span></span>|<span data-ttu-id="8aa11-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8aa11-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8aa11-108">GetConstantCount – metoda</span><span class="sxs-lookup"><span data-stu-id="8aa11-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="8aa11-109">Získá počet konstanty definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="8aa11-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="8aa11-110">GetConstants – metoda</span><span class="sxs-lookup"><span data-stu-id="8aa11-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="8aa11-111">Získá místní konstanty definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="8aa11-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8aa11-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8aa11-112">Requirements</span></span>  
 <span data-ttu-id="8aa11-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8aa11-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa11-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8aa11-114">See also</span></span>

- [<span data-ttu-id="8aa11-115">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8aa11-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="8aa11-116">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8aa11-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
