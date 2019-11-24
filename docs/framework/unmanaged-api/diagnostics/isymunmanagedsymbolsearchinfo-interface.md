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
ms.openlocfilehash: d7371361b074454e8aa359c49b964193c12f3034
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446145"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="f1294-102">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1294-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="f1294-103">Provides methods that get information about the search path.</span><span class="sxs-lookup"><span data-stu-id="f1294-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="f1294-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f1294-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1294-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f1294-105">Methods</span></span>  
  
|<span data-ttu-id="f1294-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f1294-106">Method</span></span>|<span data-ttu-id="f1294-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f1294-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1294-108">GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="f1294-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="f1294-109">Gets the HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f1294-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="f1294-110">GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="f1294-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="f1294-111">Gets the search path.</span><span class="sxs-lookup"><span data-stu-id="f1294-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="f1294-112">GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="f1294-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="f1294-113">Gets the search path length.</span><span class="sxs-lookup"><span data-stu-id="f1294-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1294-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1294-114">Requirements</span></span>  
 <span data-ttu-id="f1294-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f1294-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1294-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1294-116">See also</span></span>

- [<span data-ttu-id="f1294-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f1294-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
