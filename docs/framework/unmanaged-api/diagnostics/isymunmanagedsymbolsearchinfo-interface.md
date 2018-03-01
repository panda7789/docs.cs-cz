---
title: "ISymUnmanagedSymbolSearchInfo – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 441330471906a891646ad55eb73ec25b44800cbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="7aca6-102">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7aca6-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="7aca6-103">Poskytuje metody, které získat informace o cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7aca6-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="7aca6-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7aca6-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7aca6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7aca6-105">Methods</span></span>  
  
|<span data-ttu-id="7aca6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7aca6-106">Method</span></span>|<span data-ttu-id="7aca6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7aca6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7aca6-108">GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="7aca6-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="7aca6-109">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7aca6-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="7aca6-110">GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="7aca6-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="7aca6-111">Získá cestu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7aca6-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="7aca6-112">GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="7aca6-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="7aca6-113">Získá délku cesty vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7aca6-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7aca6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7aca6-114">Requirements</span></span>  
 <span data-ttu-id="7aca6-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7aca6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aca6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aca6-116">See Also</span></span>  
 [<span data-ttu-id="7aca6-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7aca6-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
