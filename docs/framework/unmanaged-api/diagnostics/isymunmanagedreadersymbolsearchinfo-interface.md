---
title: "ISymUnmanagedReaderSymbolSearchInfo – rozhraní"
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
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7f53e45eb321f114483648afc63d2669065a791
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="678aa-102">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="678aa-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="678aa-103">Poskytuje metody, které získání informací o symbolu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="678aa-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="678aa-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="678aa-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="678aa-105">Metody</span><span class="sxs-lookup"><span data-stu-id="678aa-105">Methods</span></span>  
  
|<span data-ttu-id="678aa-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="678aa-106">Method</span></span>|<span data-ttu-id="678aa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="678aa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="678aa-108">GetSymbolSearchInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="678aa-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="678aa-109">Získá informace o vyhledávání symbolu.</span><span class="sxs-lookup"><span data-stu-id="678aa-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="678aa-110">GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="678aa-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="678aa-111">Získá počet informací o symbolu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="678aa-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="678aa-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="678aa-112">Requirements</span></span>  
 <span data-ttu-id="678aa-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="678aa-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678aa-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="678aa-114">See Also</span></span>  
 [<span data-ttu-id="678aa-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="678aa-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
