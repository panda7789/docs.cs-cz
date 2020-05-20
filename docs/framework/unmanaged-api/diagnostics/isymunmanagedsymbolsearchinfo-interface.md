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
ms.openlocfilehash: 308c501e17446719067d2dc0580d698c1770bf53
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610662"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="98cec-102">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98cec-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="98cec-103">Poskytuje metody, které získávají informace o cestě pro hledání.</span><span class="sxs-lookup"><span data-stu-id="98cec-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="98cec-104">Získejte toto rozhraní voláním `QueryInterface` objektu, který implementuje rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="98cec-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98cec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="98cec-105">Methods</span></span>  
  
|<span data-ttu-id="98cec-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="98cec-106">Method</span></span>|<span data-ttu-id="98cec-107">Popis</span><span class="sxs-lookup"><span data-stu-id="98cec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98cec-108">GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="98cec-108">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="98cec-109">Získá HRESULT.</span><span class="sxs-lookup"><span data-stu-id="98cec-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="98cec-110">GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="98cec-110">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="98cec-111">Získá cestu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="98cec-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="98cec-112">GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="98cec-112">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="98cec-113">Získá délku cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="98cec-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98cec-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98cec-114">Requirements</span></span>  
 <span data-ttu-id="98cec-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="98cec-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="98cec-116">See also</span></span>

- [<span data-ttu-id="98cec-117">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="98cec-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
