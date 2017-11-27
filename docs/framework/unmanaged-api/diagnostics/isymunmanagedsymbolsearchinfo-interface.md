---
title: "ISymUnmanagedSymbolSearchInfo – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo
helpviewer_keywords: ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 967511238dceb752ab30ce10dcaba8b65f4dd9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="7b9a0-102">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b9a0-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="7b9a0-103">Poskytuje metody, které získat informace o cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7b9a0-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="7b9a0-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b9a0-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b9a0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7b9a0-105">Methods</span></span>  
  
|<span data-ttu-id="7b9a0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7b9a0-106">Method</span></span>|<span data-ttu-id="7b9a0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7b9a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b9a0-108">Gethresult – metoda</span><span class="sxs-lookup"><span data-stu-id="7b9a0-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="7b9a0-109">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7b9a0-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="7b9a0-110">Getsearchpath – metoda</span><span class="sxs-lookup"><span data-stu-id="7b9a0-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="7b9a0-111">Získá cestu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7b9a0-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="7b9a0-112">Getsearchpathlength – metoda</span><span class="sxs-lookup"><span data-stu-id="7b9a0-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="7b9a0-113">Získá délku cesty vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7b9a0-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b9a0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b9a0-114">Requirements</span></span>  
 <span data-ttu-id="7b9a0-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7b9a0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b9a0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b9a0-116">See Also</span></span>  
 [<span data-ttu-id="7b9a0-117">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7b9a0-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
