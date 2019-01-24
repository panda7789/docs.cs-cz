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
ms.openlocfilehash: 8f5fc951b629a3158fc2c2d6047234fb661f3741
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494896"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="b3ad2-102">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3ad2-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="b3ad2-103">Poskytuje metody, které získáte informace o cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="b3ad2-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="b3ad2-104">Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3ad2-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3ad2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b3ad2-105">Methods</span></span>  
  
|<span data-ttu-id="b3ad2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3ad2-106">Method</span></span>|<span data-ttu-id="b3ad2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b3ad2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3ad2-108">GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="b3ad2-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="b3ad2-109">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b3ad2-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="b3ad2-110">GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="b3ad2-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="b3ad2-111">Získá cestu hledání.</span><span class="sxs-lookup"><span data-stu-id="b3ad2-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="b3ad2-112">GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="b3ad2-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="b3ad2-113">Získá délku cesty hledání.</span><span class="sxs-lookup"><span data-stu-id="b3ad2-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3ad2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3ad2-114">Requirements</span></span>  
 <span data-ttu-id="b3ad2-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b3ad2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ad2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3ad2-116">See also</span></span>
- [<span data-ttu-id="b3ad2-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b3ad2-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
