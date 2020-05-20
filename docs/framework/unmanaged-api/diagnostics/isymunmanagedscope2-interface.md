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
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610857"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="fdc2d-102">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdc2d-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="fdc2d-103">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="fdc2d-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="fdc2d-104">Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedScope](isymunmanagedscope-interface.md) o metody, které získávají informace o konstantách definovaných v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="fdc2d-104">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdc2d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fdc2d-105">Methods</span></span>  
  
|<span data-ttu-id="fdc2d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fdc2d-106">Method</span></span>|<span data-ttu-id="fdc2d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fdc2d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdc2d-108">GetConstantCount – metoda</span><span class="sxs-lookup"><span data-stu-id="fdc2d-108">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="fdc2d-109">Získá počet konstant definovaných v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="fdc2d-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="fdc2d-110">GetConstants – metoda</span><span class="sxs-lookup"><span data-stu-id="fdc2d-110">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="fdc2d-111">Získá místní konstanty definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="fdc2d-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fdc2d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdc2d-112">Requirements</span></span>  
 <span data-ttu-id="fdc2d-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fdc2d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc2d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdc2d-114">See also</span></span>

- [<span data-ttu-id="fdc2d-115">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="fdc2d-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="fdc2d-116">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdc2d-116">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
