---
title: ISymUnmanagedSymbolSearchInfo – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5dce9653d3fef534ac6567e36a4c8213e13ab231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429166"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="be352-102">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be352-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="be352-103">Poskytuje metody, které získat informace o cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="be352-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="be352-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be352-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be352-105">Metody</span><span class="sxs-lookup"><span data-stu-id="be352-105">Methods</span></span>  
  
|<span data-ttu-id="be352-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="be352-106">Method</span></span>|<span data-ttu-id="be352-107">Popis</span><span class="sxs-lookup"><span data-stu-id="be352-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be352-108">GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="be352-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="be352-109">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="be352-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="be352-110">GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="be352-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="be352-111">Získá cestu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="be352-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="be352-112">GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="be352-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="be352-113">Získá délku cesty vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="be352-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be352-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be352-114">Requirements</span></span>  
 <span data-ttu-id="be352-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="be352-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be352-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="be352-116">See Also</span></span>  
 [<span data-ttu-id="be352-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="be352-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
