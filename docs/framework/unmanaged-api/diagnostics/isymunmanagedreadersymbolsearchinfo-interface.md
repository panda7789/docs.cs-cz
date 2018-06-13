---
title: ISymUnmanagedReaderSymbolSearchInfo – rozhraní
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e2a0352f52bd617738e6d7cfe33b4d7acdb6da0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427655"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="7a1a9-102">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a1a9-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="7a1a9-103">Poskytuje metody, které získání informací o symbolu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7a1a9-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="7a1a9-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a1a9-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a1a9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7a1a9-105">Methods</span></span>  
  
|<span data-ttu-id="7a1a9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7a1a9-106">Method</span></span>|<span data-ttu-id="7a1a9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7a1a9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a1a9-108">GetSymbolSearchInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="7a1a9-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="7a1a9-109">Získá informace o vyhledávání symbolu.</span><span class="sxs-lookup"><span data-stu-id="7a1a9-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="7a1a9-110">GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7a1a9-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="7a1a9-111">Získá počet informací o symbolu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7a1a9-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a1a9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a1a9-112">Requirements</span></span>  
 <span data-ttu-id="7a1a9-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a1a9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1a9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a1a9-114">See Also</span></span>  
 [<span data-ttu-id="7a1a9-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7a1a9-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
