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
ms.openlocfilehash: 2a872774b1c4510c8d0325c59ae7678c867c1aff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986229"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="72b90-102">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72b90-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="72b90-103">Poskytuje metody, které získávají informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="72b90-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="72b90-104">Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72b90-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72b90-105">Metody</span><span class="sxs-lookup"><span data-stu-id="72b90-105">Methods</span></span>  
  
|<span data-ttu-id="72b90-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="72b90-106">Method</span></span>|<span data-ttu-id="72b90-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72b90-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72b90-108">GetSymbolSearchInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="72b90-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="72b90-109">Získá informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="72b90-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="72b90-110">GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="72b90-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="72b90-111">Získá počet informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="72b90-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72b90-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72b90-112">Requirements</span></span>  
 <span data-ttu-id="72b90-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="72b90-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b90-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72b90-114">See also</span></span>

- [<span data-ttu-id="72b90-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="72b90-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
