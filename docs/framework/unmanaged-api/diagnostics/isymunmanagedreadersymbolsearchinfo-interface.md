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
ms.openlocfilehash: 4a6eb99de44c2d3f1afe6dda2d6ec895ec57c617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635000"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="70b77-102">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70b77-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="70b77-103">Poskytuje metody, které získávají informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="70b77-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="70b77-104">Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70b77-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70b77-105">Metody</span><span class="sxs-lookup"><span data-stu-id="70b77-105">Methods</span></span>  
  
|<span data-ttu-id="70b77-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="70b77-106">Method</span></span>|<span data-ttu-id="70b77-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70b77-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70b77-108">GetSymbolSearchInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="70b77-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="70b77-109">Získá informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="70b77-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="70b77-110">GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="70b77-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="70b77-111">Získá počet informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="70b77-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70b77-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70b77-112">Requirements</span></span>  
 <span data-ttu-id="70b77-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="70b77-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b77-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70b77-114">See also</span></span>
- [<span data-ttu-id="70b77-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="70b77-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
